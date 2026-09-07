---
theme: default
title: AIがシニアエンジニアになったとき
titleTemplate: '%s'
info: 人間とAIの役割を、Matt Pocockの考え方から見直す社内向けの10分トーク。
colorSchema: dark
aspectRatio: 16/9
canvasWidth: 1280
duration: 10min
timer: countdown
fonts:
  sans: 'Hiragino Kaku Gothic ProN'
  mono: 'SFMono-Regular'
  provider: none
htmlAttrs:
  lang: ja
monaco: false
drawings:
  enabled: false
defaults:
  layout: default
exportFilename: ai-senior-engineer
---

<div class="eyebrow">人とAIの役割を考える</div>

# AIが<br>シニアエンジニアに<br>なったとき

<div class="cover-boundary" aria-hidden="true">
  <span class="boundary-label">人間が決める</span>
  <div class="cover-interior"><span>AIに任せる</span></div>
</div>

<div class="page-number">01 / 09</div>

<!--
目安 0:35（累計 0:35）
今日は、AIが賢くなると、私たちの仕事はどう変わるのか、という話です。
コードをどれだけ速く書けるかより、何を自分で考えて、どこをAIに任せるか。
最近見たGPT-6の検証動画をきっかけに、今の自分の考えを整理しました。
「シニア」はLLMへの任せ方を考えるための比喩です。能力や経験年数を測った結果ではありません。
-->

---
class: observation
---

<div class="eyebrow">公開された検証動画を見て</div>

# 賢くなった。<br>任せ方は、そのままでいい？

<div class="image-grid">
  <figure><div class="image-placeholder" role="img" aria-label="検証動画の画像1を後から差し替える枠"><span>01</span><small>画像を差し替え</small></div><figcaption>検証例 1</figcaption></figure>
  <figure><div class="image-placeholder" role="img" aria-label="検証動画の画像2を後から差し替える枠"><span>02</span><small>画像を差し替え</small></div><figcaption>検証例 2</figcaption></figure>
  <figure><div class="image-placeholder" role="img" aria-label="検証動画の画像3を後から差し替える枠"><span>03</span><small>画像を差し替え</small></div><figcaption>検証例 3</figcaption></figure>
</div>

<p class="bottom-thought">細かな手順の中では、進化の差が小さく見えることがある。</p>
<div class="page-number">02 / 09</div>

<!--
目安 1:15（累計 1:50）
私はGPT-6を十分に使い込んでいるわけではありません。ここは、ネットにあるいろいろな人の検証動画を見た所感です。
画像や3Dなど、作っているものを見ると、かなり賢くなったように見える。
その一方で、細かな手順をたくさん与えた環境だと、前のモデルとの差があまり大きく見えないことがありました。
同じ条件で比較した実験ではないので、手順が原因だと断定はできません。
ただ、モデルが変わったのに、こちらの任せ方が変わっていないのでは、と思いました。
画像差し替え時：各動画の実際の内容に合わせて説明を調整し、出典URLを画像のキャプションと参考資料へ追加する。
-->

---
class: skill-slide
---

<div class="eyebrow">以前、私も使っていた Superpowers</div>

# 手順を、ここまで書いておく。

<div class="skill-panel">
  <div class="file-label">executing-plans / SKILL.md <span>原文抜粋・2段組</span></div>
  <div class="detailed-instructions">
    <pre class="skill-code">### Step 1: Load and Review Plan&#10;1. Ensure an isolated workspace: use superpowers:using-git-worktrees to create one or verify the existing one&#10;2. Read plan file&#10;3. Review critically - identify any questions or concerns about the plan&#10;4. If concerns: Raise them with your human partner before starting&#10;5. If no concerns: Create todos for the plan items and proceed&#10;&#10;### Step 2: Execute Tasks&#10;&#10;For each task:&#10;1. Mark as in_progress&#10;<mark>2. Follow each step exactly (plan has bite-sized steps)</mark>&#10;3. Run verifications as specified&#10;4. Mark as completed</pre>
    <pre class="skill-code">### Step 3: Complete Development&#10;&#10;After all tasks complete and verified:&#10;- Announce: "I'm using the finishing-a-development-branch skill to complete this work."&#10;- **REQUIRED SUB-SKILL:** Use superpowers:finishing-a-development-branch&#10;- Follow that skill to verify tests, present options, execute choice&#10;&#10;## When to Stop and Ask for Help&#10;&#10;**STOP executing immediately when:**&#10;- Hit a blocker (missing dependency, test fails, instruction unclear)&#10;- Plan has critical gaps preventing starting&#10;- You don't understand an instruction&#10;- Verification fails repeatedly&#10;&#10;**Ask for clarification rather than guessing.**</pre>
  </div>
</div>

<p class="bottom-thought"><span class="human">開始を記録</span> → 手順どおりに実行 → 指定の確認 → 完了を記録</p>
<a class="source-link" href="https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/skills/executing-plans/SKILL.md#L18-L48">出典：obra/superpowers · executing-plans</a>
<div class="page-number">03 / 09</div>

