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

---
layout: default
class: swiss-light repo-intro-page
---

<div class="page-head">
  <div class="page-kicker">SKILLS / TWO REPOSITORIES</div>
  <h1 class="page-title">登場人物</h1>
</div>

<div class="repo-intro-grid">
  <figure class="repo-intro-item">
    <img src="/obra-superpowers-stats.png" alt="obra/superpowersのGitHub統計">
    <figcaption>
      <h2>obra/superpowers</h2>
      <p>AIエージェントの開発手順をまとめたSkills</p>
    </figcaption>
  </figure>

  <figure class="repo-intro-item">
    <img src="/mattpocock-skills-stats.png" alt="mattpocock/skillsのGitHub統計">
    <figcaption>
      <h2>mattpocock/skills</h2>
      <p>Matt Pocockが普段使うSkills集</p>
    </figcaption>
  </figure>
</div>

<!--
まず、今回取り上げる2つのリポジトリを簡単に紹介します。

Superpowersは、AIエージェントを使った開発工程をSkillsとして体系化したものです。
Matt Pocock Skillsは、Matt Pocockが実際に使っているSkillsを公開したものです。
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
    <pre v-pre class="skill-scroll">---&#10;name: writing-skills&#10;description: Use when creating new skills, editing existing skills, or verifying skills work before deployment&#10;---&#10;&#10;# Writing Skills&#10;&#10;## Overview&#10;&#10;**Writing skills IS Test-Driven Development applied to process documentation.**&#10;&#10;**Personal skills live in your runtime's skills directory** (`~/.claude/skills/` on Claude Code) — see [codex-tools.md](../using-superpowers/references/codex-tools.md) or [gemini-tools.md](../using-superpowers/references/gemini-tools.md) for the path on those runtimes. Codex, Copilot CLI, and Gemini CLI all also recognize `~/.agents/skills/` as a cross-runtime alias.&#10;&#10;You write test cases (pressure scenarios with subagents), watch them fail (baseline behavior), write the skill (documentation), watch tests pass (agents comply), and refactor (close loopholes).&#10;&#10;**Core principle:** If you didn't watch an agent fail without the skill, you don't know if the skill teaches the right thing.&#10;&#10;**REQUIRED BACKGROUND:** You MUST understand superpowers:test-driven-development before using this skill. That skill defines the fundamental RED-GREEN-REFACTOR cycle. This skill adapts TDD to documentation.&#10;&#10;**Official guidance:** For Anthropic's official skill authoring best practices, see anthropic-best-practices.md. This document provides additional patterns and guidelines that complement the TDD-focused approach in this skill.&#10;&#10;## What is a Skill?&#10;&#10;A **skill** is a reference guide for proven techniques, patterns, or tools. Skills help future agents find and apply effective approaches.&#10;&#10;**Skills are:** Reusable techniques, patterns, tools, reference guides&#10;&#10;**Skills are NOT:** Narratives about how you solved a problem once&#10;&#10;## TDD Mapping for Skills&#10;&#10;| TDD Concept | Skill Creation |&#10;|-------------|----------------|&#10;| **Test case** | Pressure scenario with subagent |&#10;| **Production code** | Skill document (SKILL.md) |&#10;| **Test fails (RED)** | Agent violates rule without skill (baseline) |&#10;| **Test passes (GREEN)** | Agent complies with skill present |&#10;| **Refactor** | Close loopholes while maintaining compliance |&#10;| **Write test first** | Run baseline scenario BEFORE writing skill |&#10;| **Watch it fail** | Document exact rationalizations agent uses |&#10;| **Minimal code** | Write skill addressing those specific violations |&#10;| **Watch it pass** | Verify agent now complies |&#10;| **Refactor cycle** | Find new rationalizations → plug → re-verify |&#10;&#10;The entire skill creation process follows RED-GREEN-REFACTOR.&#10;&#10;## When to Create a Skill&#10;&#10;**Create when:**&#10;- Technique wasn't intuitively obvious to you&#10;- You'd reference this again across projects&#10;- Pattern applies broadly (not project-specific)&#10;- Others would benefit&#10;&#10;**Don't create for:**&#10;- One-off solutions&#10;- Standard practices well-documented elsewhere&#10;- Project-specific conventions (put in your instructions file)&#10;- Mechanical constraints (if it's enforceable with regex/validation, automate it—save documentation for judgment calls)&#10;&#10;## Skill Types&#10;&#10;### Technique&#10;Concrete method with steps to follow (condition-based-waiting, root-cause-tracing)&#10;&#10;### Pattern&#10;Way of thinking about problems (flatten-with-flags, test-invariants)&#10;&#10;### Reference&#10;API docs, syntax guides, tool documentation (office docs)&#10;&#10;## Directory Structure&#10;&#10;&#10;```&#10;skills/&#10;  skill-name/&#10;    SKILL.md              # Main reference (required)&#10;    supporting-file.*     # Only if needed&#10;```&#10;&#10;**Flat namespace** - all skills in one searchable namespace&#10;&#10;**Separate files for:**&#10;1. **Heavy reference** (100+ lines) - API docs, comprehensive syntax&#10;2. **Reusable tools** - Scripts, utilities, templates&#10;&#10;**Keep inline:**&#10;- Principles and concepts&#10;- Code patterns (&amp;lt; 50 lines)&#10;- Everything else&#10;&#10;## SKILL.md Structure&#10;&#10;**Frontmatter (YAML):**&#10;- Two required fields: `name` and `description` (see [agentskills.io/specification](https://agentskills.io/specification) for all supported fields)&#10;- Max 1024 characters total&#10;- `name`: Use letters, numbers, and hyphens only (no parentheses, special chars)&#10;- `description`: Third-person, describes ONLY when to use (NOT what it does)&#10;  - Start with "Use when..." to focus on triggering conditions&#10;  - Include specific symptoms, situations, and contexts&#10;  - **NEVER summarize the skill's process or workflow** (see SDO section for why)&#10;  - Keep under 500 characters if possible&#10;&#10;```markdown&#10;---&#10;name: Skill-Name-With-Hyphens&#10;description: Use when [specific triggering conditions and symptoms]&#10;---&#10;&#10;# Skill Name&#10;&#10;## Overview&#10;What is this? Core principle in 1-2 sentences.&#10;&#10;## When to Use&#10;[Small inline flowchart IF decision non-obvious]&#10;&#10;Bullet list with SYMPTOMS and use cases&#10;When NOT to use&#10;&#10;## Core Pattern (for techniques/patterns)&#10;Before/after code comparison&#10;&#10;## Quick Reference&#10;Table or bullets for scanning common operations&#10;&#10;## Implementation&#10;Inline code for simple patterns&#10;Link to file for heavy reference or reusable tools&#10;&#10;## Common Mistakes&#10;What goes wrong + fixes&#10;&#10;## Real-World Impact (optional)&#10;Concrete results&#10;```&#10;&#10;&#10;## Skill Discovery Optimization (SDO)&#10;&#10;**Critical for discovery:** Future agents need to FIND your skill&#10;&#10;### 1. Rich Description Field&#10;&#10;**Purpose:** Your agent reads the description to decide which skills to load for a given task. Make it answer: "Should I read this skill right now?"&#10;&#10;**Format:** Start with "Use when..." to focus on triggering conditions&#10;&#10;**CRITICAL: Description = When to Use, NOT What the Skill Does**&#10;&#10;The description should ONLY describe triggering conditions. Do NOT summarize the skill's process or workflow in the description.&#10;&#10;**Why this matters:** Testing revealed that when a description summarizes the skill's workflow, an agent may follow the description instead of reading the full skill content. A description saying "code review between tasks" caused an agent to do ONE review, even though the skill's flowchart clearly showed TWO reviews (spec compliance then code quality).&#10;&#10;When the description was changed to just "Use when executing implementation plans with independent tasks" (no workflow summary), the agent correctly read the flowchart and followed the two-stage review process.&#10;&#10;**The trap:** Descriptions that summarize workflow create a shortcut agents will take. The skill body becomes documentation agents skip.&#10;&#10;```yaml&#10;# ❌ BAD: Summarizes workflow - agents may follow this instead of reading skill&#10;description: Use when executing plans - dispatches subagent per task with code review between tasks&#10;&#10;# ❌ BAD: Too much process detail&#10;description: Use for TDD - write test first, watch it fail, write minimal code, refactor&#10;&#10;# ✅ GOOD: Just triggering conditions, no workflow summary&#10;description: Use when executing implementation plans with independent tasks in the current session&#10;&#10;# ✅ GOOD: Triggering conditions only&#10;description: Use when implementing any feature or bugfix, before writing implementation code&#10;```&#10;&#10;**Content:**&#10;- Use concrete triggers, symptoms, and situations that signal this skill applies&#10;- Describe the *problem* (race conditions, inconsistent behavior) not *language-specific symptoms* (setTimeout, sleep)&#10;- Keep triggers technology-agnostic unless the skill itself is technology-specific&#10;- If skill is technology-specific, make that explicit in the trigger&#10;- Write in third person (injected into system prompt)&#10;- **NEVER summarize the skill's process or workflow**&#10;&#10;```yaml&#10;# ❌ BAD: Too abstract, vague, doesn't include when to use&#10;description: For async testing&#10;&#10;# ❌ BAD: First person&#10;description: I can help you with async tests when they're flaky&#10;&#10;# ❌ BAD: Mentions technology but skill isn't specific to it&#10;description: Use when tests use setTimeout/sleep and are flaky&#10;&#10;# ✅ GOOD: Starts with "Use when", describes problem, no workflow&#10;description: Use when tests have race conditions, timing dependencies, or pass/fail inconsistently&#10;&#10;# ✅ GOOD: Technology-specific skill with explicit trigger&#10;description: Use when using React Router and handling authentication redirects&#10;```&#10;&#10;### 2. Keyword Coverage&#10;&#10;Use words an agent would search for:&#10;- Error messages: "Hook timed out", "ENOTEMPTY", "race condition"&#10;- Symptoms: "flaky", "hanging", "zombie", "pollution"&#10;- Synonyms: "timeout/hang/freeze", "cleanup/teardown/afterEach"&#10;- Tools: Actual commands, library names, file types&#10;&#10;### 3. Descriptive Naming&#10;&#10;**Use active voice, verb-first:**&#10;- ✅ `creating-skills` not `skill-creation`&#10;- ✅ `condition-based-waiting` not `async-test-helpers`&#10;&#10;### 4. Token Efficiency (Critical)&#10;&#10;**Problem:** getting-started and frequently-referenced skills load into EVERY conversation. Every token counts.&#10;&#10;**Target word counts:**&#10;- getting-started workflows: &amp;lt;150 words each&#10;- Frequently-loaded skills: &amp;lt;200 words total&#10;- Other skills: &amp;lt;500 words (still be concise)&#10;&#10;**Techniques:**&#10;&#10;**Move details to tool help:**&#10;```bash&#10;# ❌ BAD: Document all flags in SKILL.md&#10;search-conversations supports --text, --both, --after DATE, --before DATE, --limit N&#10;&#10;# ✅ GOOD: Reference --help&#10;search-conversations supports multiple modes and filters. Run --help for details.&#10;```&#10;&#10;**Use cross-references:**&#10;```markdown&#10;# ❌ BAD: Repeat workflow details&#10;When searching, dispatch subagent with template...&#10;[20 lines of repeated instructions]&#10;&#10;# ✅ GOOD: Reference other skill&#10;Always use subagents (50-100x context savings). REQUIRED: Use [other-skill-name] for workflow.&#10;```&#10;&#10;**Compress examples:**&#10;```markdown&#10;# ❌ BAD: Verbose example (42 words)&#10;your human partner: "How did we handle authentication errors in React Router before?"&#10;You: I'll search past conversations for React Router authentication patterns.&#10;[Dispatch subagent with search query: "React Router authentication error handling 401"]&#10;&#10;# ✅ GOOD: Minimal example (20 words)&#10;Partner: "How did we handle auth errors in React Router?"&#10;You: Searching...&#10;[Dispatch subagent → synthesis]&#10;```&#10;&#10;**Eliminate redundancy:**&#10;- Don't repeat what's in cross-referenced skills&#10;- Don't explain what's obvious from command&#10;- Don't include multiple examples of same pattern&#10;&#10;**Verification:**&#10;```bash&#10;wc -w skills/path/SKILL.md&#10;# getting-started workflows: aim for &amp;lt;150 each&#10;# Other frequently-loaded: aim for &amp;lt;200 total&#10;```&#10;&#10;**Name by what you DO or core insight:**&#10;- ✅ `condition-based-waiting` &amp;gt; `async-test-helpers`&#10;- ✅ `using-skills` not `skill-usage`&#10;- ✅ `flatten-with-flags` &amp;gt; `data-structure-refactoring`&#10;- ✅ `root-cause-tracing` &amp;gt; `debugging-techniques`&#10;&#10;**Gerunds (-ing) work well for processes:**&#10;- `creating-skills`, `testing-skills`, `debugging-with-logs`&#10;- Active, describes the action you're taking&#10;&#10;### 5. Cross-Referencing Other Skills&#10;&#10;**When writing documentation that references other skills:**&#10;&#10;Use skill name only, with explicit requirement markers:&#10;- ✅ Good: `**REQUIRED SUB-SKILL:** Use superpowers:test-driven-development`&#10;- ✅ Good: `**REQUIRED BACKGROUND:** You MUST understand superpowers:systematic-debugging`&#10;- ❌ Bad: `See skills/testing/test-driven-development` (unclear if required)&#10;- ❌ Bad: `@skills/testing/test-driven-development/SKILL.md` (force-loads, burns context)&#10;&#10;**Why no @ links:** `@` syntax force-loads files immediately, consuming 200k+ context before you need them.&#10;&#10;## Flowchart Usage&#10;&#10;```dot&#10;digraph when_flowchart {&#10;    "Need to show information?" [shape=diamond];&#10;    "Decision where I might go wrong?" [shape=diamond];&#10;    "Use markdown" [shape=box];&#10;    "Small inline flowchart" [shape=box];&#10;&#10;    "Need to show information?" -&amp;gt; "Decision where I might go wrong?" [label="yes"];&#10;    "Decision where I might go wrong?" -&amp;gt; "Small inline flowchart" [label="yes"];&#10;    "Decision where I might go wrong?" -&amp;gt; "Use markdown" [label="no"];&#10;}&#10;```&#10;&#10;**Use flowcharts ONLY for:**&#10;- Non-obvious decision points&#10;- Process loops where you might stop too early&#10;- "When to use A vs B" decisions&#10;&#10;**Never use flowcharts for:**&#10;- Reference material → Tables, lists&#10;- Code examples → Markdown blocks&#10;- Linear instructions → Numbered lists&#10;- Labels without semantic meaning (step1, helper2)&#10;&#10;See `graphviz-conventions.dot` in this directory for graphviz style rules.&#10;&#10;**Visualizing for your human partner:** Use `render-graphs.js` in this directory to render a skill's flowcharts to SVG:&#10;```bash&#10;./render-graphs.js ../some-skill           # Each diagram separately&#10;./render-graphs.js ../some-skill --combine # All diagrams in one SVG&#10;```&#10;&#10;## Code Examples&#10;&#10;**One excellent example beats many mediocre ones**&#10;&#10;Choose most relevant language:&#10;- Testing techniques → TypeScript/JavaScript&#10;- System debugging → Shell/Python&#10;- Data processing → Python&#10;&#10;**Good example:**&#10;- Complete and runnable&#10;- Well-commented explaining WHY&#10;- From real scenario&#10;- Shows pattern clearly&#10;- Ready to adapt (not generic template)&#10;&#10;**Don't:**&#10;- Implement in 5+ languages&#10;- Create fill-in-the-blank templates&#10;- Write contrived examples&#10;&#10;You're good at porting - one great example is enough.&#10;&#10;## File Organization&#10;&#10;### Self-Contained Skill&#10;```&#10;defense-in-depth/&#10;  SKILL.md    # Everything inline&#10;```&#10;When: All content fits, no heavy reference needed&#10;&#10;### Skill with Reusable Tool&#10;```&#10;condition-based-waiting/&#10;  SKILL.md    # Overview + patterns&#10;  example.ts  # Working helpers to adapt&#10;```&#10;When: Tool is reusable code, not just narrative&#10;&#10;### Skill with Heavy Reference&#10;```&#10;pptx/&#10;  SKILL.md       # Overview + workflows&#10;  pptxgenjs.md   # 600 lines API reference&#10;  ooxml.md       # 500 lines XML structure&#10;  scripts/       # Executable tools&#10;```&#10;When: Reference material too large for inline&#10;&#10;## The Iron Law (Same as TDD)&#10;&#10;```&#10;NO SKILL WITHOUT A FAILING TEST FIRST&#10;```&#10;&#10;This applies to NEW skills AND EDITS to existing skills.&#10;&#10;Write skill before testing? Delete it. Start over.&#10;Edit skill without testing? Same violation.&#10;&#10;**No exceptions:**&#10;- Not for "simple additions"&#10;- Not for "just adding a section"&#10;- Not for "documentation updates"&#10;- Don't keep untested changes as "reference"&#10;- Don't "adapt" while running tests&#10;- Delete means delete&#10;&#10;**REQUIRED BACKGROUND:** The superpowers:test-driven-development skill explains why this matters. Same principles apply to documentation.&#10;&#10;## Testing All Skill Types&#10;&#10;Different skill types need different test approaches:&#10;&#10;### Discipline-Enforcing Skills (rules/requirements)&#10;&#10;**Examples:** TDD, verification-before-completion, designing-before-coding&#10;&#10;**Test with:**&#10;- Academic questions: Do they understand the rules?&#10;- Pressure scenarios: Do they comply under stress?&#10;- Multiple pressures combined: time + sunk cost + exhaustion&#10;- Identify rationalizations and add explicit counters&#10;&#10;**Success criteria:** Agent follows rule under maximum pressure&#10;&#10;### Technique Skills (how-to guides)&#10;&#10;**Examples:** condition-based-waiting, root-cause-tracing, defensive-programming&#10;&#10;**Test with:**&#10;- Application scenarios: Can they apply the technique correctly?&#10;- Variation scenarios: Do they handle edge cases?&#10;- Missing information tests: Do instructions have gaps?&#10;&#10;**Success criteria:** Agent successfully applies technique to new scenario&#10;&#10;### Pattern Skills (mental models)&#10;&#10;**Examples:** reducing-complexity, information-hiding concepts&#10;&#10;**Test with:**&#10;- Recognition scenarios: Do they recognize when pattern applies?&#10;- Application scenarios: Can they use the mental model?&#10;- Counter-examples: Do they know when NOT to apply?&#10;&#10;**Success criteria:** Agent correctly identifies when/how to apply pattern&#10;&#10;### Reference Skills (documentation/APIs)&#10;&#10;**Examples:** API documentation, command references, library guides&#10;&#10;**Test with:**&#10;- Retrieval scenarios: Can they find the right information?&#10;- Application scenarios: Can they use what they found correctly?&#10;- Gap testing: Are common use cases covered?&#10;&#10;**Success criteria:** Agent finds and correctly applies reference information&#10;&#10;## Common Rationalizations for Skipping Testing&#10;&#10;| Excuse | Reality |&#10;|--------|---------|&#10;| "Skill is obviously clear" | Clear to you ≠ clear to other agents. Test it. |&#10;| "It's just a reference" | References can have gaps, unclear sections. Test retrieval. |&#10;| "Testing is overkill" | Untested skills have issues. Always. 15 min testing saves hours. |&#10;| "I'll test if problems emerge" | Problems = agents can't use skill. Test BEFORE deploying. |&#10;| "Too tedious to test" | Testing is less tedious than debugging bad skill in production. |&#10;| "I'm confident it's good" | Overconfidence guarantees issues. Test anyway. |&#10;| "Academic review is enough" | Reading ≠ using. Test application scenarios. |&#10;| "No time to test" | Deploying untested skill wastes more time fixing it later. |&#10;&#10;**All of these mean: Test before deploying. No exceptions.**&#10;&#10;## Match the Form to the Failure&#10;&#10;Before writing guidance, classify the baseline failure. The form that bulletproofs one failure type measurably backfires on another.&#10;&#10;| Baseline failure | Right form | Wrong form |&#10;|---|---|---|&#10;| Skips/violates a rule under pressure (knows better, does it anyway) | Prohibition + rationalization table + red flags (see Bulletproofing below) | Soft guidance ("prefer...", "consider...") |&#10;| Complies, but output has the wrong shape (bloated prompt, buried verdict, restated spec) | Positive recipe or contract: state what the output IS — its parts, in order | Prohibition list ("don't restate", "never narrate") |&#10;| Omits a required element from something they already produce | Structural: REQUIRED field or slot in the template they fill in | Prose reminders near the template |&#10;| Behavior should depend on a condition | Conditional keyed to an observable predicate ("if the brief exists, reference it") | Unconditional rule + exemption clauses |&#10;&#10;**Why prohibitions backfire on shaping problems:** under a competing incentive ("make the prompt self-contained"), agents negotiate with "don't X". In head-to-head wording tests on dispatch-prompt guidance, the prohibition arm produced clearly more of the unwanted content than the recipe arm (fully separated distributions), and trended worse than even the no-guidance control — micro-test your own case rather than assuming, but never reach for the prohibition by default. A recipe leaves nothing to negotiate: the output matches the stated shape or it doesn't.&#10;&#10;**Rules for whichever form you pick:**&#10;- **No nuance clauses.** "Don't X unless it matters" reopens the negotiation — appending a single nuance clause to a winning recipe degraded it from consistent to noisy in the same wording tests. Express a real exception as its own conditional on an observable predicate.&#10;- **Exemption clauses don't scope.** "This limit doesn't apply to code blocks" still suppresses code blocks. If part of the output must be exempt, restructure so the rule can't reach it.&#10;&#10;## Bulletproofing Skills Against Rationalization&#10;&#10;Skills that enforce discipline (like TDD) need to resist rationalization. Agents are smart and will find loopholes when under pressure.&#10;&#10;**Scope:** this toolkit is for discipline failures — an agent that knows the rule and skips it under pressure. For wrong-shaped output or omitted elements, prohibition-based bulletproofing backfires; use the forms in Match the Form to the Failure instead.&#10;&#10;**Psychology note:** Understanding WHY persuasion techniques work helps you apply them systematically. See persuasion-principles.md for research foundation (Cialdini, 2021; Meincke et al., 2025) on authority, commitment, scarcity, social proof, and unity principles.&#10;&#10;### Close Every Loophole Explicitly&#10;&#10;Don't just state the rule - forbid specific workarounds:&#10;&#10;&amp;lt;Bad&amp;gt;&#10;```markdown&#10;Write code before test? Delete it.&#10;```&#10;&amp;lt;/Bad&amp;gt;&#10;&#10;&amp;lt;Good&amp;gt;&#10;```markdown&#10;Write code before test? Delete it. Start over.&#10;&#10;**No exceptions:**&#10;- Don't keep it as "reference"&#10;- Don't "adapt" it while writing tests&#10;- Don't look at it&#10;- Delete means delete&#10;```&#10;&amp;lt;/Good&amp;gt;&#10;&#10;### Address "Spirit vs Letter" Arguments&#10;&#10;Add foundational principle early:&#10;&#10;```markdown&#10;**Violating the letter of the rules is violating the spirit of the rules.**&#10;```&#10;&#10;This cuts off entire class of "I'm following the spirit" rationalizations.&#10;&#10;### Build Rationalization Table&#10;&#10;Capture rationalizations from baseline testing (see Testing section below). Every excuse agents make goes in the table:&#10;&#10;```markdown&#10;| Excuse | Reality |&#10;|--------|---------|&#10;| "Too simple to test" | Simple code breaks. Test takes 30 seconds. |&#10;| "I'll test after" | Tests passing immediately prove nothing. |&#10;| "Tests after achieve same goals" | Tests-after = "what does this do?" Tests-first = "what should this do?" |&#10;```&#10;&#10;### Create Red Flags List&#10;&#10;Make it easy for agents to self-check when rationalizing:&#10;&#10;```markdown&#10;## Red Flags - STOP and Start Over&#10;&#10;- Code before test&#10;- "I already manually tested it"&#10;- "Tests after achieve the same purpose"&#10;- "It's about spirit not ritual"&#10;- "This is different because..."&#10;&#10;**All of these mean: Delete code. Start over with TDD.**&#10;```&#10;&#10;### Update SDO for Violation Symptoms&#10;&#10;Add to description: symptoms of when you're ABOUT to violate the rule:&#10;&#10;```yaml&#10;description: use when implementing any feature or bugfix, before writing implementation code&#10;```&#10;&#10;## RED-GREEN-REFACTOR for Skills&#10;&#10;Follow the TDD cycle:&#10;&#10;### RED: Write Failing Test (Baseline)&#10;&#10;Run pressure scenario with subagent WITHOUT the skill. Document exact behavior:&#10;- What choices did they make?&#10;- What rationalizations did they use (verbatim)?&#10;- Which pressures triggered violations?&#10;&#10;This is "watch the test fail" - you must see what agents naturally do before writing the skill.&#10;&#10;### GREEN: Write Minimal Skill&#10;&#10;Write skill that addresses those specific rationalizations. Don't add extra content for hypothetical cases.&#10;&#10;Run same scenarios WITH skill. Agent should now comply.&#10;&#10;### REFACTOR: Close Loopholes&#10;&#10;Agent found new rationalization? Add explicit counter. Re-test until bulletproof.&#10;&#10;### Micro-Test Wording Before Full Scenarios&#10;&#10;Full pressure-scenario runs are the final gate, but they are slow and expensive per iteration. Verify the wording itself first with micro-tests:&#10;&#10;1. **One fresh-context sample per call** — a raw API call, or a single-shot subagent if you don't have API access. System prompt = the realistic context the guidance will live in (the full skill or prompt template, not the guidance in isolation); user message = a task that tempts the failure.&#10;2. **Always include a no-guidance control.** If the control doesn't exhibit the failure, there is nothing to fix — stop, don't author the guidance.&#10;3. **5+ reps per variant.** Single samples lie.&#10;4. **Manually read every flagged match.** Score programmatically if you like, but template echoes and quoted counter-examples masquerade as hits; automated counts alone overstate both failure and success.&#10;5. **Variance is a metric.** When guidance lands, reps converge on the same shape. Five different interpretations across five reps means the wording isn't binding — tighten the form before adding words.&#10;&#10;Micro-tests verify wording; they do not replace pressure scenarios for discipline skills.&#10;&#10;**Testing methodology:** See [testing-skills-with-subagents.md](testing-skills-with-subagents.md) for the complete testing methodology:&#10;- How to write pressure scenarios&#10;- Pressure types (time, sunk cost, authority, exhaustion)&#10;- Plugging holes systematically&#10;- Meta-testing techniques&#10;&#10;## Anti-Patterns&#10;&#10;### ❌ Narrative Example&#10;"In session 2025-10-03, we found empty projectDir caused..."&#10;**Why bad:** Too specific, not reusable&#10;&#10;### ❌ Multi-Language Dilution&#10;example-js.js, example-py.py, example-go.go&#10;**Why bad:** Mediocre quality, maintenance burden&#10;&#10;### ❌ Code in Flowcharts&#10;```dot&#10;step1 [label="import fs"];&#10;step2 [label="read file"];&#10;```&#10;**Why bad:** Can't copy-paste, hard to read&#10;&#10;### ❌ Generic Labels&#10;helper1, helper2, step3, pattern4&#10;**Why bad:** Labels should have semantic meaning&#10;&#10;## STOP: Before Moving to Next Skill&#10;&#10;**After writing ANY skill, you MUST STOP and complete the deployment process.**&#10;&#10;**Do NOT:**&#10;- Create multiple skills in batch without testing each&#10;- Move to next skill before current one is verified&#10;- Skip testing because "batching is more efficient"&#10;&#10;**The deployment checklist below is MANDATORY for EACH skill.**&#10;&#10;Deploying untested skills = deploying untested code. It's a violation of quality standards.&#10;&#10;## Skill Creation Checklist (TDD Adapted)&#10;&#10;**IMPORTANT: Create a todo for EACH checklist item below.**&#10;&#10;**RED Phase - Write Failing Test:**&#10;- [ ] Create pressure scenarios (3+ combined pressures for discipline skills)&#10;- [ ] Run scenarios WITHOUT skill - document baseline behavior verbatim&#10;- [ ] Identify patterns in rationalizations/failures&#10;&#10;**GREEN Phase - Write Minimal Skill:**&#10;- [ ] Name uses only letters, numbers, hyphens (no parentheses/special chars)&#10;- [ ] YAML frontmatter with required `name` and `description` fields (max 1024 chars; see [spec](https://agentskills.io/specification))&#10;- [ ] Description starts with "Use when..." and includes specific triggers/symptoms&#10;- [ ] Description written in third person&#10;- [ ] Keywords throughout for search (errors, symptoms, tools)&#10;- [ ] Clear overview with core principle&#10;- [ ] Address specific baseline failures identified in RED&#10;- [ ] Guidance form matches the failure type (see Match the Form to the Failure)&#10;- [ ] For behavior-shaping guidance: wording micro-tested against a no-guidance control (5+ reps, every flagged match read manually) — N/A for pure reference skills&#10;- [ ] Code inline OR link to separate file&#10;- [ ] One excellent example (not multi-language)&#10;- [ ] Run scenarios WITH skill - verify agents now comply&#10;&#10;**REFACTOR Phase - Close Loopholes:**&#10;- [ ] Identify NEW rationalizations from testing&#10;- [ ] Add explicit counters (if discipline skill)&#10;- [ ] Build rationalization table from all test iterations&#10;- [ ] Create red flags list&#10;- [ ] Re-test until bulletproof&#10;&#10;**Quality Checks:**&#10;- [ ] Small flowchart only if decision non-obvious&#10;- [ ] Quick reference table&#10;- [ ] Common mistakes section&#10;- [ ] No narrative storytelling&#10;- [ ] Supporting files only for tools or heavy reference&#10;&#10;**Deployment:**&#10;- [ ] Commit skill to git and push to your fork (if configured)&#10;- [ ] Consider contributing back via PR (if broadly useful)&#10;&#10;## Discovery Workflow&#10;&#10;How future agents find your skill:&#10;&#10;1. **Encounters problem** ("tests are flaky")&#10;2. **Searches skills** (greps descriptions, browses categories)&#10;3. **Finds SKILL** (description matches)&#10;4. **Scans overview** (is this relevant?)&#10;5. **Reads patterns** (quick reference table)&#10;6. **Loads example** (only when implementing)&#10;&#10;**Optimize for this flow** - put searchable terms early and often.</pre>
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
class: swiss-light roles-page comparison-page
---

