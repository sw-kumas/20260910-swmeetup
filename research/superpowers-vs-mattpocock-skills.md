# Superpowers と mattpocock/skills の比較調査

調査日: 2026-09-07  
対象: `obra/superpowers` (`b36e0829c6d0140e93cfef2ca599b1b07d4a7797`)、`mattpocock/skills` (`3cca18b368ae95cdbdebbff572ccafa662551015`)、AI Hero の一次資料

## 発表で使える結論

比較の軸は「厳格か、緩いか」よりも、**How をどこまで事前に固定するか**です。

- Superpowers は、設計を承認した後、ファイル、コード、検証手順まで含む詳細な実装計画を作り、タスクごとに実装・レビューを回すワークフローです。
- mattpocock/skills は、小さく組み合わせ可能な Skill 群です。仕様ではモジュール、インターフェイス、テスト境界などの判断を残す一方、具体的なファイルパスやコードは原則として書きません。
- したがって Matt 側は単に「緩い」のではありません。**人間が重要な判断点を承認し、Agent には仕様、テスト、リポジトリ標準という境界の内側で実装させる**構成だと説明できます。ただし「テストさえ通れば実装方法は問わない」は強すぎます。設計、TDD、型検査、リポジトリ標準、コードレビューも明示的な制約です。

## 7つの主張の判定

### 1. Superpowers のフロー

**判定: 概ね正しいが、省略を明示した方がよいです。**