<!--
目安 1:20（累計 3:10）
以前の私もSuperpowersにお世話になりました。計画を作り、それに沿って進め、確認する。抜けを防ぐうえで役立ちました。
これは、決まった計画を実行するskillの実物です。全体の一部を抜き出しています。
注目してほしいのは「各手順をそのまま実行する」という部分です。作業開始や完了の記録まで書いてあります。
判断が不安定な相手に仕事を頼むなら、こういう手順書を用意するのは自然です。
良い悪いではなく、どこまで先に決めて渡すか、という任せ方の話です。
引用は固定commitの18–48行を2段に分けて表示。全文を読ませず、強調した「各手順をそのまま実行する」を指す。本文全体は64行ですが、別skillや計画への参照もあり、行数だけで比較しない。
-->

---
class: analogy
---

<div class="eyebrow">任せる相手が変わったら</div>

# 経験豊富な人にも、<br>そこまで指示しますか？

<div class="analogy-grid">
  <div class="instruction-slip"><span class="file-label">たとえば、こんな指示</span><p>まず、このファイルを開く。<br>次に、この関数を書き換える。<br>この順番で。必ず、このとおりに。</p></div>
  <div class="senior-boundary"><span class="boundary-label">任せる範囲</span><div class="senior-interior">経験豊富な<br>エンジニア</div></div>
</div>

<div class="page-number">04 / 09</div>

<!--
目安 1:05（累計 4:15）
入ったばかりの人なら、一つずつ説明することがあります。
でも、十分に経験のある人を迎えたときも、開くファイルから順番まで、毎回指定するでしょうか。
「まずこのファイルを開いて、次にこの関数を……」と読み上げて、一拍置く。笑いを取りにいきすぎない。
ここでの指示は説明用の例で、Superpowersからの引用ではありません。
LLMも、相手の判断に任せられる範囲が広がったなら、こちらの説明の細かさを見直せるのではないか。
これは私の見立てです。では、何を自分で決め、何を任せるのか。
-->

---
class: skill-slide matt-slide
---

<div class="eyebrow">私が賛同する Matt Pocock の考え方</div>

# 決めたことを渡す。実装を任せる。

<div class="skill-panel">
  <div class="file-label">implement / SKILL.md <span>本文・空行省略</span></div>
  <pre class="skill-code">Implement the work described by the user in the spec or tickets.&#10;Use /tdd where possible, at pre-agreed seams.&#10;Run typechecking regularly, single test files regularly, and the full test suite once at the end.&#10;Once done, use /code-review to review the work.&#10;Commit your work to the current branch.</pre>
</div>

<p class="bottom-thought"><span class="human">仕様・確認する境界を合意</span> → <span class="ai">実装・検証</span></p>
<p class="supporting">テストとレビューの進め方は、別のskillへ。</p>
<a class="source-link" href="https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/implement/SKILL.md#L7-L15">出典：mattpocock/skills · implement</a>
<div class="page-number">05 / 09</div>

<!--
目安 1:25（累計 5:40）
ここからは、私が強く賛同しているMatt Pocockの考え方を紹介しながら、人とAIの役割を考えていきます。
これは、同じく決まった内容を実装するためのskillです。本文はこの5つの指示です。
合意した仕様を実装する。事前に決めた境界でテストを書く。型やテストを確認する。レビューする。コミットする。
どのファイルから、どの順番で変更するかは、この本文には書かれていません。
ただ、短いから何もしなくてよいわけではありません。テストやレビューの詳しい進め方は、別のskillにあります。
私は今、Superpowersを使わなくなりました。こうして決めるところを決め、実装は任せる考え方が、自分に合っています。
本文の短さだけで、参照先を含む総指示量や性能の優劣を主張しない。
-->

---
class: roles-slide
---

<div class="eyebrow">決めることと、調べればわかること</div>

# AIの質問に、うなずくだけにしない。

<div class="roles-grid">
  <div class="role-examples">
    <div><span class="role-tag human">人間が決める</span><p>検索で、何を優先する？<br><small>速さか、結果の新しさか。</small></p></div>
    <div><span class="role-tag ai">AIが調べる</span><p>今の検索は、どう動く？<br><small>コードとテストを調べる。</small></p></div>
  </div>
  <div class="ownership-boundary"><span class="boundary-label">人間：外からどう使い、どう動くか</span><div class="ownership-interior"><span class="role-tag ai">AI：内部の実装</span><p>調査 → 提案 → 実装 → 検証</p></div><span class="boundary-caption">設計と方針を合意してから、内側を任せる。</span></div>
</div>

<a class="source-link" href="https://www.aihero.dev/skills-grilling">出典：The /grilling Skill</a>
<div class="page-number">06 / 09</div>

