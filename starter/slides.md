---
theme: '@alexop/slidev-theme-brand'
addons:
  - '@alexop/slidev-addon-utils'
title: 'Clean Code Is Sexy Again'
transition: slide-left
mdc: true
drawings:
  persist: false
info: |
  ## Clean Code Is Sexy Again — Making Your Vue Project AI-Ready

  Clean code went from nice-to-have to business-critical, because AI agents
  work the same way good engineers do — and your codebase is their UX.

  By Alexander Opalic — alexop.dev
hideFooter: true
layout: image
image: /madvue-2026.png
backgroundSize: contain
---

<!--
Vue MAD 2026 -- Madrid.

TRANSITION: Now the talk title...
-->

---

<PartSlide
  title="Clean Code Is Sexy Again"
  subtitle="Making Your Vue Project AI-Ready · Vue MAD 2026 · Alexander Opalic"
/>

<!--
[breathe] [scan room]

Welcome -- excited to be here.
Talk about something I would have rolled my eyes at two years ago:
clean code. And why it just got way more interesting.

TRANSITION: Quick intro...
-->

---

# About me

<About />

<!--
Quick intro

Alexander Opalic -- Vue 8+ years
Otto Payments -- e-commerce
Blog at alexop.dev -- mostly Vue and AI now

TRANSITION: Before we start -- I want to know where YOU are on this journey.
-->

---
layout: image
image: /five-levels.png
backgroundSize: contain
---

<!--
Dan Shapiro framed this beautifully. Six levels, like driving automation.

L0 spicy autocomplete -- AI as a smarter Stack Overflow.
L1 coding intern -- writes boilerplate, you review every line.
L2 junior dev -- pair programmer, you trade off in real time.
L3 developer -- AI writes most of it, you are the verification bottleneck.
L4 senior dev -- runs unattended, you check the final result.
L5 software factory -- you manage goals, AI defines, ships, fixes.

The question for you: where are you actually sitting?

TRANSITION: Credit where it's due -- this framing is from a great blog post.
-->

---

# Credit where it's due

<div class="text-center text-sm op-60 mb-8">The "five levels" framing comes from an awesome blog post.</div>

<div class="max-w-2xl mx-auto">

<Card glow>
<div class="flex items-start gap-4">
  <div class="i-ph-article-bold flex-shrink-0 mt-1" style="color: #ff6bed; width: 40px; height: 40px" />
  <div>
    <div class="text-xl font-bold" style="color: #ff6bed">The Five Levels: From Spicy Autocomplete to the Software Factory</div>
    <div class="text-sm op-70 mt-2">Dan Shapiro · January 2026</div>
    <div class="mt-3 flex items-center gap-2 text-xs op-60">
      <div class="i-ph-link" />
      <span>danshapiro.com/blog/2026/01/the-five-levels-from-spicy-autocomplete-to-the-software-factory</span>
    </div>
  </div>
</div>
</Card>

</div>

<div class="mt-8 text-center op-70 text-sm max-w-2xl mx-auto">
  Go read it. It's the cleanest mental model I've seen for where AI-assisted dev is heading.
</div>

<!--
Quick credit before we move on.

The framing -- the six levels, the driving analogy --
that is all Dan Shapiro. January 2026 blog post.

If you take ONE link from this talk, take that one.
It is the cleanest mental model I have found
for where AI-assisted development is heading.

TRANSITION: For context, here's where I am -- and why.
-->

---
layout: statement
transition: fade-out
---

# Making a talk about AI is really hard

<!--
[pause]

The space moves every week.
Half of what I write is stale by the time I hit publish.

So this talk is NOT about the latest model or the hottest tool.
It is about the part that does not change:
your codebase.

TRANSITION: And to prove the space moves every week -- exhibit A from two weeks ago.
-->

---

# Two weeks ago: Bun got rewritten in Rust

<div class="text-center text-sm op-60 mb-6">A major JavaScript runtime. From Zig to Rust. Almost entirely by AI.</div>

<div class="grid grid-cols-3 gap-6 mt-8">

<Card glow>
<div class="text-xs op-50 mb-2">Lines of code</div>
<div class="text-4xl font-bold" style="color: #ff6bed">~1M</div>
<div class="text-sm mt-2 op-80">+1,009,257 / −4,024 in one PR</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-2">Time</div>
<div class="text-4xl font-bold" style="color: #ff6bed">~10 days</div>
<div class="text-sm mt-2 op-80">6,755 commits · 2,188 files</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-2">Reviewers</div>
<div class="text-4xl font-bold" style="color: #ff6bed">Claude</div>
<div class="text-sm mt-2 op-80">near-zero human review · ~13k unsafe blocks</div>
</Card>

</div>

<div class="mt-8 text-center text-lg max-w-3xl mx-auto">
  Whether it ships or it explodes — <strong style="color: #ff6bed">the industry just shifted.</strong>
</div>

<!--
[pause]

Exhibit A for why this talk is hard.

Two weeks ago -- Bun, one of the most-hyped JavaScript runtimes,
got rewritten from Zig to Rust.

One million lines of code. Ten days. By an agent.

Bun is owned by Anthropic now. The rewrite was almost entirely Claude.
Near-zero human review. Thirteen thousand unsafe blocks.

The Rust community melted down. The Zig community melted down.
The reviewers were Claude. Claude marked one of the follow-up PRs as AI slop.

Whether this is a triumph or a disaster -- I genuinely don't know yet.

But here is what I do know:
this is the world we ship into now.
A major OSS project rewritten in two weeks by a machine.

The times are crazy. The pace is real. This is not slowing down.

TRANSITION: Which brings us to the quote that sums up the whole shift.
-->

---
layout: quote
transition: fade
---

<QuoteCard author="Simon Willison" highlight="everything else">
  Being able to read a detailed specification and transform it into lines of code is the thing that's being automated away. What's left is everything else.
</QuoteCard>

<!--
QUOTE: Simon Willison -- "developers won't write code by hand"

[slow down]
Typing the code is the part that gets automated.
"Everything else" -- the deciding, the architecting, the validating --
that is what is left.

TRANSITION: So here is the contradiction every Vue dev is feeling.
-->

---
layout: statement
transition: fade-out
---

# "You don't have to write code anymore."

<v-click>

# That's half true.

</v-click>

<v-click>

# It only works if your project lets the AI work.

</v-click>

<!--
[wait]

Everyone keeps saying this line.

CLICK -- Half true.

CLICK -- It only works if your codebase lets the agent work.

And in some of my repos it 10x'd me.
In others it produced complete garbage.

Same person. Same agent. Same model.
Different codebases.

TRANSITION: So the question is...
-->

---
layout: statement
transition: fade-out
---

# Why does AI succeed in some codebases and fail in others?

<!--
[hold the silence]

This is the question.
The rest of the talk is the answer.

TRANSITION: Here is what we are going to do.
-->

---

<PyramidOutline :items="[
  { title: 'The Problem', subtitle: 'Why AI 10x some codebases and breaks others' },
  { title: 'What an Agent Actually Is', subtitle: 'A loop, not a magic box' },
  { title: 'Context', subtitle: 'Does it know why things exist?' },
  { title: 'Feedback Loops', subtitle: 'Does it know when it is wrong?' },
  { title: 'Discoverability', subtitle: 'Can the agent find the right code?' },
  { title: 'Where this is heading', subtitle: 'The role merge' }
]" />

