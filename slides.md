---
theme: default
title: AIにHowを教える必要がなくなったかもしれない
info: |
  SuperpowersとMatt Pocock Skillsの設計思想を比較します。
colorSchema: light
drawings:
  persist: false
transition: fade-out
comark: true
duration: 10min
layout: default
class: swiss-cover
---

<div class="cover-field">
  <h1 class="cover-title">
    AIに<span class="cover-em">How</span>を教える必要が<br>
    なくなったかもしれない
  </h1>

  <div class="cover-foot">
    Superpowers から Matt Pocock Skills へ
  </div>
</div>

<!--
GPT6が出て、一段と賢くなったと感じた。
Howを教える必要がなくなったかも。
-->

---
layout: default
class: swiss-light
---

<div class="page-head">
  <div class="page-kicker">SUPERPOWERS / WORKFLOW</div>
  <h1 class="page-title">Superpowersのワークフロー</h1>
</div>

<div class="timeline">
  <div class="stage">
    <div class="stage-number">01</div>
    <div class="stage-title">設計を詰める</div>
    <div class="stage-mark"></div>
    <div class="stage-skills"><code>brainstorming</code></div>
  </div>

  <div class="stage stage-emphasis">
    <div class="stage-number">02</div>
    <div class="stage-title">仕様を書く</div>
    <div class="stage-mark"></div>
    <div class="stage-skills"><code>writing-plans</code></div>
  </div>

  <div class="stage">
    <div class="stage-number">03</div>
    <div class="stage-title">実装する</div>
    <div class="stage-mark"></div>
    <div class="stage-skills"><code>subagent-driven-<br>development</code><code>test-driven-<br>development</code></div>
  </div>

  <div class="stage">
    <div class="stage-number">04</div>
    <div class="stage-title">検証する</div>
    <div class="stage-mark"></div>
    <div class="stage-skills"><code>requesting-code-review</code></div>
  </div>

  <div class="stage">
    <div class="stage-number">05</div>
    <div class="stage-title">完了する</div>
    <div class="stage-mark"></div>
    <div class="stage-skills"><code>finishing-a-development-<br>branch</code></div>
  </div>
</div>

<!--
個人開発で過去にSupwerpowersを使った。
Supwerpowersは仕様駆動開発の思想で、設計＞仕様＞実装＞検証＞完了という順で進める。

Superpowersの特徴として、「writing-plans」で仕様書以外にタスクファイルも生成される。
そのタスクファイルは非常に細かく、何を実装するか、どう実装するか、場合によって実装例のコードまで書かれている。
-->

---
layout: default
class: swiss-dark
---

<div class="page-head">
  <div class="page-kicker kicker-on-dark">SUPERPOWERS / PHILOSOPHY</div>
  <h1 class="page-title title-on-dark">「事細かく」書く</h1>
</div>

<div class="philosophy-grid">
  <div class="model-route">
    <div class="route-row">
      <span class="route-meta">DESIGN</span>
      <strong>最も高性能なモデル</strong>
      <span>仕様と設計を固める</span>
    </div><div class="route-row route-accent">
      <span class="route-meta">PLAN</span>
      <strong>詳細な実装計画</strong>
      <span>ファイル・コード・テスト手順</span>
    </div><div class="route-row">
      <span class="route-meta">EXECUTE</span>
      <strong>高速で安価なモデル</strong>
      <span>明確な仕様を機械的に実装する</span>
    </div>
  </div>

  <div class="skill-spec">
    <div class="skill-spec-head">
      <span>writing-skills / SKILL.md</span>
      <span class="skill-lines">679 LINES</span>
    </div>
    <iframe class="skill-scroll" src="/sources/superpowers-writing-skills.html" title="Superpowers writing-skills全文"></iframe>
    <div class="skill-source">
      <a href="https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/skills/writing-skills/SKILL.md">obra/superpowers · b36e082</a>
    </div>
  </div>
</div>

<!--
なぜSuperpowersはそこまで事細かく書くか。

賢いモデルで仕様と設計を固めて、やすいモデルでも実装するという思想だから。

やすいモデルの賢さを期待していないから、誰でも分かる手順書を作ることになる。

writing-skillsというスキルを作成するためのスキルがある。
スキルの作り方というより「完璧な手順書の作り方」の説明。
-->

---
layout: default
class: swiss-light matt-workflow-page
---

<div class="page-head">
  <div class="page-kicker">MATT POCOCK / WORKFLOW</div>
  <h1 class="page-title">Matt Pocock Skillsのワークフロー</h1>
</div>

<div class="matt-flow">
  <div class="matt-step matt-step-start">
    <div class="matt-number">01</div>
    <div class="matt-command">/grill-me</div>
    <div class="matt-or">or</div>
    <div class="matt-command">/grill-with-docs</div>
  </div>
  <div class="matt-arrow">→</div>
  <div class="matt-step matt-step-optional">
    <div class="matt-number">02</div>
    <div class="matt-command">/to-spec</div>
  </div>
  <div class="matt-arrow">›</div>
  <div class="matt-step matt-step-optional">
    <div class="matt-number">03</div>
    <div class="matt-command">/to-tickets</div>
  </div>
  <div class="matt-arrow">›</div>
  <div class="matt-step">
    <div class="matt-number">04</div>
    <div class="matt-command">/implement</div>
  </div>
  <div class="matt-arrow">›</div>
  <div class="matt-step matt-step-end">
    <div class="matt-number">05</div>
    <div class="matt-command">/code-review</div>
  </div>