<div class="page-head">
  <div class="page-kicker">TWO PHILOSOPHIES / ONE CONTRAST</div>
  <h1 class="page-title">Superpowers VS Matt Pocock Skills</h1>
</div>

<div class="roles-grid comparison-grid">
  <section class="role-column role-human">
    <div class="role-meta">SUPERPOWERS / 5 YEARS</div>
    <h2>ジュニアが迷わない<br>手順書をつくる</h2>
    <p class="comparison-copy">5年ほど経験を積んだエンジニアと設計を詰め、ジュニアでも実装できる粒度まで落とす。実装は手順書に沿って任せる。</p>
  </section>

  <div class="role-divider">
    <span>VS</span>
  </div>

  <section class="role-column role-ai">
    <div class="role-meta">MATT POCOCK SKILLS / 10+ YEARS</div>
    <h2>熟練者には<br>境界だけを渡す</h2>
    <p class="comparison-copy">10年以上の経験を持つエンジニアに細かな手順を渡しても、その判断力までは引き出せない。譲れない条件を決め、実装方法は任せる。</p>
  </section>
</div>

<!--
ここでいう「5年」と「10年以上」は、AIの能力差を説明するための比喩です。

Superpowersは、経験のあるエンジニアと設計を詰めたうえで、ジュニアでも迷わず実装できるところまで手順を細かくします。

