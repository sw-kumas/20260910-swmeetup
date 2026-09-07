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

<div class="page-number">01 / 10</div>

<!--
皆さんお疲れ様です。先週GPT6が公開されましたので、いろんな検証動画やブログをみて、「また一段と賢くなったな」と感じましたが、「じゃ結局人間がやらなければいけない仕事は残りなにがあるのか」とも思いましたので、今回は「AIがシニアエンジニアになったとき、人とAIの役割がどうなるか」というテーマについてお話をさせていただきます。
-->

---
class: observation
---

<div class="eyebrow">公開されている検証動画を見た感想</div>

# GPT6は賢くなった。

<div class="image-grid">
  <figure><div class="image-placeholder" role="img" aria-label="検証動画の画像1を後から差し替える枠"><span>01</span><small>画像を差し替え</small></div><figcaption>検証例 1</figcaption></figure>
  <figure><div class="image-placeholder" role="img" aria-label="検証動画の画像2を後から差し替える枠"><span>02</span><small>画像を差し替え</small></div><figcaption>検証例 2</figcaption></figure>
  <figure><div class="image-placeholder" role="img" aria-label="検証動画の画像3を後から差し替える枠"><span>03</span><small>画像を差し替え</small></div><figcaption>検証例 3</figcaption></figure>
</div>

<p class="bottom-thought">手順を細かく決めるほど、賢くなった差を感じにくい気がする。</p>
<div class="page-number">02 / 10</div>

<!--
先ほども話しましたが、私はまだGPT6をそこまで使い込んでいませんので、ここから話すことは、いろんな方の検証動画やブログを見たうえでの感想になります。

画像を作ったり3Dのものを動かしたり、これまで難しかったことがかなりできるようになっていて、モデル自体はやっぱり賢くなっていると思います。ただ、細かな手順をたくさん与えた環境で動かしているのを見ると、以前のモデルとそこまで変わらないように見えることもありました。

もちろん同じ条件で比べたわけではありませんので、手順が原因だとは言い切れませんが、モデルが変わったのに、こちらの使い方は今までのままでいいのかな、という疑問を持ちました。
-->

---
class: skill-slide
---

<div class="eyebrow">以前、私も使っていたSuperpowers</div>

# かなり細かいところまで、<br>やり方が決まっている。

<div class="skill-panel">
  <div class="file-label">executing-plans / SKILL.md <span>原文抜粋・2段組</span></div>
  <div class="detailed-instructions">
    <pre class="skill-code">### Step 1: Load and Review Plan&#10;1. Ensure an isolated workspace: use superpowers:using-git-worktrees to create one or verify the existing one&#10;2. Read plan file&#10;3. Review critically - identify any questions or concerns about the plan&#10;4. If concerns: Raise them with your human partner before starting&#10;5. If no concerns: Create todos for the plan items and proceed&#10;&#10;### Step 2: Execute Tasks&#10;&#10;For each task:&#10;1. Mark as in_progress&#10;<mark>2. Follow each step exactly (plan has bite-sized steps)</mark>&#10;3. Run verifications as specified&#10;4. Mark as completed</pre>
    <pre class="skill-code">### Step 3: Complete Development&#10;&#10;After all tasks complete and verified:&#10;- Announce: "I'm using the finishing-a-development-branch skill to complete this work."&#10;- **REQUIRED SUB-SKILL:** Use superpowers:finishing-a-development-branch&#10;- Follow that skill to verify tests, present options, execute choice&#10;&#10;## When to Stop and Ask for Help&#10;&#10;**STOP executing immediately when:**&#10;- Hit a blocker (missing dependency, test fails, instruction unclear)&#10;- Plan has critical gaps preventing starting&#10;- You don't understand an instruction&#10;- Verification fails repeatedly&#10;&#10;**Ask for clarification rather than guessing.**</pre>
  </div>
</div>

<p class="bottom-thought">計画どおりに進めて、途中の確認方法や止める条件まで決めておく。</p>
<a class="source-link" href="https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/skills/executing-plans/SKILL.md#L18-L48">出典：obra/superpowers · executing-plans</a>
<div class="page-number">03 / 10</div>