<!--
Six beats.

Problem first. Then what an agent really is.
Then three concrete buckets you can act on Monday.
Then where this is going.

TRANSITION: Quick scope check before we dive in.
-->

---

# Scope check

<div class="text-center text-sm op-60 mb-6">Before we dive in — let me narrow the focus.</div>

<div class="grid grid-cols-2 gap-6">

<Card variant="muted">
<div class="text-xs font-bold mb-2" style="color: rgba(255,255,255,0.6)">NOT this talk</div>
<ul class="text-sm space-y-2 op-80">
  <li>· Spec-driven development</li>
  <li>· A deep dive into my personal workflow</li>
  <li>· How teams reorganize around agents</li>
  <li>· The latest model or hottest tool</li>
</ul>
<div class="mt-3 text-xs op-50">All separate talks.</div>
</Card>

<Card glow>
<div class="text-xs font-bold mb-2" style="color: #ff6bed">THIS talk</div>
<ul class="text-sm space-y-2 op-80">
  <li>· Foundations under a Vue codebase</li>
  <li>· Brownfield projects you already have</li>
  <li>· How to stop the agent shipping slop</li>
  <li>· Things you can do Monday</li>
</ul>
<div class="mt-3 text-xs" style="color: #ff6bed">The substrate. Not the workflow.</div>
</Card>

</div>

<!--
Before we dive in -- I want to narrow the focus.

OUT OF SCOPE.
This is NOT a talk about spec-driven development.
It is NOT a deep dive into my personal workflow -- I'll show a glimpse later, but the workflow is a separate talk.
It is NOT about how teams should reorganize around agents.
And it is NOT about the latest model or hottest tool.

All of those are interesting -- separate talks.

IN SCOPE.
This is about FOUNDATIONS in a Vue codebase.
Especially BROWNFIELD -- the real projects you already have, not greenfield demos.
The stuff you do so the agent stops shipping slop every time you prompt it.
Things you can act on MONDAY.

The SUBSTRATE under your project. Not the workflow on top of it.

TRANSITION: Let's start with what an agent is.
-->

---
transition: fade
---

<PartSlide
  part="1"
  title="What an Agent Actually Is"
  subtitle="A new engineer joining your team"
/>

<!--
[scan room]

Most Vue devs treat agents as magic.
Magic is the wrong mental model.
-->

---

# How an AI agent works

<div class="flex justify-center mt-4">

<AgentLoopDemo />

</div>

<!--
That is the whole picture.
Read context. Pick a tool. Run it. Read the result. Repeat.

CLICK -- Bounded by three things.

CLICK -- Context window, tools, ability to verify.
That is it.

CLICK -- The analogy that unlocks everything: a new engineer.
You would not throw a new hire into your worst legacy module
and expect a feature in a week. Same with agents.

TRANSITION: Let me strip the magic. Here is what a tool actually is.
-->

---

# A tool is just a function

```ts
const TOOLS = {
  read: {
    description: 'Read file with line numbers',
    schema: { path: 'string' },
    execute: async (args) => Bun.file(args.path).text()
  },
  bash: {
    description: 'Run a shell command',
    schema: { cmd: 'string' },
    execute: async (args) => $`sh -c ${args.cmd}`.text()
  },
  edit: {
    description: 'Find and replace in file',
    schema: { path: 'string', old: 'string', new: 'string' },
    execute: edit
  }
}
```

<div class="mt-6 text-center text-lg op-80">
  Name · description · schema · function.<br/>
  You hand the list to the LLM. <strong style="color: #ff6bed">It picks which one to call.</strong>
</div>

<!--
A tool is a function. That is the whole concept.

Name. Description. Schema. The code that runs.

The LLM does not "know" how to read files.
You give it a function called read, you describe what it does,
and you let it call it.

That is the entire mechanism.

TRANSITION: And the loop is even simpler.
-->

---

# The loop is just recursion

```ts
async function agentLoop(messages, systemPrompt) {
  const response = await callApi(messages, systemPrompt, TOOLS)
  const toolResults = await runTools(response.content)

  // No tools called → the agent is done
  if (toolResults.length === 0) return messages

  // Tools called → loop with results appended
  return agentLoop(
    [...messages, response, toolResults],
    systemPrompt
  )
}
```

<div class="mt-6 text-center text-lg op-80">
  Call API · run tools · <strong style="color: #ff6bed">repeat until no more tool calls.</strong>
</div>

<!--
And the loop is just recursion.

Call the API. Run whatever tools the model asked for.
Loop again with the results appended to the conversation.

When the model returns no tool calls -- it is done.

That is the entire agent architecture.
Everyone is talking about agents like they are a mystery. They are not.

TRANSITION: So how big is this whole thing?
-->

---
layout: statement
transition: fade-out
---

# That's the whole agent.

<v-click>

# ~350 lines of TypeScript. No magic.

</v-click>

<div v-click class="mt-12 text-base op-60 max-w-3xl mx-auto text-center">
  A function that calls itself<br/>
  with the results of the previous call.
</div>

<!--
[pause]

That is nanocode. I built it to understand Claude Code from the inside.
~350 lines of TypeScript.

CLICK

CLICK

A function that calls itself with the results of the previous call.

Once you see an agent this way, the question stops being
"how does the magic work?"

The question becomes:
why does the same simple loop work brilliantly in one repo
and fall apart in another?

That is what the rest of this talk is about.

TRANSITION: Three things the agent needs from your codebase.
-->

---

# The three buckets

<div class="grid grid-cols-3 gap-6 mt-10">

<Card glow>
<div class="text-xs op-50 mb-2">01</div>
<div class="text-2xl font-bold mb-3" style="color: #ff6bed">Context</div>
<div class="text-sm op-80">Does the agent know why things exist?</div>
<div class="mt-4 text-xs op-50">Docs. AGENTS.md. ADRs. The rules of your house.</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-2">02</div>
<div class="text-2xl font-bold mb-3" style="color: #ff6bed">Feedback loops</div>
<div class="text-sm op-80">Does the agent know when it is wrong?</div>
<div class="mt-4 text-xs op-50">Tests. Linting. Types. Your backpressure.</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-2">03</div>
<div class="text-2xl font-bold mb-3" style="color: #ff6bed">Discoverability</div>
<div class="text-sm op-80">Can the agent find the right code?</div>
<div class="mt-4 text-xs op-50">Modular monolith. Monorepo structure. Naming.</div>
</Card>

</div>

<!--
Three buckets. These recur in the whole rest of the talk.

Context FIRST -- the rules of your house.
Define the structure, the tests, the style guide --
everything a new dev would also need.
Once context is solid, the agent can even implement
the other two buckets for you.

Feedback: does it know when it broke something?
Discoverability: can it FIND the right code?

A codebase that is hard for HUMANS is hard for agents.
Same patterns. Different stakes now.

TRANSITION: The quotable moment.
-->

---
layout: statement
transition: fade-out
---

# Clean code isn't nice-to-have anymore.

<v-click>

# It's the substrate AI runs on.

</v-click>

<div v-click class="mt-12 text-base op-60 max-w-3xl mx-auto text-center">
  Modular boundaries. Tests. Docs.<br/>
  The patterns that made code maintainable for humans<br/>
  are the same patterns that make code legible for agents.
</div>

<!--
[pause before speaking. let it land]