Matt Pocock Skillsは、熟練者に細かな手順を渡しても判断力を十分に引き出せないと考えます。譲れない境界だけを決め、具体的な実装は任せます。
-->

---
layout: default
class: swiss-dark star-comparison-page
---

<div class="page-head">
  <div class="page-kicker kicker-on-dark">GITHUB STARS / SEP 9, 2026</div>
  <h1 class="page-title title-on-dark">Matt Pocock Skillsが急速に差を縮めている</h1>
</div>

<div class="star-comparison">
  <img class="star-history-image" src="/star-history-202699.png" alt="SuperpowersとMatt Pocock SkillsのStar推移">

  <div class="star-summary">
    <div class="star-summary-row">
      <span>現在のStar差</span>
      <strong>約2.7万</strong>
      <small>283.1k / 256.6k</small>
    </div>
    <div class="star-summary-row star-summary-accent">
      <span>直近1週間の増加</span>
      <strong>約4.3倍</strong>
      <small>13.4k / 3.1k</small>
    </div>
  </div>
</div>

<!--
Superpowersが先に伸びましたが、後発のMatt Pocock Skillsが急速に差を縮めています。

2026年9月9日時点の差は約2万7千Starです。
直近1週間の増加数を比べると、Matt Pocock SkillsはSuperpowersの約4.3倍でした。

この勢いなら追いつきそうだと感じています。
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