<!--
これは、私も以前使っていたSuperpowersのskillです。計画を作って、その計画に沿って進めて、途中で問題があれば止めるという形になっていますので、抜け漏れを減らすうえではかなり助かりました。

実際の文章を見ると、まず作業用の場所を用意して、計画を読んで、問題がないか確認してから始める。実装に入ったら、それぞれの手順をそのまま実行する。最後に別のskillを呼び出して完了まで進める、というところまで決まっています。

当時のモデルに仕事を任せるなら、ここまで細かく手順を書いておくのは普通だったと思いますし、私自身もそれで助けられました。
-->

---
class: why-superpowers
---

<div class="eyebrow">Superpowersのskillの作り方</div>

# なぜ、ここまで長くて細かいのか？

<div class="why-grid">
  <div class="skill-shape">
    <span class="role-tag human">SKILL.mdに書く項目</span>
    <div class="shape-list">
      <span>いつ使うか</span>
      <span>基本の考え方</span>
      <span>すぐ確認できる一覧</span>
      <span>具体的な進め方</span>
      <span>よくある間違い</span>
      <span>実際に使った結果</span>
    </div>
  </div>
  <div class="skill-tdd">
    <span class="role-tag ai">skillを書く流れ</span>
    <div class="tdd-list">
      <span><b>1</b> skillなしで試す</span>
      <span><b>2</b> どこで失敗したかを見る</span>
      <span><b>3</b> 失敗を防ぐ指示を書く</span>
      <span><b>4</b> 抜け道があれば、また足す</span>
    </div>
  </div>
</div>

<p class="bottom-thought">守らせたいことが多いほど、skillも長くなる。</p>
<a class="source-link" href="https://github.com/obra/superpowers/blob/main/skills/writing-skills/SKILL.md">出典：obra/superpowers · writing-skills</a>
<div class="page-number">04 / 10</div>

<!--
では、なぜSuperpowersのskillはここまで長くて細かいのか。実は、skillの書き方を決めるwriting-skillsというskillがあって、その中に基本の構造がかなり細かく書かれています。

左側にあるように、いつ使うか、基本の考え方、すぐ確認できる一覧、具体的な進め方、よくある間違い、実際に使った結果、という項目を入れる形になっています。

さらに、skillを作るときもTDDと同じように、まずskillがない状態でAIに作業させて、どこで失敗するかを確認します。その失敗を防ぐ指示を書いて、もう一度試す。そこでAIが別の抜け道を見つけたら、その抜け道を防ぐ指示も追加します。

AIに決めた手順をきちんと守らせるための作り方になっていますので、守らせたいことが多いskillほど、文章も長くなります。
-->

---
class: analogy
---

<div class="eyebrow">人に置き換えて考えてみる</div>

# 経験10年の人にも、<br>ここまで細かく指示するだろうか？

<div class="analogy-grid">
  <div class="instruction-slip"><span class="file-label">たとえば、こんな指示</span><p>まず、このファイルを開く。<br>次に、この関数を書き換える。<br>必ず、この順番で進める。</p></div>
  <div class="senior-boundary"><span class="boundary-label">仕事を任せる相手</span><div class="senior-interior">経験10年の<br>エンジニア</div></div>
</div>

<div class="page-number">05 / 10</div>

<!--
ここで、LLMを人に置き換えて考えてみます。たとえば入社したばかりの人であれば、最初はファイルの場所から作業の順番まで、一つずつ説明することがあると思います。

では、相手が経験10年のエンジニアだった場合も、まずこのファイルを開いて、次にこの関数を書き換えて、必ずこの順番で進めてください、と毎回説明するでしょうか。たぶん、そこまで言わなくても目的を伝えれば、自分で調べて進めてくれると思います。

今のLLMも、自分で判断できる範囲が広がっているのであれば、こちらが説明する細かさも変えていいんじゃないか、と私は考えています。
-->

---
class: skill-slide matt-slide
---

<div class="eyebrow">私が今使っているMatt Pocockのskills</div>