You don't need new patterns for AI.
The patterns you already fight for in code review --
the ones the senior dev keeps insisting on --
those are the patterns that make agents work.

If you have spent years caring about architecture, testability,
naming, separation of concerns --
you have been training for this moment without knowing it.

CLICK
CLICK

A codebase that is hard for humans is hard for agents.
Sprawl, hidden coupling, magical state --
humans hate it. Agents fail at it.

TRANSITION: Concrete. In Vue. Starting with context.
-->

---
transition: fade
---

<PartSlide
  part="2"
  title="Context"
  subtitle="AGENTS.md is the unlock"
/>

<!--
[scan room]

Bucket one. The foundation.
With context we define the structure, how we test, the style guide --
everything a new dev would also need.
Once context is solid, you can ask the agent to add oxlint,
wire up vitest, scaffold the folder layout -- it knows the rules now.
-->

---
layout: image
image: /memento.png
backgroundSize: contain
---

<!--
Claude Code is Leonard from Memento.

Every turn, the context resets.
No long-term memory. No yesterday.

So he tattoos the rules on his body.
He photographs the people he meets.
He writes notes he can trust.

That is AGENTS.md.
The tattoo your agent reads every single turn,
because tomorrow it will not remember today.

TRANSITION: So what does that look like in practice?
-->

---

# Bad AGENTS.md · Good AGENTS.md

<div class="text-center text-sm op-60 mb-4">Same goal. One floods the context. One points at docs.</div>

<div class="grid grid-cols-2 gap-4">

<div>

<div class="text-xs font-bold mb-2" style="color: rgba(255,255,255,0.6)">BAD — the everything dump</div>

```md
# AGENTS.md

## Project Overview
...50 lines...

## Code Style
...200 lines of formatting rules...

## Architecture Decisions
...150 lines of history...

## Gotchas
...300 lines of edge cases...

## Testing Conventions
...100 lines...
```

<div class="mt-2 text-xs" style="color: #ef4444">
~2000 lines. Half your context gone before any work starts.
</div>

</div>

<div>

<div class="text-xs font-bold mb-2" style="color: #ff6bed">GOOD — points at the docs</div>

```md
# AGENTS.md

Run `pnpm lint:fix && pnpm typecheck`
after code changes.

## Stack
Nuxt 4, @nuxt/content v3, @nuxt/ui v3

## Structure
- `app/` — Vue application
- `content/` — Markdown files

## Further reading

**IMPORTANT:** read the relevant doc
below before starting any task.

- `docs/nuxt-content-gotchas.md`
- `docs/testing-strategy.md`
- `docs/SYSTEM_KNOWLEDGE_MAP.md`
```

<div class="mt-2 text-xs" style="color: #ff6bed">
~50 lines. Loads docs only when relevant.
</div>

</div>

</div>

<div v-click class="mt-4 text-center text-lg">
  Progressive disclosure — <strong style="color: #ff6bed">the right context at the right time.</strong>
</div>

<!--
[breathe]

Two AGENTS.md files. Same goal.

LEFT -- the instinct everyone has on day one.
Dump everything. Style rules ESLint already enforces.
Bug post-mortems. Every gotcha you ever hit.
2000 lines. Half your context window gone before any work starts.
HumanLayer calls this the dumb zone -- the model degrades when context is noisy.

RIGHT -- the version that survives.
ONE LINE for tooling: "Run pnpm lint:fix and pnpm typecheck after changes."
The agent runs the build, reads the error, fixes itself.
That is backpressure -- you stop being the linter.

Then a short stack and structure section.
Then the magic part -- "Further reading" with the IMPORTANT instruction.
The agent loads content-gotchas.md ONLY when touching content.
testing-strategy.md ONLY when writing a test.
That is progressive disclosure -- credit to Lin Yuan and Poteto.

Two filters before a line goes in AGENTS.md:
ONE -- can a tool enforce it? Then don't write prose about it.
TWO -- is it universal, or situational? Situational goes in /docs.

CLICK -- The right context at the right time.

TRANSITION: But you don't even need to write this yourself.
-->

---

# Don't write it yourself — copy `brainmaxxing`

<div class="text-center text-sm op-60 mb-6"><code>github.com/poteto/brainmaxxing</code> — persistent memory + skills + hooks for Claude Code.</div>

<div class="grid grid-cols-3 gap-5">

<Card glow>
<div class="text-xs op-50 mb-2"><code>brain/</code></div>
<div class="text-xl font-bold mb-3" style="color: #ff6bed">The vault</div>
<div class="text-sm op-80">An Obsidian-style markdown vault.</div>
<div class="mt-3 text-xs op-60">The agent reads it at session start. Writes to it after mistakes. Compounds over time.</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-2"><code>.claude/skills/</code></div>
<div class="text-xl font-bold mb-3" style="color: #ff6bed">Six skills</div>
<div class="text-sm op-80"><code>/reflect</code> distils a session into the vault.</div>
<div class="mt-3 text-xs op-60">Plus <code>/ruminate</code>, <code>/meditate</code>, <code>/plan</code>, <code>/review</code>, <code>/brain</code>.</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-2"><code>.claude/hooks/</code></div>
<div class="text-xl font-bold mb-3" style="color: #ff6bed">Two hooks</div>
<div class="text-sm op-80"><code>SessionStart</code> injects the brain.</div>
<div class="mt-3 text-xs op-60"><code>PostToolUse</code> re-indexes <code>brain/</code> when files drift. Pure bash, no LLM.</div>
</Card>

</div>

<div v-click class="mt-10 text-center">
  <div class="text-xs op-60 mb-2">Install</div>
  <div class="text-base"><code style="color: #ff6bed">"Install brainmaxxing from github.com/poteto/brainmaxxing into this project."</code></div>
  <div class="text-xs op-50 mt-2">No script. Just tell Claude. It copies the files and merges <code>settings.json</code>.</div>
</div>

<!--
You can write AGENTS.md from scratch. Or you can stand on Poteto's shoulders.

brainmaxxing is the strategy in a box. Three pieces:

ONE -- brain/. A markdown vault. Obsidian opens it natively.
The SessionStart hook cats brain/index.md into every session.
That is the persistent memory layer the LLM does not have on its own.

TWO -- six skills. /reflect is the killer.
After a hard session, /reflect distils what the agent learned
into the vault. Next session it already knows. Compounding leverage.

THREE -- two hooks, both pure bash. No LLM in the loop.
SessionStart injects the brain. PostToolUse re-indexes when
files in brain/ change. The factory runs itself.

CLICK -- The install is wild. No npm install. No script.
You literally tell Claude "install brainmaxxing from this URL"
and the agent does the copying.

TRANSITION: And the bonus -- it ships with 16 principles built in.
-->

---

# 16 principles you don't have to write

<div class="text-center text-sm op-60 mb-6">In <code>brain/principles/</code> — the rules your AGENTS.md never has to spell out.</div>

<div class="grid grid-cols-2 gap-x-8 gap-y-3 max-w-5xl mx-auto">

<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">01</div>
  <div class="text-sm" style="color: #ff6bed">guard-the-context-window</div>
</div>
<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">02</div>
  <div class="text-sm" style="color: #ff6bed">fix-root-causes</div>
</div>

<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">03</div>
  <div class="text-sm" style="color: #ff6bed">subtract-before-you-add</div>
</div>
<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">04</div>
  <div class="text-sm" style="color: #ff6bed">prove-it-works</div>