</div>

<div class="matt-footnote">Matt Pocock Skillsには、このほかにも多数のSkillがあります。</div>

<!--
最近Supwerpowersの変わりにMatt Pocock Skillsを使っている。

一見Supwerpowersに近い構成だが、
実はto-specとto-ticketsは必須ではない。

 to-specとto-ticketsはあくまで「この会話のコンテキストウィンドウに収まらなさそうな場合、外部に記録を残す」ためのスキル。

チケットに「何を作るか」と「受け入れ基準」しか書かれていない。

「How」を教える必要がなくなり、逆に「AIが必要に応じてHowを提示して選んでもらう」というのが特徴です。
-->

---
layout: default
class: pruning-split
---

<div class="pruning-left">
  <h1 class="pruning-title">
    <span>WRITING</span>
    <span>FOR</span>
    <span>AGENTS</span>
  </h1>

  <div class="pruning-case">
    <div class="pruning-case-label">CASE STUDY</div>
    <strong>grilling</strong>
    <div class="pruning-case-meta">
      <span>28 LINES</span>
      <span>短くても効く</span>
    </div>
  </div>
</div>

<div class="pruning-right">
  <div class="pruning-principle">PRUNING PRINCIPLE</div>
  <div class="pruning-question">
    この文を<br>
    削除すると、<br>
    Agentの挙動は<br>
    <span class="pruning-em">変わるか？</span>
  </div>
  <div class="pruning-answer">変わらないなら、削除する。</div>
</div>

<!--
MattPocockは、「今のAIはすでにシニアエンジニア並み、あるいはそれ以上」と評価しているので、「10年以上のシニアエンジニアにマイクロマネジメントをするのは逆効果」と思っているので、

なので、Writing for Agentsというスキルは「この文を削除.....削除する」という基準で作成された。

実際、grillingは28行しかない。
-->

---
layout: default
class: swiss-light roles-page
---

<div class="page-head">
  <div class="page-kicker">HUMAN × AI / RESPONSIBILITY</div>
  <h1 class="page-title">今後人間とAIの役割はどうなるか？</h1>
</div>

<div class="roles-grid">
  <section class="role-column role-human">
    <div class="role-meta">HUMAN / WHAT</div>
    <h2>インターフェイスを<br>決める</h2>
    <ul>
      <li><span>01</span>仕様と制約</li>
      <li><span>02</span>トレードオフ</li>
      <li><span>03</span>受け入れ条件・テスト境界</li>
    </ul>
  </section>

  <div class="role-divider">
    <span>CONTRACT</span>
  </div>

  <section class="role-column role-ai">
    <div class="role-meta">AI / HOW</div>
    <h2>インターフェイスを<br>実装する</h2>
    <ul>
      <li><span>01</span>コードとテストを書く</li>
      <li><span>02</span>型検査・テストを通す</li>
      <li><span>03</span>レビュー指摘を修正する</li>
    </ul>
  </section>
</div>

<div class="roles-statement">制約を守っていれば、実装(How)は問わない</div>

<!--
今後どうなるか、人間は何をすべきか？

簡単にいうと人間はクライアントになり、AIがSESエンジニアになると思います。

人間は、仕様、制約、トレードオフなどのインターフェイスを決めます。

AIは、そのインターフェイスを実装します。コードとテストを書き、型検査とテストを通し、レビューの指摘を修正します。

つまり、制約を守っていれば、実装は問いません。
人間はHowを事細かく指定するのではなく、設計と判断に集中する。
-->

---
layout: default
class: swiss-light references-page
---

<div class="page-head">
  <div class="page-kicker">SOURCES / FURTHER READING</div>
  <h1 class="page-title">参考資料</h1>
</div>

<div class="reference-list">
  <a class="reference-item" href="https://www.aihero.dev/how-to-make-codebases-ai-agents-love" target="_blank">
    <div class="reference-number">01</div>
    <div class="reference-title">How to Make Codebases AI Agents Love</div>
    <div class="reference-url">aihero.dev/how-to-make-codebases-ai-agents-love</div>
  </a>
  <a class="reference-item" href="https://github.com/obra/superpowers" target="_blank">
    <div class="reference-number">02</div>
    <div class="reference-title">obra / superpowers</div>
    <div class="reference-url">github.com/obra/superpowers</div>
  </a>
  <a class="reference-item" href="https://github.com/mattpocock/skills" target="_blank">
    <div class="reference-number">03</div>
    <div class="reference-title">mattpocock / skills</div>
    <div class="reference-url">github.com/mattpocock/skills</div>
  </a>
</div>

<!--
最後に、今回参考にした資料です。興味があれば、あとでご覧ください。
-->