# 必要なことだけ決めて、<br>実装はAIに任せる。

<div class="skill-panel">
  <div class="file-label">implement / SKILL.md <span>本文・空行省略</span></div>
  <pre class="skill-code">Implement the work described by the user in the spec or tickets.&#10;Use /tdd where possible, at pre-agreed seams.&#10;Run typechecking regularly, single test files regularly, and the full test suite once at the end.&#10;Once done, use /code-review to review the work.&#10;Commit your work to the current branch.</pre>
</div>

<p class="bottom-thought">仕様とテストを書く場所は先に決めて、実装と確認はAIに任せる。</p>
<p class="supporting">TDDとコードレビューは、それぞれ別のskillに分かれている。</p>
<a class="source-link" href="https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/implement/SKILL.md#L7-L15">出典：mattpocock/skills · implement</a>
<div class="page-number">06 / 10</div>

<!--
ここからは、今の自分の考え方にかなり近い、Matt Pocockのskillsを紹介します。これから話す内容は、基本的にMattの考え方を参考にしています。

こちらも先ほどと同じく、決まっている内容を実装するためのskillですが、書いてあるのはこの5つだけです。仕様やチケットに書かれた内容を実装する。事前に決めた場所でTDDを使う。型とテストを確認して、最後にコードレビューをしてコミットする。

どのファイルから触るのか、どの順番で変更するのかまでは書かれていません。TDDとコードレビューの詳しい進め方も、それぞれ別のskillに分かれていますので、実装の途中で必要になったときだけ読みます。

私は今、Superpowersを使わなくなっていて、先に必要なことだけ決めたら、あとの実装はAIに任せるというやり方をしています。
-->

---
class: roles-slide
---

<div class="eyebrow">調べればわかることはAIが調べる</div>

# AIに聞かれたことを、<br>全部そのまま決めない。

<div class="roles-grid">
  <div class="role-examples">
    <div><span class="role-tag human">人間が決める</span><p>検索で何を優先する？<br><small>速さか、結果の新しさか。</small></p></div>
    <div><span class="role-tag ai">AIが調べる</span><p>今の検索はどう動く？<br><small>コードとテストを調べる。</small></p></div>
  </div>
  <div class="ownership-boundary"><span class="boundary-label">人間：どう使うか、どう動いてほしいか</span><div class="ownership-interior"><span class="role-tag ai">AI：中の作り方</span><p>調べる → 提案する → 実装する → 確認する</p></div><span class="boundary-caption">ここまでを一緒に決めたら、中の作り方は任せる。</span></div>
</div>

<a class="source-link" href="https://www.aihero.dev/skills-grilling">出典：The /grilling Skill</a>
<div class="page-number">07 / 10</div>

<!--
Mattのskillsでは、調べればわかることと、人間が決めなければいけないことを分けています。

たとえば検索機能を改善するとき、今の検索がどう動いているのかは、コードやテストを見ればわかりますので、そこはAIに調べてもらいます。一方で、検索の速さと結果の新しさのどちらを優先するのかは、作りたいものによって変わりますので、そこは人間が決めます。もちろんAIには選択肢やおすすめも出してもらいますが、聞かれたことに全部「はい」と答えて、いつの間にかAIが決めたものを作っていた、という状態にはしません。

設計についても同じで、外からどう使うのか、どんな動きを期待するのかは一緒に決めます。そこまで決まったら、中をどう作るかはAIに任せます。
-->

---
class: checks-slide
---

<div class="eyebrow">任せるためにテストを使う</div>

# 手順は細かく決めない。<br>その代わり、完成の条件は決めておく。

<div class="verification-flow">
  <div class="flow-step human-step"><span class="role-tag human">人間とAIで決める</span><h2>完成の条件</h2><p>どう動けば完成なのか</p></div>
  <span class="flow-arrow" aria-hidden="true">→</span>
  <div class="flow-step ai-step"><span class="role-tag ai">AIに任せる</span><h2>実装する</h2><p>中をどう作るか</p></div>
  <span class="flow-arrow" aria-hidden="true">→</span>
  <div class="flow-step test-step"><span class="role-tag test">テストで確認する</span><h2>テスト・型・レビュー</h2><p>決めたとおりに動くか</p></div>