</div>

<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">05</div>
  <div class="text-sm op-80">encode-lessons-in-structure</div>
</div>
<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">06</div>
  <div class="text-sm op-80">redesign-from-first-principles</div>
</div>

<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">07</div>
  <div class="text-sm op-80">never-block-on-the-human</div>
</div>
<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">08</div>
  <div class="text-sm op-80">exhaust-the-design-space</div>
</div>

<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">09</div>
  <div class="text-sm op-80">outcome-oriented-execution</div>
</div>
<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">10</div>
  <div class="text-sm op-80">boundary-discipline</div>
</div>

<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">11</div>
  <div class="text-sm op-80">cost-aware-delegation</div>
</div>
<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">12</div>
  <div class="text-sm op-80">foundational-thinking</div>
</div>

<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">13</div>
  <div class="text-sm op-80">experience-first</div>
</div>
<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">14</div>
  <div class="text-sm op-80">make-operations-idempotent</div>
</div>

<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">15</div>
  <div class="text-sm op-80">migrate-callers-then-delete-legacy-apis</div>
</div>
<div class="flex items-start gap-3">
  <div class="text-xs font-mono op-40 mt-0.5">16</div>
  <div class="text-sm op-80">serialize-shared-state-mutations</div>
</div>

</div>

<div v-click class="mt-8 text-center text-base op-90 max-w-3xl mx-auto">
  These are the things you'd otherwise <strong style="color: #ff6bed">rediscover the hard way</strong> over a year.
</div>

<!--
Sixteen principles. Built in.

[scan room]

I am not going to read all of them. I want you to PHOTOGRAPH this slide
and read it on the train home.

But the top four are the ones I lean on every day:

guard-the-context-window -- the whole reason we keep AGENTS.md small.
fix-root-causes -- when the agent ships a bug, fix the factory not the PR.
subtract-before-you-add -- the senior engineer's instinct.
prove-it-works -- if there is no test, it does not work.

These are not novel ideas. They are the things every senior engineer
learned the hard way. brainmaxxing wrote them down for you.

CLICK -- A year of rediscovery. Saved.

This is what my AGENTS.md strategy actually is:
a thin AGENTS.md that points at /docs (progressive disclosure)
plus brainmaxxing's vault + skills + principles underneath.

TRANSITION: But there is one trick that is even bigger.
-->

---
layout: statement
transition: fade-out
---

# Want VueUse-style composables?

<v-click>

# Give the agent VueUse.

</v-click>

<!--
[pause]

Hot take.

Agents are post-trained on READING CODE.
Not reading prose docs.
Stale docs in their training data are noise.

Real source in your tree is signal.

CLICK -- If you want the agent to write like VueUse,
let it READ VueUse.

TRANSITION: How.
-->

---
layout: quote
transition: fade
---

<QuoteCard author="Michael Arnaldi" highlight="setting up repositories">
  Most of my time as a programmer is now spent setting up repositories so that coding agents can act well inside them.
</QuoteCard>

<!--
QUOTE: Michael Arnaldi -- "Vibe Engineering Effect Apps: Just Clone the Repo"

The shift in his quote is the shift in the whole talk.
Programming is now: configuring the room the agent works in.

TRANSITION: One command. Try it tomorrow.
-->

---

# Vendor the library

<div class="text-sm op-60 mb-4">Pull the source into your repo as a git subtree.</div>

```bash
git subtree add --prefix=repos/vueuse \
  https://github.com/vueuse/vueuse main --squash
```

<div class="mt-4 text-sm op-60 mb-2">Then point AGENTS.md at it:</div>

```md
## Reference repositories

- `repos/vueuse/` — when writing new composables, mirror the
  patterns in `repos/vueuse/packages/core/use*/`.
- `repos/pinia/` — store patterns & private-state idioms.
- `repos/nuxt/` — module & plugin conventions.
```

<div v-click class="mt-8 grid grid-cols-2 gap-6">

<Card variant="muted">
<div class="text-xs op-60 mb-1">Why a subtree?</div>
<div class="text-sm">Squashed. Self-contained. Reviewable in diff. No submodule pain.</div>
</Card>

<Card glow>
<div class="text-xs op-60 mb-1">Result</div>
<div class="text-sm">Agent reads REAL VueUse source before writing your composable. VueUse-quality output without copy-paste.</div>
</Card>

</div>

<!--
One command. Vendors VueUse into your repo as a squashed subtree.

Then one line in AGENTS.md: "Mirror these patterns."

That is it.

CLICK

Why a subtree, not a submodule? No clone-time pain.
No "did you forget to init"? Just files.

Result -- the agent's pattern matching is now anchored on real code.
Pattern matching beats prompting.

I packaged this as a Claude Code skill: clone-repo.
Vendors any repo, wires it into AGENTS.md, done.

TRANSITION: One more layer to context -- extending the agent itself.
-->

---

# Bonus: extending the agent

<div class="grid grid-cols-2 gap-6 mt-4">

<Card glow>
<div class="text-sm font-bold mb-2" style="color: #ff6bed">Slash commands</div>
<div class="text-xs op-70">Bake your repo's workflows into the harness. <code>/spec</code>, <code>/review</code>, <code>/check</code>.</div>
</Card>

<Card glow>
<div class="text-sm font-bold mb-2" style="color: #ff6bed">Chat modes / personas</div>
<div class="text-xs op-70">Different personas for different jobs — designer, reviewer, debugger.</div>
</Card>

<Card glow>
<div class="text-sm font-bold mb-2" style="color: #ff6bed">MCP servers</div>
<div class="text-xs op-70">Figma → component. CloudWatch → incidents. Linear → ticket context.</div>
</Card>

<Card glow>
<div class="text-sm font-bold mb-2" style="color: #ff6bed">Persistent memory</div>
<div class="text-xs op-70"><code>brainmaxxing</code> — an Obsidian vault the agent reads at session start and writes to when it learns.</div>
</Card>

</div>

<div v-click class="mt-8 text-center max-w-3xl mx-auto">

<Callout type="warn">
Once your foundation is clean, these <strong>multiply your leverage</strong>.<br/>
If your foundation is messy, they <strong>multiply your chaos</strong>.
</Callout>

</div>

<!--
Quick tour. Not deep dives.

Slash commands -- recipe book for your repo.
Chat modes -- different brain for different jobs.
MCP servers -- give the agent eyes outside your repo. Figma. AWS. Linear.
Memory -- AGENTS.md is the STATIC onboarding doc. Brainmaxxing is the LIVING memory.

CLICK -- The warning.

If the foundation is clean, these are multipliers.
If the foundation is messy, they make the mess WORSE faster.

TRANSITION: Let me get concrete on slash commands -- the ones I run every day.
-->

---

# The slash commands I actually run

<div class="text-center text-sm op-60 mb-4">From <code>github.com/alexanderop/dotfiles</code>. Drop into any repo's <code>.claude/commands/</code>.</div>

<div class="grid grid-cols-2 gap-3">

<Card variant="muted">
<div class="font-mono text-sm font-bold" style="color: #ff6bed">/push</div>
<div class="text-xs op-70 mt-1">Commit staged changes with a real message and push.</div>
</Card>

<Card variant="muted">
<div class="font-mono text-sm font-bold" style="color: #ff6bed">/pr</div>
<div class="text-xs op-70 mt-1">Open a PR with summary + test plan, derived from the diff.</div>
</Card>