正式な基本フローは、`brainstorming` → `using-git-worktrees` → `writing-plans` → `subagent-driven-development` **または** `executing-plans` → `test-driven-development` → `requesting-code-review` → `finishing-a-development-branch` です（[README L261-L277](https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/README.md#L261-L277)）。

発表では次の短縮形が正確です。

> 設計を詰める → 詳細な実装計画を書く → Subagent またはバッチで実装する → TDD とレビューで検証する → ブランチを完了する

元の5段階は概要として使えますが、worktree、TDD、`subagent-driven-development` という推奨経路を省略しています。

### 2. 高性能モデルで仕様化し、安価な Subagent で実装する思想

**判定: 現在の一次資料が明確に支持しています。**

`writing-plans` は、コードベースの知識がほぼない実装者でも従えるように、変更ファイル、コード、テスト方法を含む包括的な計画を要求します（[writing-plans L8-L18](https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/skills/writing-plans/SKILL.md#L8-L18)、[L36-L50](https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/skills/writing-plans/SKILL.md#L36-L50)）。各コード工程にはコードブロックを要求し、曖昧な指示を禁止しています（[L82-L139](https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/skills/writing-plans/SKILL.md#L82-L139)）。

モデル選択も明示的です。設計には最も高性能なモデル、明確な仕様に基づく機械的実装には高速で安価なモデルを使い、計画に完成コードがあれば最安価層を使うとしています（[subagent-driven-development L184-L219](https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/skills/subagent-driven-development/SKILL.md#L184-L219)）。

### 3. Superpowers の Skill は長く、`writing-skills` は詳細な手順書に近い

**判定: 数量的には正しい。ただし「長さを推奨する思想」と言うのは不正確です。**

現在の全 `SKILL.md` を `wc -l` で数えると、Superpowers は14ファイル、合計3,377行、中央値188行、平均241行です。11/14ファイルが100行以上で、`writing-skills` は679行です。対して Matt 側は37ファイル、合計2,465行、中央値74行、平均67行で、100行以上は10/37ファイルです。補助 Markdown は含めていないため、これは「主 Skill ファイルの長さ」の比較です。

`writing-skills` は、Skill 作成を TDD に対応づけ、圧力テスト、失敗時の言い訳、抜け道の封鎖、再検証まで定義しています（[writing-skills L8-L20](https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/skills/writing-skills/SKILL.md#L8-L20)、[L374-L450](https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/skills/writing-skills/SKILL.md#L374-L450)、[L552-L587](https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/skills/writing-skills/SKILL.md#L552-L587)）。「猿でも分かる手順書」より、社内発表では「**例外や合理化まで先回りして塞ぐ、網羅的な運用手順書**」が適切です。

ただし同ファイル自身も token efficiency を重視し、頻繁にロードされる Skill の短さを推奨しています（[L213-L270](https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/skills/writing-skills/SKILL.md#L213-L270)）。長さそのものが目的なのではなく、規律を安定して再現するための手続きが多い、という理解が公平です。

### 4. Matt 側のフロー

**判定: 有効な組み合わせだが、単一の公式フローではありません。**

README は Skill を「小さく、変更しやすく、組み合わせ可能」と説明しています（[README L15-L19](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/README.md#L15-L19)）。`grill-me` / `grill-with-docs` は着手前の認識合わせとして推奨され（[L95-L103](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/README.md#L95-L103)）、`to-spec`、`to-tickets`、`implement` は別々の user-invoked Skill として並びます（[L184-L202](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/README.md#L184-L202)）。`implement` は最後に `code-review` を呼びます（[implement L7-L15](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/implement/SKILL.md#L7-L15)）。

したがって、次の表現が安全です。

> 代表的には、`/grill-me` または `/grill-with-docs` → `/to-spec` → 必要なら `/to-tickets` → `/implement` → `/code-review` と組み合わせられます。

`to-tickets` は spec だけでなく plan や会話からも開始できるため、常に必須ではありません（[to-tickets L1-L11](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/to-tickets/SKILL.md#L1-L11)）。

### 5. Matt の Skill は短く、具体的な How を最小化する

**判定: 概ね正しいです。**

行数差は上記の通りです。代表的なフローでは `grill-me` 7行、`grill-with-docs` 7行、`to-spec` 75行、`to-tickets` 105行、`implement` 15行、`code-review` 87行でした。

重要なのは単なる短さではありません。`to-spec` はモジュール、インターフェイス、アーキテクチャ、テスト境界を記録する一方、具体的なファイルパスやコードを原則禁止します（[to-spec L43-L65](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/to-spec/SKILL.md#L43-L65)）。`to-tickets` も、利用者価値を通す縦切りのチケットと受け入れ条件を要求し、実装ファイルやコード片は原則として書きません（[to-tickets L25-L40](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/to-tickets/SKILL.md#L25-L40)、[L69-L105](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/to-tickets/SKILL.md#L69-L105)）。

### 6. `writing-for-agents` は引き算で書く

**判定: 強く支持されています。**

同 Skill は、重複、古い情報、環境から容易に取得できる情報を削り、各文に対して「デフォルトと比べて Agent の振る舞いが変わるか」をテストし、変わらなければ文ごと削除すると述べています（[writing-for-agents L76-L81](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/productivity/writing-for-agents/SKILL.md#L76-L81)）。AI Hero の[一次解説](https://www.aihero.dev/skills-writing-for-agents)も、見た目の短さではなく、削除前後で挙動が変わるかを基準にすると説明しています。

ただし「最小実装」は「説明をすべて消す」ことではありません。必要な手順は本文に置き、分岐時だけ必要な参照は progressive disclosure で外へ出し、完了条件は明確かつ網羅的にする思想です（[writing-for-agents L29-L52](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/productivity/writing-for-agents/SKILL.md#L29-L52)）。

### 7. 「緩い」のではなく、役割を分けている

**判定: 妥当な要約。ただし一次資料の直引用ではなく、複数の設計をまとめた解釈です。**

根拠は次の通りです。

- `to-spec` はテストする seam を先に設計し、人間に確認します（[to-spec L13-L19](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/to-spec/SKILL.md#L13-L19)）。
- `to-tickets` は分割粒度と依存関係を人間が承認するまで反復します（[to-tickets L42-L56](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/to-tickets/SKILL.md#L42-L56)）。
- `implement` は実装方法を細かく規定せず、TDD、型検査、テスト、レビューを要求します（[implement L7-L15](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/implement/SKILL.md#L7-L15)）。
- `code-review` は仕様準拠とリポジトリ標準を別軸で検証します（[code-review L6-L12](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/code-review/SKILL.md#L6-L12)、[L80-L87](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/code-review/SKILL.md#L80-L87)）。
- 設計思想は「小さなインターフェイスの背後に多くの実装を隠し、そのインターフェイスをテスト面にする」です（[codebase-design L8-L28](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/codebase-design/SKILL.md#L8-L28)、[L60-L65](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/codebase-design/SKILL.md#L60-L65)）。

発表では次の表現が妥当です。

> 人間は、問題、インターフェイス、テスト境界、依存関係、トレードオフを決めます。Agent は、その合意とリポジトリ標準を満たす実装を選びます。How を放棄するのではなく、固定すべき How と任せる How を分けています。

## 終盤の主張: 出典と個人見解を分ける

### 「新しいモデルなら実装は確認しなくてもよい」

**話者本人の経験・意見として提示すべきです。** 今回確認したリポジトリの思想ではありません。むしろ Matt 側も、静的型、ブラウザ、テストというフィードバックループとコードレビューを重視しています（[README L142-L178](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/README.md#L142-L178)）。「逐行レビューの必要性を感じなくなった。ただし自動検証とレビュー工程は残す」と言えば、一次資料とも衝突しません。

### 「問題が出ても AGENTS.md に書けば再発しない」

**「再発率を下げられる」までに弱めるべきです。** `AGENTS.md` は Agent が読む常設の指示書ですが、長く無関係な指示は性能を落とします。Matt の思想では、規則を足す前に、挙動を変える文か、環境や既存資料から取得できない情報かを確認します（[writing-for-agents L20-L43](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/productivity/writing-for-agents/SKILL.md#L20-L43)、[AI Hero: A Complete Guide To AGENTS.md](https://www.aihero.dev/a-complete-guide-to-agents-md)）。

### 「コードを書かなくても、コードを学ぶ必要はなくならない」

**結論はリポジトリ思想と整合しますが、因果説明は話者の主張です。** Matt は「実装速度が上がるほど設計上のエントロピーも加速する」とし、型、テスト、深いモジュール、インターフェイス設計を重視しています（[README L142-L178](https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/README.md#L142-L178)）。「原理が分からなければ設計やトレードオフ判断ができない」は、その一次資料に支えられた話者自身の結論として述べるのが適切です。

## 資料上の注意

- [AI Hero `llms.txt`](https://www.aihero.dev/llms.txt) 自体は、サイトのルート、Markdown 版、API の場所を示す discovery 文書です。思想の本文ではありません。本ノートでは、そこから案内される AI Hero の一次ページを補助根拠にしました。
- 行数は上記2コミットの全 `SKILL.md` を対象にしたスナップショットです。今後の追加・分割で変わります。
- 「人間とAIの役割分担」は有力な総括ですが、Matt がその一文を標語として書いているわけではありません。発表では「私はこう解釈しています」と添えると正確です。