</div>

<p class="supporting">問題が見つかったらAIが直し、方針から変える場合は人間に戻す。</p>
<a class="source-link" href="https://www.aihero.dev/5-agent-skills-i-use-every-day">参考：5 Agent Skills I Use Every Day</a>
<div class="page-number">08 / 10</div>

<!--
ここまで聞くと、AIに好きなように書かせるだけなのか、と思うかもしれませんが、そういうことではありません。Matt自身も、進め方をはっきり決めることは重要だと言っています。

私が減らしたいのは、どのファイルの何行目を変えるかといった、実装の細かな指示です。その代わり、どう動けば完成なのかは先に決めて、テストや型、コードレビューで確認します。問題が見つかったらAIに直してもらい、そもそもの方針を変える必要が出た場合は、そこで人間に戻します。

AIに任せる範囲が広がるほど、完成の条件を人間がきちんと考える必要があると思います。
-->

---
class: conclusion
---

<div class="eyebrow">最後にMatt Pocockの言葉を紹介します</div>

# 今の自分の結論

<div class="quote-lines">
  <div class="quote-line human" v-click="1"><p>人間が、外からどう使うかを決める。</p><small>You own the interface.</small></div>
  <div class="quote-line ai" v-click="2"><p>AIが、中を実装する。</p><small>AI owns the implementation.</small></div>
  <div class="quote-line test" v-click="3"><p>テストで、期待どおりに動くか確認する。</p><small>Tests keep it honest.</small></div>
</div>

<a class="source-link" href="https://www.aihero.dev/how-to-make-codebases-ai-agents-love">Matt Pocock · How To Make Codebases AI Agents Love（日本語は訳）</a>
<div class="page-number">09 / 10</div>

<!--
最後に、これはあくまで今の自分の中での結論ですが、Matt Pocockのこの言葉に、私の考えがほぼ全部入っています。

[click] 人間が、外からどう使うかを決める。
[click] AIが、中を実装する。
[click] そして、テストで期待どおりに動くかを確認する。

モデルがさらに賢くなっても、この三つのうち人間が持つところは、たぶん残り続けるんじゃないかと思います。
-->

---
class: references
---

<div class="eyebrow">今回紹介したもの</div>

# 参考資料

<div class="reference-list">
  <a href="https://www.aihero.dev/how-to-make-codebases-ai-agents-love"><span>人間が設計し、AIが実装するという考え方</span><small>aihero.dev/how-to-make-codebases-ai-agents-love</small></a>
  <a href="https://www.aihero.dev/skills-grilling"><span>AIが調べることと、人間が決めること</span><small>aihero.dev/skills-grilling</small></a>
  <a href="https://www.aihero.dev/skills-grill-me"><span>何を作るかは人間が決める</span><small>aihero.dev/skills-grill-me</small></a>
  <a href="https://www.aihero.dev/5-agent-skills-i-use-every-day"><span>Matt Pocockが普段使っているskills</span><small>aihero.dev/5-agent-skills-i-use-every-day</small></a>
  <a href="https://github.com/obra/superpowers/blob/b36e0829c6d0140e93cfef2ca599b1b07d4a7797/skills/executing-plans/SKILL.md"><span>Superpowersのexecuting-plans</span><small>github.com/obra/superpowers · executing-plans</small></a>
  <a href="https://github.com/mattpocock/skills/blob/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/implement/SKILL.md"><span>Matt Pocockのimplement</span><small>github.com/mattpocock/skills · implement</small></a>
  <a href="https://github.com/obra/superpowers/blob/main/skills/writing-skills/SKILL.md"><span>Superpowersのwriting-skills</span><small>github.com/obra/superpowers · writing-skills</small></a>
</div>

<div class="page-number">10 / 10</div>

<!--
今回紹介した資料はこちらにまとめていますので、気になるものがあれば後で見てみてください。以上です。ありがとうございました。
-->