<Card variant="muted">
<div class="font-mono text-sm font-bold" style="color: #ff6bed">/check</div>
<div class="text-xs op-70 mt-1">Fan out parallel reviewers — Vue, a11y, security, perf, tests.</div>
</Card>

<Card variant="muted">
<div class="font-mono text-sm font-bold" style="color: #ff6bed">/fix-pipeline</div>
<div class="text-xs op-70 mt-1">Read failing CI logs, plan a fix, then apply it.</div>
</Card>

<Card variant="muted">
<div class="font-mono text-sm font-bold" style="color: #ff6bed">/review-coderabbit</div>
<div class="text-xs op-70 mt-1">Triage CodeRabbit comments, implement the valid ones.</div>
</Card>

<Card variant="muted">
<div class="font-mono text-sm font-bold" style="color: #ff6bed">/research</div>
<div class="text-xs op-70 mt-1">Spawn a research agent across web + docs + codebase.</div>
</Card>

<Card variant="muted">
<div class="font-mono text-sm font-bold" style="color: #ff6bed">/interview</div>
<div class="text-xs op-70 mt-1">Have the agent grill ME on a plan before I write the spec.</div>
</Card>

<Card glow>
<div class="font-mono text-sm font-bold" style="color: #ff6bed">/learn</div>
<div class="text-xs op-70 mt-1"><strong>The factory-fixer.</strong> Distil today's lessons into <code>AGENTS.md</code>.</div>
</Card>

</div>

<!--
These are MY commands. Live in my dotfiles -- github.com/alexanderop/dotfiles.

/push and /pr remove the friction in the shipping loop.
/check fans out five specialized reviewers on every diff -- in parallel.
/fix-pipeline reads CI logs and plans the fix BEFORE touching code.
/research spawns a research subagent across web + docs + codebase.
/interview is backwards -- the agent grills ME until the plan is sharp.

The killer is /learn.
After a hard session, distil what the agent learned the hard way
back into AGENTS.md. This is fix-the-factory in action.

TRANSITION: Context is the foundation. Now the second bucket -- feedback loops.
-->

---
transition: fade
---

<PartSlide
  part="3"
  title="Feedback Loops"
  subtitle="Backpressure: tests, types, lint"
/>

<!--
[scan room]

Bucket two. If an agent does not know when it broke something,
it will ship whatever compiles.
-->

---

# An agent with a failing test runs in a loop until it's green.

<v-click>

# Without tests, it ships whatever compiles.

</v-click>

<div v-click class="mt-12 grid grid-cols-3 gap-6">

<Card glow>
<div class="i-ph-test-tube-bold mb-3" style="color: #ff6bed; width: 28px; height: 28px" />
<div class="text-lg font-bold">Vitest</div>
<div class="text-xs op-70 mt-2">Fast. Watch mode. Browser mode. The agent's first signal.</div>
</Card>

<Card glow>
<div class="i-ph-shield-check-bold mb-3" style="color: #ff6bed; width: 28px; height: 28px" />
<div class="text-lg font-bold">Strict tsconfig</div>
<div class="text-xs op-70 mt-2">Types are an early failure. Catch the lie before the bug.</div>
</Card>

<Card glow>
<div class="i-ph-broom-bold mb-3" style="color: #ff6bed; width: 28px; height: 28px" />
<div class="text-lg font-bold">ESLint / oxlint</div>
<div class="text-xs op-70 mt-2">The agent's conscience for everything types miss.</div>
</Card>

</div>

<!--
This is the most important slide in the whole feedback section.

An agent with a failing test loops until it is green.
Without tests, it ships whatever compiles.

CLICK

CLICK -- Three layers. Vitest. Strict TS. Lint.
Each one is a failure signal the agent can act on.

The slower your tests, the slower the agent. Keep them fast.

TRANSITION: But test SHAPE matters more than test count.
-->

---

# Selectors vs page objects

<div class="text-center text-xs op-60 mb-3">Same test. Two styles. One survives a refactor.</div>

<div class="grid grid-cols-2 gap-4">

<div>

<div class="text-xs font-bold mb-2" style="color: rgba(255,255,255,0.6)">LEFT — Inline selectors</div>

```ts
test("applies discount", async () => {
  const input = page.getByRole("textbox", {
    name: "Enter discount code"
  })
  await input.fill("SAVE10")
  await page.getByRole("button", {
    name: "Apply"
  }).click()
  await expect(
    page.locator(".discount-banner.success")
  ).toBeVisible()
  await expect(
    page.locator("[data-testid='cart-total']")
  ).toHaveText("$45.00")
})
```

<div class="mt-2 text-xs" style="color: #ef4444">Designer renames a label → 12 tests break.</div>

</div>

<div>

<div class="text-xs font-bold mb-2" style="color: #ff6bed">RIGHT — Page object</div>

```ts
// pages/CartPage.ts
export class CartPage {
  async applyDiscount(code: string) { ... }
  async discountStatus() { ... }
  async total() { ... }
}

// tests/cart-discount.spec.ts
test("applies discount", async () => {
  const cart = new CartPage(page)
  await cart.goto()
  await cart.applyDiscount("SAVE10")
  expect(await cart.discountStatus())
    .toBe("applied")
  expect(await cart.total()).toBe("$45.00")
})
```

<div class="mt-2 text-xs" style="color: #ff6bed">Update CartPage.ts once. All 12 tests stay green.</div>

</div>

</div>

<div v-click class="mt-6 text-center text-lg">
  The agent doesn't need to understand your DOM.<br/>
  <strong style="color: #ff6bed">It needs an API. The page object IS that API.</strong>
</div>

<!--
Both tests do the same thing.

LEFT: hardcoded selectors, accessible names, css classes.
Two weeks later a designer renames a label -- 12 tests break.
The agent has to update every test.

RIGHT: page object. The test reads like English.
The DOM changed? Update CartPage.ts ONCE.

CLICK -- The agent does not need to understand your DOM.
It needs an API. The page object IS that API.

TRANSITION: Tests are just one layer. There are 15.
-->

---

# 15 layers of feedback

<div class="text-center text-sm op-60 mb-4">Tests are layer 3 of 15. Every layer is a signal the agent can chase.</div>

<div class="grid grid-cols-[1fr_auto] gap-8 items-center">

<div>
  <img src="/quality-pipeline-layers.png" class="rounded-lg shadow-2xl" />
</div>

<div class="flex flex-col items-center gap-3">
  <img src="/qr-quality-pipeline.png" class="w-44 h-44 bg-white p-2 rounded-lg" />
  <div class="text-xs op-70 text-center max-w-44">
    Full breakdown<br/>
    <span style="color: #ff6bed">alexop.dev/posts/<br/>modern-frontend-<br/>quality-pipeline</span>
  </div>
</div>

</div>

<!--
Tests are layer 3 of 15.

Type safety, lint, unit, component, API mocking, contract, E2E,
a11y, visual regression, performance, dead code, i18n drift,
preview deploys, AI code review, observability.

Every one is a signal the agent can chase.
The cheap ones at the center run on every save.
The expensive ones at the edge run in CI or prod.

I wrote up the full stack on my blog -- scan the QR for the deep dive.

TRANSITION: All those layers are SIGNALS. You still need a GATE.
-->

---

# The commit-time gate: Lefthook