<!--
目安 1:30（累計 7:10）
たとえば検索を改善するとします。今のコードがどう動くかは、AIが調べればわかることです。
一方、速さと結果の新しさのどちらを優先するかは、利用者に何を届けたいかによって変わる。そこは自分で考える。
AIには選択肢や推奨案も出してもらいます。でも、「はい、はい」と答え続けて、いつの間にかAIが決めたものを作る状態にはしない。
設計も人間の仕事に残ります。何を受け取り、何を返し、どう振る舞うか。その約束を決めたうえで、中身の実装を任せる。
すべての実装上の選択を人間に戻す、という意味ではありません。合意した境界の中の細かな判断は任せます。
検索の例は発表用の説明例。Mattの直接の引用ではない。
補助出典：https://www.aihero.dev/skills-grill-me と https://www.aihero.dev/how-to-make-codebases-ai-agents-love
-->

---
class: checks-slide
---

<div class="eyebrow">任せるために、確かめ方を決める</div>

# 作り方の指図は減らす。<br>守る条件は、明確にする。

<div class="verification-flow">
  <div class="flow-step human-step"><span class="role-tag human">人間と合意</span><h2>期待する動き</h2><p>何ができればよいか</p></div>
  <span class="flow-arrow" aria-hidden="true">→</span>
  <div class="flow-step ai-step"><span class="role-tag ai">AIに任せる</span><h2>実装と修正</h2><p>中身をどう作るか</p></div>
  <span class="flow-arrow" aria-hidden="true">→</span>
  <div class="flow-step test-step"><span class="role-tag test">結果を確かめる</span><h2>テスト・型・レビュー</h2><p>約束どおりに動くか</p></div>
</div>

<p class="supporting">確認で問題が見つかれば修正する。方針を変えるなら、人間と相談する。</p>
<a class="source-link" href="https://www.aihero.dev/5-agent-skills-i-use-every-day">参考：5 Agent Skills I Use Every Day</a>
<div class="page-number">07 / 09</div>

<!--
目安 1:05（累計 8:15）
作り方の指図を減らす、というのは私の考えです。Matt自身は、明確で厳格な進め方が重要だと述べています。
この二つは両立します。どの行をどう変えるかまで指定しなくても、何を守るか、どう確かめるかは決められる。
期待する動きをテストにし、型やレビューで確かめる。問題があればAIが直す。
そもそもの仕様を変える必要があれば、そこで人間と相談する。
テストが通れば、現実のあらゆる正しさが証明されるわけではありません。何を確かめるかを決め、結果を吟味する仕事は残ります。
-->

---
class: conclusion
---

<div class="eyebrow">Matt Pocock の言葉で</div>

# 人間とAIの役割

<div class="quote-lines">
  <div class="quote-line human" v-click="1"><p>人間が、外から見える振る舞いを決める。</p><small>You own the interface.</small></div>
  <div class="quote-line ai" v-click="2"><p>AIが、中身を実装する。</p><small>AI owns the implementation.</small></div>
  <div class="quote-line test" v-click="3"><p>テストが、その正しさを確かめる。</p><small>Tests keep it honest.</small></div>
</div>

<a class="source-link" href="https://www.aihero.dev/how-to-make-codebases-ai-agents-love">Matt Pocock · How To Make Codebases AI Agents Love（日本語は訳）</a>
<div class="page-number">08 / 09</div>

<!--
目安 1:00（累計 9:15）
あくまで、今の私の中での結論です。
Matt Pocockのこの言葉に、私の考えはほぼすべて入っています。
[click] 人間が、外から見える振る舞いを決める。
[click] AIが、中身を実装する。
[click] テストが、その正しさを確かめる。
数秒、間を置く。ここで解説を重ねずに終える。
日本語は発表用の訳。interfaceは、モジュールの入出力や振る舞いの約束を指す。
-->

---
class: references
---

<div class="eyebrow">続きはこちらから</div>

# 参考資料

<div class="reference-list">
  <a href="https://www.aihero.dev/how-to-make-codebases-ai-agents-love"><span>設計と実装の役割分担・最後の引用</span><small>aihero.dev/how-to-make-codebases-ai-agents-love</small></a>
  <a href="https://www.aihero.dev/skills-grilling"><span>調べることと、決めること</span><small>aihero.dev/skills-grilling</small></a>
  <a href="https://www.aihero.dev/skills-grill-me"><span>人間が話の範囲を握る</span><small>aihero.dev/skills-grill-me</small></a>
  <a href="https://www.aihero.dev/5-agent-skills-i-use-every-day"><span>Matt Pocockが使うskillと進め方</span><small>aihero.dev/5-agent-skills-i-use-every-day</small></a>
  <a href="https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/skills/executing-plans/SKILL.md"><span>Superpowers：計画を実行するskill</span><small>github.com/obra/superpowers · executing-plans</small></a>
  <a href="https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/implement/SKILL.md"><span>Matt Pocock：実装するskill</span><small>github.com/mattpocock/skills · implement</small></a>
</div>

<div class="page-number">09 / 09</div>

<!--
目安 0:10（累計 9:25、残り35秒は間と切り替えの余裕）
参考資料はこちらです。ありがとうございました。
リンクはクリック可能。比較したskillは引用時点のcommitに固定。
画像3点の出典は差し替え時に追加する。リンク一覧を読み上げる必要はない。
-->
