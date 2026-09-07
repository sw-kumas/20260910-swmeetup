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
本日は、最近私がSuperpowersを使わなくなり、代わりにMatt Pocock Skillsを使うようになった理由をお話しします。
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

  <div class="stage">
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
まず、Superpowersの基本的なワークフローを紹介します。

最初にbrainstormingで、実装へ進む前に設計を詰めます。次にwriting-plansで、変更するファイル、コード、テスト方法まで含む仕様を書きます。

実装はSubagentに任せ、各タスクをTDDで進めます。実装後にコードレビューを行い、最後にブランチを完了します。

画面では流れを追いやすいように、関連するスキルを5段階にまとめています。
-->

---
layout: default
class: swiss-dark
---

<div class="page-head">
  <div class="page-kicker kicker-on-dark">SUPERPOWERS / PHILOSOPHY</div>
  <h1 class="page-title title-on-dark">Skillsを「事細かく」書く</h1>
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
Superpowersの思想は明快です。

設計には最も高性能なモデルを使います。そしてwriting-plansで、変更するファイル、コード、テスト手順まで詳細に決めます。計画が十分に具体的であれば、実装は高速で安価なモデルに任せられます。

この考え方は、Skillの書き方にも表れています。右側には、679行あるwriting-skillsの全文を載せています。圧力テスト、Agentがルールを破るときの言い訳、抜け道の塞ぎ方、再検証まで、非常に事細かく説明しています。

極端に言えば、「猿でも分かる手順書」のような粒度です。ただし、長いこと自体が目的ではありません。誰が実行しても同じ規律を再現できるように、Howを細かく定義しています。
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
  <div class="matt-step">
    <div class="matt-number">02</div>
    <div class="matt-command">/to-spec</div>
  </div>
  <div class="matt-arrow">›</div>
  <div class="matt-step">
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
一方、Matt Pocock Skillsにも、よく似た流れがあります。

最初にgrill-me、またはgrill-with-docsで、実装前に認識を合わせます。次にto-specで仕様をまとめ、to-ticketsで作業を分割します。その後、implementで実装し、最後にcode-reviewを行います。

これは唯一の必須フローではありません。ただ、Superpowersと比較するうえでは、この組み合わせが最も分かりやすいと思います。
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
Matt Pocockのwriting-for-agentsには、非常に分かりやすい判断基準があります。

この文を削除すると、Agentの挙動は変わるか。変わらないのであれば、その文は削除します。

短くすること自体が目的ではありません。重複した説明、環境を見れば分かる情報、Agentがもともと実行する指示を取り除き、挙動を変える言葉だけを残します。

例えば、今回スライド作成にも使っているgrillingは、わずか28行です。それでも、質問を前提関係ごとに整理し、私と認識が揃うまでAgentを止める、という強い効果があります。

writing-for-agentsをうまく使うと、このように短くても効果の強いSkillを作れます。
-->

---
layout: default
class: swiss-light roles-page
---

<div class="page-head">
  <div class="page-kicker">HUMAN × AI / RESPONSIBILITY</div>
  <h1 class="page-title">緩いのではなく、役割が違う</h1>
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

<div class="roles-statement">制約を守っていれば、実装は問わない</div>

<!--
Matt Pocock Skillsは、Superpowersよりルールが緩い、ということではありません。人間とAIの役割が違います。

人間は、仕様、制約、インターフェイス、トレードオフを決めます。テストについても、何を満たせば完成なのかという受け入れ条件と境界を決めます。

AIは、そのインターフェイスを実装します。コードとテストを書き、型検査とテストを通し、レビューの指摘を修正します。

つまり、制約を守っていれば、実装は問いません。人間はHowを事細かく指定するのではなく、設計と判断に集中できます。
-->

---
layout: default
class: swiss-dark trust-page
---

<div class="page-head">
  <div class="page-kicker kicker-on-dark">MY EXPERIENCE / GPT-5.6以降</div>
  <h1 class="page-title title-on-dark">実装は、もう見なくてもいい？</h1>
</div>

<div class="trust-grid">
  <section class="trust-item">
    <div class="trust-number">01</div>
    <h2>すぐ直せる</h2>
    <p>問題があっても、<br>ほとんどすぐに修正できる</p>
  </section>

  <section class="trust-item trust-item-accent">
    <div class="trust-number">02</div>
    <h2>ルールに残せる</h2>
    <p>殆どの場合、<br>AGENTS.mdに書けば<br>再発しなくなる</p>
  </section>

  <section class="trust-item">
    <div class="trust-number">03</div>
    <h2>大胆に直せる</h2>
    <p>大きなリファクタリングにも<br>抵抗を感じにくくなった</p>
  </section>
</div>

<div class="trust-loop">
  <span>GENERATE</span><i>→</i><span>FIX</span><i>→</i><span>CODIFY</span><i>→</i><span>REPEAT</span>
</div>

<!--
ここからは、GPT-5.6以降の私個人の実感です。

最近は、AIが書いた実装を細かく確認しなくてもよいのではないか、と感じるようになりました。

もちろん、問題がまったく起きないわけではありません。ただ、何か問題があっても、ほとんどの場合はすぐに修正できます。同じ失敗を繰り返すなら、AGENTS.mdにルールとして書くことで、再発しなくなります。

自分で大量のコードを書き直す必要もないため、大きなリファクタリングへの抵抗感も薄くなりました。

実装、修正、ルール化というループが速くなったことで、実装そのものを監督する時間が減っています。
-->

---
layout: default
class: closing-page
---

<section class="closing-claim">
  <div class="closing-meta">CONCLUSION</div>
  <h1>
    コードを<br>
    書かなくても、<br>
    <em>学ぶ必要</em>は<br>
    なくならない
  </h1>
</section>

<section class="closing-reason">
  <div class="closing-path">
    <div class="closing-step">
      <span>01</span>
      <div>
        <h2>原理を理解する</h2>
        <p>なぜ動くのかを知る</p>
      </div>
    </div>
    <div class="closing-step">
      <span>02</span>
      <div>
        <h2>設計できる</h2>
        <p>境界と制約を決める</p>
      </div>
    </div>
    <div class="closing-step">
      <span>03</span>
      <div>
        <h2>判断できる</h2>
        <p>トレードオフを選ぶ</p>
      </div>
    </div>
  </div>

  <div class="closing-line">
    <span>仕事の中心が、</span>
    <strong>書くことから、決めることへ。</strong>
  </div>
</section>

<!--
ただし、コードを書かなくなることと、コードを学ばなくてよいことは、まったく別です。

原理が分からなければ、適切な設計はできません。設計ができなければ、どこに境界を置くか、どの制約を優先するかというトレードオフも判断できません。

AIが実装を担うようになっても、技術を理解する必要はなくなりません。むしろ人間には、何を作るのか、何を守るのか、どの選択肢を採るのかを決める力が求められます。

エンジニアの仕事の中心は、コードを書くことから、決めることへ移りつつあると思います。
-->