<div class="text-center text-sm op-60 mb-4">15 layers are signals. <strong>Lefthook is the gate.</strong></div>

```yaml
# lefthook.yml
pre-commit:
  parallel: true
  jobs:
    - run: pnpm oxlint
    - run: pnpm oxfmt --check
    - run: pnpm vue-tsc --build
    - run: pnpm vitest related --run {staged_files}

commit-msg:
  jobs:
    - run: |
        grep -qE '^(feat|fix|chore|refactor|test|docs)(\(.+\))?!?: .+' {1} \
          || (echo "Conventional commit required"; exit 1)
```

<div class="mt-6 grid grid-cols-2 gap-6">

<Card glow>
<div class="text-xs op-60 mb-1">Why Lefthook, not Husky</div>
<div class="text-sm">Parallel jobs. YAML the agent can READ and edit. No shell-script soup.</div>
</Card>

<Card variant="muted">
<div class="text-xs op-60 mb-1">The one rule</div>
<div class="text-sm">No <code>--no-verify</code>. If a hook fails, <strong>fix the underlying issue.</strong></div>
</Card>

</div>

<!--
[pause]

15 layers are signals. Lefthook is the GATE.

Bad code doesn't reach main. Full stop.

Why Lefthook over Husky?
- Parallel jobs out of the box -- oxlint, oxfmt, vue-tsc, vitest related all run together.
- YAML is the format. The AGENT can read and edit lefthook.yml.
  It cannot fight a shell-script soup.

Mirror these same checks in .github/workflows/ci.yml so the gate
holds in CI too.

The one rule: no --no-verify escape hatches. If a hook fails, FIX IT.
The whole point of the gate is that it doesn't open.

TRANSITION: But there's a layer EVEN BEFORE commit -- inside the agent loop itself.
-->

---

# Hooks: guards inside the agent

<div class="text-center text-sm op-60 mb-4">Lefthook is the gate at commit time. <strong>Hooks are guards mid-loop.</strong></div>

<div class="grid grid-cols-2 gap-3">

<Card variant="muted">
<div class="text-xs font-bold mb-1" style="color: #ff6bed">PreToolUse(Bash)</div>
<div class="text-sm">Block destructive commands: <code>rm -rf</code>, <code>git push --force</code>, <code>git reset --hard</code>.</div>
</Card>

<Card variant="muted">
<div class="text-xs font-bold mb-1" style="color: #ff6bed">PreToolUse(Bash)</div>
<div class="text-sm">Enforce <code>pnpm</code>. No npm/yarn slipping in.</div>
</Card>

<Card variant="muted">
<div class="text-xs font-bold mb-1" style="color: #ff6bed">PreToolUse(Edit | Write)</div>
<div class="text-sm">Protect generated files: <code>.nuxt/</code>, <code>components.d.ts</code>, <code>auto-imports.d.ts</code>.</div>
</Card>

<Card variant="muted">
<div class="text-xs font-bold mb-1" style="color: #ff6bed">PreToolUse(Read | Bash)</div>
<div class="text-sm">Block <code>.env</code> reads. Point the agent at <code>.env.example</code>.</div>
</Card>

<Card variant="muted">
<div class="text-xs font-bold mb-1" style="color: #ff6bed">SessionStart</div>
<div class="text-sm">Orient: print project type, branch, run <code>nuxi prepare</code> if types are stale.</div>
</Card>

<Card glow>
<div class="text-xs font-bold mb-1" style="color: #ff6bed">PostToolUse(Edit | Write)</div>
<div class="text-sm"><strong>The one carve-out</strong>: <code>oxfmt</code>. Normalization, not feedback.</div>
</Card>

</div>

<div v-click class="mt-6 text-center text-base op-80 max-w-3xl mx-auto">
  Don't put typecheck / lint / tests in <code>PostToolUse</code>. <span style="color: #ff6bed">That's what Lefthook is for.</span>
</div>

<!--
Lefthook is the gate at commit time.
Hooks are the GUARDS mid-loop -- inside Claude Code itself.

Five guards prevent disaster:

1. Block destructive bash -- rm -rf, force push, hard reset. Exit code 2 = blocked.
2. Enforce pnpm. No npm/yarn slipping into the lockfile.
3. Protect generated files. The agent should NEVER hand-edit .nuxt/ or components.d.ts.
4. Block .env reads -- including the bash escape hatches (cat, head, jq .env).
   Point it at .env.example instead.
5. SessionStart -- orient the agent. What project? What branch? Run nuxi prepare if stale.

And ONE carve-out: oxfmt on PostToolUse(Edit|Write).
Why? Because oxfmt is NORMALIZATION not feedback.
Prettier is too slow -- 200-500ms per edit. Oxfmt is milliseconds.

CLICK -- The trap: don't put typecheck/lint/tests in PostToolUse.
Drift. Intermediate broken state. Context cost. Slow signals.
That's what Lefthook is for. Hooks are guards. Lefthook is the gate.

Codex got hooks in May 2026. Cursor next. This is the new normal.

TRANSITION: Last bucket -- discoverability. Can the agent find the right code?
-->

---
transition: fade
---

<PartSlide
  part="4"
  title="Discoverability"
  subtitle="One folder = one feature"
/>

<!--
[scan room]

Bucket three. The folder structure is the API the agent uses to read your code.
Once context is in place, the agent can help you carve the structure too.
-->

---

# One folder = one feature

<div class="grid grid-cols-2 gap-8 mt-4">

<div>

<div class="text-sm font-bold mb-2" style="color: #ff6bed">Monorepo with feature packages</div>

<FolderTree
  root
  title="Project Files"
  :structure="`apps/
  web/
packages/
  ui/
  features/
    cart/
    checkout/
    auth/
    catalog/`"
/>

</div>

<div class="flex flex-col justify-center gap-4">

<Card variant="muted">
<div class="text-sm op-80">Vue SFCs are already agent-friendly — one file = one concern.</div>
</Card>

<Card variant="muted">
<div class="text-sm op-80">Composables + Pinia stores give clean module seams.</div>
</Card>

<Card glow>
<div class="text-sm">The pnpm workspace makes those seams <strong style="color: #ff6bed">enforceable</strong>.</div>
</Card>

</div>

</div>

<!--
The big idea.

Vue is already friendly for agents at the file level --
one component, one file, one concern.

Where Vue projects go wrong is the FOLDER level.
A flat `components/` and `composables/` and `stores/`
hides the seams between features.

Put each feature in its own package. The workspace boundary
becomes a wall the agent can see.

TRANSITION: Let me show you what that wall does.
-->

---

# Same task, two structures

<div class="text-center text-sm op-60 mb-4">"Add a discount code to the cart" — watch the same agent work</div>

<div class="grid grid-cols-2 gap-6">

<div>

<div class="text-xs op-50 mb-2">LEFT — Flat structure</div>

<FolderTree
  root
  title="src/"
  :structure="`src/
  components/
    CartSummary.vue
    CartItem.vue
    DiscountBadge.vue
    Header.vue
    ProductCard.vue
  composables/
    useCart.ts
    useAuth.ts
    useCheckout.ts
  stores/
    cart.ts
    user.ts`"
/>

</div>

<div>

<div class="text-xs op-50 mb-2">RIGHT — Modular monolith</div>

<FolderTree
  root
  title="packages/features/"
  :structure="`packages/
  features/
    cart/
      components/
      composables/
      store.ts
      index.ts
    checkout/
    auth/
    catalog/`"
/>

</div>

</div>

<div class="mt-4 grid grid-cols-2 gap-6 text-xs">
  <div class="text-center op-60">cart logic is scattered across 3 folders</div>
  <div class="text-center" style="color: #ff6bed">cart logic is one folder. <strong>index.ts is the public API.</strong></div>
</div>

<!--
Same product. Same agent. Same task: add a discount code.

LEFT: cart, useCart, store.ts — three different folders.
What is shared with checkout? Who knows.

RIGHT: features/cart is a unit.
index.ts says what is public.
Anything not exported is private to the feature.

TRANSITION: Now the agent traces.
-->

---

# The agent traces

<div class="grid grid-cols-2 gap-4 mt-2">

<div>

<div class="text-xs font-bold mb-2" style="color: rgba(255,255,255,0.6)">LEFT — flat structure</div>

```text
Grep("cart")             → 47 hits, 9 features
Read CartSummary.vue     → not the right one
Read CartItem.vue        → close, state elsewhere
Grep("useCart")          → 23 hits, half are tests
Read useCart.ts          → found state
Read stores/cart.ts      → found mutations
Edit CartSummary.vue
Edit useCart.ts
Edit stores/cart.ts
Bash: vitest             → 90s, 2 fails
Read checkout.spec.ts    → coupling discovered
Edit useCheckout.ts      → fix coupling
Bash: vitest             → 90s, green
```

<div class="mt-3 text-center">
  <span class="text-lg font-bold" style="color: #ef4444">12 tool calls · ~3 min</span>
  <div class="text-xs op-60 mt-1">+ one accidental coupling</div>
</div>

</div>

<div>

<div class="text-xs font-bold mb-2" style="color: #ff6bed">RIGHT — modular monolith</div>

```text
Glob("features/cart/**")   → 8 files
Read features/cart/index.ts
Read features/cart/store.ts
Read features/cart/
     components/
     CartSummary.vue
Edit store.ts
Edit CartSummary.vue
Bash: vitest features/cart → 4s, green
```

<div class="mt-3 text-center">
  <span class="text-lg font-bold" style="color: #ff6bed">6 tool calls · ~30 sec</span>
  <div class="text-xs op-60 mt-1">blast radius = one folder</div>
</div>

</div>

</div>

<div v-click class="mt-6 text-center text-lg">
  You didn't make the agent <em>smarter</em>.<br/>
  <strong style="color: #ff6bed">You made the codebase legible.</strong>
</div>

<!--
Walk through LEFT slowly. Let the audience feel the waste.

47 grep hits. The agent reads three files before finding state.
Tests take 90 seconds. Two unrelated tests fail because cart and
checkout share a composable that nobody documented.

Click to RIGHT.

Same task. Six tool calls. Vitest in 4 seconds because we scope it.

CLICK -- The point: you didn't make the agent smarter.
You made the codebase LEGIBLE.

TRANSITION: That's the three buckets. Zoom out -- where is this all heading?
-->

---
transition: fade
---

<PartSlide
  title="Where this is heading"
  subtitle="The role merge"
/>

<!--
[breathe] [scan room]

Last act. The bigger picture.
-->

---
layout: statement
transition: fade-out
---

# AFK coding is already here.

<v-click>

# You write the spec. The agent ships the PR. You review.

</v-click>

<!--
[pause]

AFK -- away from keyboard.

You write a spec. Kick off an agent. Walk away.
Come back to a draft PR.
The agent ran tests, hit a failure, fixed itself, ran again,
opened the PR with a summary. You review.

CLICK

The work is no longer "me typing."
The work is "me deciding what should exist,
and reviewing what came back."

TRANSITION: Let me show you what that looks like in MY week.
-->

---

# What my week actually looks like

<div class="text-center text-sm op-60 mb-4">I haven't typed code into a feature in months. This is the loop.</div>

<div class="space-y-3">

<Card variant="muted">
  <div class="flex items-center gap-4">
    <div class="text-2xl font-bold op-50">01</div>
    <div>
      <div class="text-base font-bold">Paste the ticket into the feature branch</div>
      <div class="text-xs op-60">The story, verbatim — not my summary.</div>
    </div>
  </div>
</Card>

<Card variant="muted">
  <div class="flex items-center gap-4">
    <div class="text-2xl font-bold op-50">02</div>
    <div>
      <div class="text-base font-bold">"Read the codebase. Ask me what's unclear."</div>
      <div class="text-xs op-60">Catches missing scope before any code moves.</div>
    </div>
  </div>
</Card>

<Card variant="muted">
  <div class="flex items-center gap-4">
    <div class="text-2xl font-bold op-50">03</div>
    <div>
      <div class="text-base font-bold">Break into vertical-slice sub-tasks · ship small PRs</div>
      <div class="text-xs op-60">Each slice is reviewable on its own.</div>
    </div>
  </div>
</Card>

<Card variant="muted">
  <div class="flex items-center gap-4">
    <div class="text-2xl font-bold op-50">04</div>
    <div>
      <div class="text-base font-bold">I review · Copilot reviews</div>
      <div class="text-xs op-60">Two sets of eyes on every PR. Mine, plus an automated reviewer.</div>
    </div>
  </div>
</Card>

<Card glow>
  <div class="flex items-center gap-4">
    <div class="text-2xl font-bold" style="color: #ff6bed">05</div>
    <div>
      <div class="text-base font-bold" style="color: #ff6bed">Refactor pass in a fresh context</div>
      <div class="text-xs op-70">No carryover bias from the implementation chat. Just: simplify.</div>
    </div>
  </div>
</Card>

</div>

<!--
This is concrete. Real. What my week actually looks like.

01 -- I paste the ticket TEXT into the branch. Verbatim.
The agent should see what business and devs agreed on,
not my paraphrase of it.

02 -- The most important step in the whole loop.
"Read the codebase. Ask me what's unclear."
Nine times out of ten the agent finds something we forgot.
An edge case nobody specced. A field nobody mapped.
This catches it BEFORE any code moves.

03 -- Vertical slices. Each one ships independently. Small PRs.

04 -- Two reviewers. Me, and an automated one -- Copilot or CodeRabbit.
Different eyes catch different things.

05 -- After it's green, a separate refactor pass in a FRESH context.
No memory of the implementation conversation. No "I built this so it must be good" bias.
Just: simplify this.

I am the engineering manager of one IC. The IC is the agent.

TRANSITION: But the most important thing in this loop is what I do
when the agent gets it WRONG.
-->

---
layout: statement
transition: fade-out
---

# Agent did it wrong?

<v-click>

# Fix the factory, not the PR.

</v-click>

<div v-click class="mt-12 max-w-3xl mx-auto">

<Card glow>
<div class="text-sm op-90">
A bug isn't a bug. It's a factory defect.<br/><br/>
Don't just patch the PR — <strong style="color: #ff6bed">add the ESLint rule</strong>, <strong style="color: #ff6bed">update AGENTS.md</strong>, <strong style="color: #ff6bed">tighten the slash command</strong>. So the same mistake can't ship next week.
</div>
</Card>

</div>

<!--
[pause]

Here is the part most people miss.

The agent ships a bug.
The instinct is: fix the bug, merge, move on.

CLICK -- The instinct is wrong. Fix the FACTORY.

CLICK -- A bug isn't a bug. It is a factory defect.

Add an ESLint rule that catches that whole class of mistake.
Update AGENTS.md so the convention is written down.
Tighten the slash command or the prompt if that is where it leaked.

The PR fix is one bug. The factory fix prevents the next hundred.

This is the same compounding loop as the three buckets earlier:
discoverability, feedback, context.
Every PR review teaches the factory.

The codebase gets smarter over time. You get more leverage every week.

TRANSITION: So if THIS is the loop -- what does the TEAM look like?
-->

---

# The software factory

<div class="text-sm op-60 text-center mb-6">Teams shrink. Roles merge. Agents do the handoffs.</div>

<div class="grid grid-cols-2 gap-6">

<Card variant="muted">
<div class="text-sm font-bold mb-3" style="color: rgba(255,255,255,0.7)">Old team — 12 people</div>
<ul class="text-xs space-y-1 op-70">
  <li>· Frontend, backend, QA, DevOps</li>
  <li>· Designer, BA, PO, EM</li>
  <li>· Handoffs everywhere</li>
  <li>· Specialists optimize their slice</li>
</ul>
</Card>

<Card glow>
<div class="text-sm font-bold mb-3" style="color: #ff6bed">New team — 5 + agents</div>
<ul class="text-xs space-y-1 op-70">
  <li>· 5 generalists, end-to-end</li>
  <li>· Agents do the handoffs</li>
  <li>· Everyone is a builder</li>
  <li>· Generalists optimize the <em>outcome</em></li>
</ul>
</Card>

</div>

<div v-click class="mt-8 text-center text-lg op-90">
  <strong style="color: #ff6bed">Designers ship Vue components.</strong> PMs prototype flows.<br/>
  BAs write the failing test that defines done.
</div>

<!--
12 to 5. Generalists with agents as their execution layer.

Old: each specialist optimizes their slice.
New: generalists optimize the OUTCOME.

CLICK

The simple coder role -- translating a Jira ticket into a script setup block --
that is the part that gets automated.

What is LEFT is the part developers used to complain they weren't paid to do:
understanding the business.

Designers ship Vue components. PMs prototype flows.
BAs write the failing test that defines done.

TRANSITION: Which means the dev role itself is merging.
-->

---

# The role merge

<div class="grid grid-cols-3 gap-4 mt-6">

<Card glow>
<div class="text-xs op-50 mb-2">BA's old job</div>
<div class="text-sm font-bold" style="color: #ff6bed">Know what the business needs</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-2">PO's old job</div>
<div class="text-sm font-bold" style="color: #ff6bed">Decide what to build next</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-2">Dev's new job</div>
<div class="text-sm font-bold" style="color: #ff6bed">Architect so an agent can build it</div>
</Card>

</div>

<div v-click class="mt-12 text-center text-2xl max-w-3xl mx-auto leading-snug">
  You're not losing your job to AI.<br/>
  <strong style="color: #ff6bed">You're absorbing two other jobs</strong> because AI made the typing free.
</div>

<!--
[slow down]

The developer who thrives now is the one who:
- Knows what the business actually needs (the BA's old job)
- Can decide what to build next (the PO's old job)
- Can architect the system so an agent can build it (the dev's new job)

CLICK -- This is the line:

You're not losing your job to AI.
You're absorbing two other jobs because AI made the typing free.

Frame this as opportunity. Not threat.
Vue devs who care about UX and product
are CLOSER to this than backend devs grinding on microservices.

TRANSITION: One slide. Do this Monday.
-->

---

# Do this Monday

<div class="space-y-4 mt-8">

<div v-click>
<Card glow>
<div class="flex items-center gap-4">
  <div class="text-3xl font-bold" style="color: #ff6bed">01</div>
  <div>
    <div class="text-lg font-bold">Write an AGENTS.md</div>
    <div class="text-sm op-70">Folder conventions. Naming. Design system. Test rules. One page is enough to start.</div>
  </div>
</div>
</Card>
</div>

<div v-click>
<Card glow>
<div class="flex items-center gap-4">
  <div class="text-3xl font-bold" style="color: #ff6bed">02</div>
  <div>
    <div class="text-lg font-bold">Add Vitest + one real test</div>
    <div class="text-sm op-70">Backpressure starts with one failing test the agent can chase.</div>
  </div>
</div>
</Card>
</div>

<div v-click>
<Card glow>
<div class="flex items-center gap-4">
  <div class="text-3xl font-bold" style="color: #ff6bed">03</div>
  <div>
    <div class="text-lg font-bold">Restructure into a pnpm workspace</div>
    <div class="text-sm op-70">Start with one feature module. Move the next when you touch it.</div>
  </div>
</div>
</Card>
</div>

</div>

<!--
The hierarchy.

CLICK -- If you do nothing else: write an AGENTS.md tomorrow.
One page. Folders, naming, design system, tests. Done.

CLICK -- If you do two things: add Vitest with one real test.
Give the agent a signal it can chase.

CLICK -- If you do three: restructure into a pnpm workspace.
Pull ONE feature out. The rest follows when you touch it.

TRANSITION: The closer.
-->

---
layout: statement
transition: fade-out
---

# Clean code is sexy again —

<v-click>

# because now it pays you back twice.

</v-click>

<v-click>

# Once when humans read it.

</v-click>

<v-click>

# And once when agents do.

</v-click>

<!--
[breathe] [look up]

The patterns weren't wrong before.
They're just non-optional now.

The cost of bad code used to be human friction.
Now it's your AI multiplier doesn't work.

CLICK

CLICK

CLICK

Mic drop. Q&A.
-->

---
layout: end
transition: fade
---

# Thank You!

<div class="text-lg op-80 mb-8">

**alexop.dev** · **@alexanderopalic**

</div>

<div class="grid grid-cols-2 gap-6 max-w-4xl mx-auto">

<Card glow class="flex items-center gap-4 !px-5 !py-4">
  <div class="i-ph-file-text-bold flex-shrink-0" style="color: #ff6bed; width: 56px; height: 56px" />
  <div class="text-left">
    <div class="text-lg font-bold" style="color: #ff6bed">AGENTS.md starter</div>
    <div class="text-xs op-60 mt-1.5">A minimal AGENTS.md template you can drop into any Vue project.</div>
    <div class="mt-2 flex items-center gap-2 text-xs op-40">
      <div class="i-ph-github-logo" />
      <span>alexop.dev/blog/agents-md</span>
    </div>
  </div>
</Card>

<Card variant="muted" class="flex items-center gap-4 !px-5 !py-4">
  <div class="i-ph-git-fork-bold flex-shrink-0" style="color: rgba(255,255,255,0.5); width: 56px; height: 56px" />
  <div class="text-left">
    <div class="text-lg font-bold">clone-repo skill</div>
    <div class="text-xs op-60 mt-1.5">Vendor any repo as a subtree and wire it into AGENTS.md.</div>
    <div class="mt-2 flex items-center gap-2 text-xs op-40">
      <div class="i-ph-github-logo" />
      <span>github.com/alexanderop/clone-repo</span>
    </div>
  </div>
</Card>

</div>

<!--
[breathe] [look up]

Thank you!

Two takeaways on the slide.

AGENTS.md starter -- a one-page template you can copy.
clone-repo skill -- vendor any reference repo in one command.

Come find me to chat. I want to hear what your AGENTS.md looks like.

[pause]
-->
