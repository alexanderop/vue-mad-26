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
layout: image
image: /madvue-2026.png
backgroundSize: contain
---

<PartSlide
  title="Clean Code Is Sexy Again"
  subtitle="Making Your Vue Project AI-Ready · Vue MAD 2026 · Alexander Opalic"
/>

---
layout: image
image: /five-levels.png
backgroundSize: contain
---

<div class="absolute bottom-4 right-6 text-xs op-50">
  Framing: Dan Shapiro · <em>The Five Levels: From Spicy Autocomplete to the Software Factory</em> · Jan 2026
</div>

<!--
Dan Shapiro framed this beautifully. Six levels, like driving automation.

L0 spicy autocomplete -- AI as a smarter Stack Overflow.
L1 coding intern -- writes boilerplate, you review every line.
L2 junior dev -- pair programmer, you trade off in real time.
L3 developer -- AI writes most of it, you are the verification bottleneck.
L4 senior dev -- runs unattended, you check the final result.
L5 software factory -- you manage goals, AI defines, ships, fixes.

The question for you: where are you actually sitting?

TRANSITION: For context, here's where I am -- and why.
-->

---

# Two weeks ago: Bun got rewritten in Rust

<div class="flex justify-center">
  <img src="/bun-rust-pr.png" class="max-h-80 rounded-lg shadow-lg" />
</div>

<!--
Exhibit A for why this talk is hard.

Bun -- one of the most-hyped JS runtimes -- rewritten from Zig to Rust.
1M lines. 10 days. By an agent.

Anthropic owns Bun now. Almost entirely Claude. Near-zero human review. 13k unsafe blocks.
Rust and Zig communities melted down. Reviewers were Claude. Claude flagged a follow-up PR as AI slop.

Triumph or disaster? I don't know yet.
What I know: this is the world we ship into. Major OSS rewritten in two weeks by a machine.
The pace is real. Not slowing down.

TRANSITION: Which brings us to the quote that sums up the shift.
-->

---

# And the creator defends it

<div class="flex justify-center">
  <img src="/bun-creator-defense.png" class="max-h-90 rounded-lg shadow-lg" />
</div>

<!--
Jarred Sumner, the creator of Bun, jumped in to defend the Rust port.

Smaller binaries: -5.5MB on macOS, -6.8MB on Linux, -3.8MB on Windows.

His response to the critics:
- The unsafe usage is a deliberate tradeoff -- a port intended to not change behavior. Strictly better than before. Miri in CI soon.
- The code style looks like Zig because it is intentional -- the team needs to feel at home in the codebase the agent shipped.

That last point is the one. The agent shipped code that humans still have to live with.

TRANSITION: Which brings us to the quote that sums up the shift.
-->

---
layout: quote
transition: fade
---

<QuoteCard author="Simon Willison" source="simonwillison.net, Jan 2026" highlight="everything else">
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

# Only if your project is built for AI and your devs know what they're doing.

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
transition: fade-out
---

<div class="h-full flex items-center justify-center">
  <img src="/why-ai-succeeds.png" class="max-h-full max-w-full rounded-lg shadow-lg" />
</div>

<!--
[hold the silence]

This is the question.
The rest of the talk is the answer.

TRANSITION: Quick intro -- then how we're going to answer that.
-->

---

# About me

<About />

<!--
Quick intro -- now that you know why you should care.

Alexander Opalic -- Vue 8+ years
Otto Payments -- e-commerce
Blog at alexop.dev -- mostly Vue and AI now

TRANSITION: Here is what we are going to do.
-->

---
layout: statement
transition: fade
---

# Quick show of hands

<div class="mt-12 text-3xl leading-relaxed op-90">

Who is driving with...

</div>

<div class="mt-8 text-2xl leading-loose">

- **Claude Code**
- **Codex**
- **Copilot**
- **Cursor**
- something else

</div>

<div class="mt-10 text-xl op-60">

Just so I know which harness you live in.

</div>

<!--
Quick check before we go in.

I want to know which harness you actually use day to day.
Claude Code -- Codex -- Copilot -- Cursor -- something else.

[count hands per option]

Reason I am asking: the patterns in this talk apply to all of them,
but the failure modes look different per harness.

TRANSITION: OK -- here is the plan.
-->

---

<PyramidOutline :items="[
  { title: 'What an Agent Actually Is', subtitle: 'A loop, not a magic box' },
  { title: 'Context', subtitle: 'Does it know why things exist?' },
  { title: 'Extending the Agent', subtitle: 'Skills and CLIs extend the agent’s reach' },
  { title: 'Feedback Loops', subtitle: 'Does it know when it is wrong?' },
  { title: 'Discoverability', subtitle: 'Can the agent find the right code?' },
  { title: 'Future', subtitle: 'The role merge' }
]" />

<!--
Six beats.

Start with what an agent really is.
Then three buckets you can act on Monday -- Context, Feedback, Discoverability.
Extending the agent layers on top.
Close with where this is heading.

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

<div class="flex justify-center items-center h-full">

<img src="/how-an-ai-agent-works.png" alt="How an AI agent works" class="max-h-[85vh] w-auto" />

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
transition: fade-out
---

<div class="h-full flex items-center justify-center">
  <img src="/nanocode-repo.png" class="max-h-full max-w-full rounded-lg shadow-lg" />
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

TRANSITION: First, the official framing -- then three buckets.
-->

---
layout: quote
transition: fade
---

<QuoteCard author="Anthropic engineering team" highlight="more than the model alone">
  The ecosystem built around the model — the harness — determines how Claude Code performs more than the model alone.
</QuoteCard>

<div class="absolute bottom-4 right-6 text-xs op-50">
  Source: <em>How Claude Code works in large codebases</em> · claude.com/blog · May 2026
</div>

<!--
[pause]

That is the Anthropic engineering team. Published this month.
Not a hype tweet -- the team that ships Claude Code.

The HARNESS matters more than the MODEL.
Extension points you actually control -- CLAUDE.md, hooks, skills, plugins.
That is the surface area worth your time.

Stop optimizing prompts. Start configuring the room.

The three buckets coming up are exactly that work --
my organizing frame for the same layers.

TRANSITION: Three things the agent needs from your codebase.
-->

---
transition: fade-out
---

<div class="h-full flex items-center justify-center">
  <img src="/three-buckets.png" class="max-h-full max-w-full rounded-lg shadow-lg" />
</div>

<!--
[reveal beat]

Three buckets. Context, Feedback, Discoverability.
The rest of the talk lives inside these three.
-->

---

# The <span style="background: linear-gradient(90deg, #a855f7, #3b82f6, #14b8a6); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">three</span> buckets

<div class="text-center text-sm op-60 -mt-2 mb-6">A practical framework for building reliable, maintainable agents.</div>

<div class="grid grid-cols-3 gap-6">

<BucketCard
  number="01"
  color="purple"
  title="Context"
  question="Does the agent know why things exist?"
  footerText="Docs, AGENTS.md, ADRs, the rules of your house."
  topIcon="document"
  footerIcon="document"
/>

<BucketCard
  number="02"
  color="blue"
  title="Feedback loops"
  question="Does the agent know when it is wrong?"
  footerText="Tests, linting, types, your backpressure."
  topIcon="chat"
  footerIcon="refresh"
/>

<BucketCard
  number="03"
  color="teal"
  title="Discoverability"
  question="Can the agent find the right code?"
  footerText="Modular monolith, monorepo structure, naming."
  topIcon="search"
  footerIcon="sitemap"
/>

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
layout: two-cols-header
---

# AGENTS.md — same file, two philosophies

::left::

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

::right::

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

<div v-click class="absolute bottom-4 left-0 right-0 text-center text-lg">
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

TRANSITION: And the same idea scales to the filesystem.
-->

---

# AGENTS.md is hierarchical

<div class="text-center text-sm op-60 mb-4">Root for the big picture. Per-feature files for local gotchas. <strong>Claude walks the tree.</strong></div>

<div class="grid grid-cols-2 gap-4">

<div>

<div class="text-xs font-bold mb-2" style="color: #ff6bed">Root — <code>AGENTS.md</code></div>

```md
# Project
Run `pnpm lint && pnpm typecheck`.

## Stack
Vue 3, Pinia, Vitest, Vite

## Structure
- `src/features/*` — feature-sliced
- `src/lib/` — shared layers

## Further reading
- `docs/testing-strategy.md`
- `docs/data-model.md`
```

</div>

<div>

<div class="text-xs font-bold mb-2" style="color: #ff6bed">Feature — <code>features/workout/AGENTS.md</code></div>

```md
# Workout feature

Active state lives in `useWorkoutMode`
— NOT in the Pinia store.

## Gotchas
- Use `usePersistedRestTimer()` —
  never read `restTimer.value` raw.
- New components → `./components/`.
- No imports from `../timers/`.
```

</div>

</div>

<div v-click class="mt-6 max-w-4xl mx-auto">

<Callout type="info">
Editing <code>features/workout/...</code>? Claude loads <strong>root + workout/AGENTS.md</strong>. <code>timers/AGENTS.md</code> never enters context. Progressive disclosure — built into the filesystem.
</Callout>

</div>

<div class="absolute bottom-3 right-6 text-xs op-50">
  Pattern: Anthropic, <em>How Claude Code works in large codebases</em> · claude.com/blog
</div>

<!--
[breathe]

The Bad/Good slide showed ONE AGENTS.md. The real strategy is HIERARCHICAL.

Anthropic published this pattern this month -- the official playbook
for large codebases. Root file for the big picture, subdirectory files
for local conventions.

Root AGENTS.md = stack, tooling, structure. Pointers only.
Each feature/ gets its OWN AGENTS.md = local gotchas, store shape, rules.

When the agent edits features/workout/something.vue, it walks UP the tree:
- loads root AGENTS.md
- loads features/workout/AGENTS.md
- ignores timers, exercises, settings.

CLICK -- Progressive disclosure baked into the filesystem.
The folder boundary that contains the CODE also contains its DOCS.

This pairs perfectly with feature-sliced architecture --
we'll see the feature folders in the Discoverability section.

TRANSITION: But the harness already has half of this built in.
-->

---
layout: default
---

# Every harness ships with "memory" — but it's local

<div class="text-center text-sm op-60 mb-6">Claude Code, Cursor, Codex — they all carry context between sessions. <strong>On your machine.</strong></div>

<div class="grid grid-cols-2 gap-6">

<Card glow>
<div class="text-xs op-50 mb-2">You write it</div>
<div class="text-base font-bold mb-2" style="color: #ff6bed"><code>CLAUDE.md</code></div>
<div class="text-xs op-80">Project-level instructions. Loaded every session.</div>
<div class="mt-2 text-xs op-50">Lives in the repo. Already shared. ✅</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-2">Claude writes it</div>
<div class="text-base font-bold mb-2" style="color: #ff6bed">Auto-memory</div>
<div class="text-xs op-80">Claude accumulates corrections, preferences, gotchas.</div>
<div class="mt-2 text-xs op-50"><code>~/.claude/projects/&lt;proj&gt;/memory/</code> — only on your laptop. ❌</div>
</Card>

</div>

<div v-click class="mt-8 max-w-3xl mx-auto">
  <div class="text-center text-base mb-3">
    Your teammate doesn't see it. The cloud agent doesn't see it. The next contributor starts from zero.
  </div>
  <div class="text-center text-lg">
    <strong style="color: #ff6bed">Memory belongs in the repo</strong> — not in <code>~/.claude/</code>.
  </div>
</div>

<div v-click class="mt-4 max-w-3xl mx-auto">
  <div class="text-center text-xs op-60">
    Same rule for exclusions: commit <code>permissions.deny</code> in <code>.claude/settings.json</code> so <code>dist/</code>, <code>.nuxt/</code>, generated <code>*.d.ts</code> stay out of context — for everyone, not just you. <span class="op-50">(Anthropic, <em>How Claude Code works in large codebases</em>.)</span>
  </div>
</div>

<!--
Every harness has this. Claude Code calls it Memory.
Cursor calls them Memories. Codex has its own variant.

Two halves -- shown right here:

LEFT -- CLAUDE.md. The instructions YOU write. Lives in the repo.
Every teammate gets it. Every cloud agent gets it. This part works.

RIGHT -- auto-memory. The corrections and preferences Claude
accumulates *itself*. Read the Claude docs -- it's a real feature.
The path is right there: tilde slash dot-claude slash projects.

That second half is the problem.

CLICK

Your teammate spins up the repo -- starts from zero.
The AFK agent in the cloud -- starts from zero.
You join a new laptop -- start from zero.

The intelligence is real. It's just locked to one machine.

Memory belongs in the repo. Same as CLAUDE.md.
And that is exactly what the next slide does.

TRANSITION: brainmaxxing commits the missing half.
-->

---

# Don't write it yourself — copy `brainmaxxing`

<div class="text-center text-sm op-60 mb-4"><code>github.com/poteto/brainmaxxing</code> — persistent memory + skills + hooks for Claude Code.</div>

<div class="flex justify-center mb-6">
  <img src="/brainmaxxing-repo.png" class="max-h-40 rounded-lg shadow-lg" />
</div>

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

TRANSITION: But the cards are not the magic. The skills are.
The six skills are what keep `brain/` alive.
-->

---
layout: default
---

# Six skills that keep `brain/` alive

<div class="text-center text-sm op-60 mb-5">Each skill reads the vault, writes back to it, or sharpens what's there.</div>

<div class="grid grid-cols-3 gap-3">

<Card glow>
<div class="text-xs op-50 mb-1"><code>/plan</code></div>
<div class="text-base font-bold mb-1" style="color: #ff6bed">Plan</div>
<div class="text-xs op-80">Phased plan written to <code>brain/plans/</code>. Planning only — no code.</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-1"><code>/review</code></div>
<div class="text-base font-bold mb-1" style="color: #ff6bed">Review</div>
<div class="text-xs op-80">Critique a PR or plan against <code>brain/principles/</code>. No edits.</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-1"><code>/reflect</code></div>
<div class="text-base font-bold mb-1" style="color: #ff6bed">Reflect</div>
<div class="text-xs op-80">Distil this session's mistakes &amp; learnings back into <code>brain/</code>.</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-1"><code>/meditate</code></div>
<div class="text-base font-bold mb-1" style="color: #ff6bed">Meditate</div>
<div class="text-xs op-80">Audit the vault. Prune stale notes. Find cross-cutting principles.</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-1"><code>/ruminate</code></div>
<div class="text-base font-bold mb-1" style="color: #ff6bed">Ruminate</div>
<div class="text-xs op-80">Mine past conversations for patterns that never got written down.</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-1"><code>/brain</code></div>
<div class="text-base font-bold mb-1" style="color: #ff6bed">Brain</div>
<div class="text-xs op-80">Direct read/write of vault files. The primitive the others build on.</div>
</Card>

</div>

<div v-click class="mt-8">
  <div class="text-center text-xs op-60 mb-3">The loop that compounds</div>
  <div class="flex items-center justify-center gap-2 text-sm flex-wrap">
    <code style="color: #ff6bed">/plan</code>
    <span class="op-40">→</span>
    <span class="op-80">code</span>
    <span class="op-40">→</span>
    <code style="color: #ff6bed">/review</code>
    <span class="op-40">→</span>
    <code style="color: #ff6bed">/reflect</code>
    <span class="op-40 mx-2">·····  weekly  ·····</span>
    <code style="color: #ff6bed">/meditate</code>
    <span class="op-40">+</span>
    <code style="color: #ff6bed">/ruminate</code>
  </div>
  <div class="text-center text-xs op-50 mt-3">Every loop ends with the vault sharper than it started.</div>
</div>

<!--
The cards on the previous slide were the boxes. These are the verbs.
Six skills, and each one either reads brain/, writes to brain/, or
cleans brain/. That is the whole game.

Per task:

/plan -- before I touch code on anything bigger than a one-file fix.
It reads brain/principles/, then writes a phased plan to brain/plans/.
Planning only. The plan is the deliverable.

Code. The agent now has a plan grounded in *my* principles, not
generic advice from training data.

/review -- after the code is written. Loads the same principles
fresh, critiques the diff against them. No edits, just the review.

/reflect -- end of session. Did I correct the agent? Did I learn
something new about the codebase? /reflect distils it into brain/
so next session starts ahead of where this one ended.

CLICK

Periodically -- maybe weekly:

/meditate audits the vault. Prunes stale notes. Asks "is this still
true?" of every entry. Cleans the room.

/ruminate goes the other direction -- mines old Claude conversations
for patterns that never made it into brain/. Recovers lost knowledge.

That is the compounding piece. Every loop, brain/ gets a little
sharper. Next session, the agent starts from there.

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

# What `brain/` actually looks like

<div class="text-center text-sm op-60 mb-6">One folder. One index. The <code>SessionStart</code> hook injects <code>index.md</code> — the agent follows wikilinks only when relevant.</div>

<div class="grid grid-cols-2 gap-6">

<Card variant="muted">
<div class="text-xs op-60 mb-2">The vault on disk</div>

```text
brain/
├── codebase/
│   ├── custom-components.md
│   ├── slide-gotchas.md
│   ├── theme-system.md
│   ├── testing-strategy.md
│   └── …
├── plans/
│   ├── preparser-extensions.md
│   └── roadmap.md
├── principles/
│   ├── guard-the-context-window.md
│   ├── fix-root-causes.md
│   ├── subtract-before-you-add.md
│   └── …
├── codebase.md
└── index.md
```

</Card>

<Card glow>
<div class="text-xs op-60 mb-2"><code>index.md</code> — the only file always in context</div>

```md
# Brain

## Codebase
- [[codebase]]
- [[codebase/theme-system]]
- [[codebase/slide-gotchas]]
- [[codebase/testing-strategy]]

## Plans
- [[plans/roadmap]]
- [[plans/preparser-extensions]]

## Principles
- [[principles/guard-the-context-window]]
- [[principles/fix-root-causes]]
- [[principles/subtract-before-you-add]]
- [[principles/prove-it-works]]
```

</Card>

</div>

<div v-click class="mt-6 text-center text-base op-90">
  Agent reads <code>index.md</code> first → <strong style="color: #ff6bed">only opens the wikilink it needs.</strong> Whole vault available, almost nothing loaded.
</div>

<!--
This is what the strategy looks like on disk.

LEFT -- one folder. brain/.
codebase/ -- what THIS repo actually does. Theme system, gotchas, testing.
plans/ -- what we are working towards.
principles/ -- the 16 from the last slide.

RIGHT -- one file. index.md.
It is just a list of wikilinks. No content inlined.

The SessionStart hook cats index.md into every conversation.
The agent sees the MAP, not the territory.
When it needs theme details, it follows [[codebase/theme-system]].
When it does not, that file never enters the context window.

CLICK -- whole vault available. Almost nothing loaded.
That is guard-the-context-window in practice.

TRANSITION: But there is one trick that is even bigger.
-->

---
transition: fade-out
---

# Want VueUse-style composables?

<v-click>

# Give the agent VueUse.

</v-click>

<div v-click class="mt-12 max-w-3xl mx-auto">

<QuoteCard author="Michael Arnaldi" highlight="setting up repositories">
  Most of my time as a programmer is now spent setting up repositories so that coding agents can act well inside them.
</QuoteCard>

</div>

<!--
[pause]

Hot take.

Agents are post-trained on READING CODE.
Not reading prose docs.
Stale docs in their training data are noise.
Real source in your tree is signal.

CLICK -- If you want the agent to write like VueUse,
let it READ VueUse.

CLICK -- Michael Arnaldi nails the shift:
"Setting up repositories so that coding agents can act well inside them."
That is the job now. Programming is configuring the room the agent works in.

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

<!--
One command. Vendors VueUse into your repo as a squashed subtree.

Then one line in AGENTS.md: "Mirror these patterns."

That is it.

CLICK

Why a subtree, not a submodule? No clone-time pain.
No "did you forget to init"? Just files.

Result -- the agent's pattern matching is now anchored on real code.
Pattern matching beats prompting.

CLICK -- Pro tip. Same trick works for STEALING FEEDBACK LOOPS.
Clone a repo you admire -- npmx.dev is a great Nuxt example.
Ask the agent "how do they test their Nuxt project?"
Copy the approach into your repo. Pattern matching beats reading docs.

I packaged this as a Claude Code skill: clone-repo.
Vendors any repo, wires it into AGENTS.md, done.

TRANSITION: One more layer to context -- extending the agent itself.
-->

---
transition: fade
---

<PartSlide
  part="3"
  title="Extending the Agent"
  subtitle="Skills wrap the CLIs you already use"
/>

<!--
[scan room]

Bucket three. Once context is solid, you can extend the agent.
Skills are markdown recipes that wrap the CLIs you already run by hand.

The warning -- if the foundation is clean, these multiply leverage.
If the foundation is messy, they multiply chaos.
-->

---

# What is an Agent Skill?

<div class="text-center text-sm op-60 mb-5">An open standard: a folder with a <code>SKILL.md</code> file. Metadata + instructions the agent loads <strong>only when relevant</strong>.</div>

<div class="grid grid-cols-2 gap-6 max-w-5xl mx-auto">

<div>

```text
.claude/skills/        # or .agents/skills/
└── my-skill/
    ├── SKILL.md       # name + description + steps
    ├── scripts/       # optional: code to run
    ├── references/    # optional: deeper docs
    └── assets/        # optional: templates
```

```yaml
---
name: debug-prod
description: Tail CloudWatch logs and
  correlate with the file being edited.
  Use when prod is broken.
---
```

</div>

<div class="text-sm op-80 leading-relaxed">

<div class="text-base font-bold mb-3" style="color: #ff6bed">Progressive disclosure — 3 stages</div>

<div class="mb-3"><strong style="color: #ff6bed">1. Discovery.</strong> At startup, the agent reads only <code>name</code> + <code>description</code> (~100 tokens each). It now knows the skill exists.</div>

<div class="mb-3"><strong style="color: #ff6bed">2. Activation.</strong> When your task matches the description, the full <code>SKILL.md</code> body loads into context.</div>

<div class="mb-3"><strong style="color: #ff6bed">3. Execution.</strong> Scripts, references, and assets load only when the steps call for them.</div>

<div class="text-xs op-60 mt-4">Open format originally by Anthropic — now supported by Claude Code, Cursor, Codex, Copilot, Gemini CLI, Goose, and ~30 others.</div>

</div>

</div>

<!--
Before the concrete examples -- what IS a skill, really.

A skill is just a folder with a SKILL.md file. YAML frontmatter on top
(name + description), markdown instructions below. That's the whole spec.

The magic is progressive disclosure. The agent doesn't read every skill
at startup -- that would blow up context. It reads only the name and
description -- maybe 100 tokens each. So you can have 50 skills loaded
and pay almost nothing for the ones you don't use.

When your prompt matches a description, THEN the full body loads.
When the body says "run scripts/extract.py", THAT loads.
Pay-as-you-go context.

And it's an open standard. The same SKILL.md works in Claude Code,
Cursor, Codex, Copilot -- about thirty agents now. Write once, runs
everywhere.

TRANSITION: So what does that look like in practice? Here are the ones
I actually use every day.
-->

---

# Skills: a markdown file the agent reads on demand

<div class="text-center text-sm op-60 mb-4">A skill is a <code>.md</code> file in <code>.claude/skills/</code> with a trigger phrase. Type the phrase — the agent loads the recipe.</div>

<div class="grid grid-cols-2 gap-3">

<Card variant="muted">
<div class="font-mono text-sm font-bold" style="color: #ff6bed">/push</div>
<div class="text-xs op-70 mt-1">Commit staged changes with a real message and push.</div>
</Card>

<Card variant="muted">
<div class="font-mono text-sm font-bold" style="color: #ff6bed">/pr</div>
<div class="text-xs op-70 mt-1">Open a PR with summary + test plan, derived from the diff.</div>
</Card>

<Card glow>
<div class="font-mono text-sm font-bold" style="color: #ff6bed">/check</div>
<div class="text-xs op-70 mt-1"><strong>Vue + a11y + perf reviewers in parallel</strong>, on every diff.</div>
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

<div v-click class="mt-6 text-center text-xs op-60 max-w-3xl mx-auto">
  Skills can be <strong style="color: #ff6bed">path-scoped</strong> — drop one in <code>features/workout/.claude/skills/</code> and it only triggers when the agent works inside <code>workout/</code>. <span class="op-50">(Pattern: Anthropic, <em>How Claude Code works in large codebases</em>.)</span>
</div>

<!--
A skill is just a markdown file in .claude/skills/.
You type the trigger phrase. The agent loads the recipe.

/push and /pr -- my two most-used. Remove all friction from shipping.
/check -- the killer for Vue work. Vue patterns + a11y + perf + tests.
   All in parallel. Every diff. Before I look at it.
/fix-pipeline -- reads CI logs and plans the fix BEFORE touching code.
/review-coderabbit -- triage CodeRabbit comments, only fix the valid ones.
/research -- subagent across web + docs + codebase.
/interview -- the agent grills ME until the plan is sharp.

The killer is /learn.
After a hard session, distil what the agent learned the hard way
back into AGENTS.md. Fix-the-factory in action.

TRANSITION: But shipped skills are just the start. The real power is writing your OWN.
-->

---

# Write your own: wrap the CLI you already use

<div class="text-center text-sm op-60 mb-6">A skill is just a recipe. If you can run it locally, the agent can too.</div>

<div class="grid grid-cols-2 gap-6 max-w-5xl mx-auto">

<div>

```md
---
description: Debug prod with CloudWatch logs
trigger: /debug-prod
---

When the user types /debug-prod <feature>:

1. Run `aws logs tail /aws/lambda/<fn> --since 30m`
2. Grep for ERROR / WARN around the timestamp
3. Cross-reference with the Vue component
   the user is editing
4. Propose a fix as a diff
```

</div>

<div>

<div class="text-base font-bold mb-3" style="color: #ff6bed">The pattern</div>
<div class="text-sm op-80 leading-relaxed">
You already know <code>aws</code>, <code>gh</code>, <code>kubectl</code>.<br/>
For UI testing: <code>agent-browser</code> — a CLI that drives a real browser, captures screenshots and console.<br/><br/>
Write a 10-line skill that wraps the flow you do by hand. The agent runs the same commands — and now it can read the output, correlate, and propose a fix.
</div>

<div v-click class="mt-6">

<Callout type="info">
<strong>No new infra.</strong> Just markdown + the CLIs already on your laptop.
</Callout>

</div>

<div class="mt-4 text-xs op-60">
QA-as-an-agent reference: <code>github.com/alexanderop/explore-qa</code>
</div>

</div>

</div>

<!--
This is the unlock.

You don't need a fancy plugin.

If you can run "aws logs tail" in your terminal,
write a 10-line skill that runs it for you.
The agent executes the same command, reads the output, correlates with the code.

Same pattern for kubectl, gh, terraform, docker, anything you already use.

For UI testing -- agent-browser is the CLI I reach for.
Full reference repo: github.com/alexanderop/explore-qa.
Clone it, see how QA-as-an-agent actually works.

CLICK -- the callout. No new infra. Just markdown.

TRANSITION: And before you write your own from scratch -- somebody has probably already shipped it.
-->

---

# Before you write one — browse <code style="color: #ff6bed">skills.sh</code>

<div class="text-center text-sm op-60 mb-5">The open agent-skills leaderboard. Search, copy, adapt. <code>npx skills update</code> to install.</div>

<div class="grid grid-cols-2 gap-6 max-w-5xl mx-auto">

<div>

```text
SKILLS LEADERBOARD          INSTALLS
─────────────────────────────────────
1  find-skills              1.6M
   vercel-labs/skills

2  frontend-design          429.1K
   anthropics/skills

3  vercel-react-            409.3K
   best-practices
   vercel-labs/agent-skills

4  web-design-guidelines    328.5K
   vercel-labs/agent-skills

5  microsoft-foundry        328.0K
   microsoft/azure-skills
```

</div>

<div class="text-sm op-80 leading-relaxed">

<div class="text-base font-bold mb-3" style="color: #ff6bed">Why browse first</div>

<div class="mb-3"><strong>Vendors already publish skills.</strong> Vercel, Anthropic, Microsoft — they ship the recipes for their own products. <code>vercel-react-best-practices</code>, <code>frontend-design</code>, Azure deploy flows.</div>

<div class="mb-3"><strong>Steal the structure.</strong> Even if you don't install one, open it on GitHub and copy the YAML frontmatter + step format into your own skill.</div>

<div class="mb-3"><strong>Same format, any agent.</strong> Skills written for one tool run in the others — the leaderboard is cross-product by design.</div>

<div v-click class="mt-5">

<Callout type="info">
<strong>Don't reinvent.</strong> Browse <code>skills.sh</code> → copy what fits → adapt the rest.
</Callout>

</div>

</div>

</div>

<!--
Before you write a skill from scratch -- check skills.sh.

It's the open leaderboard. 400,000+ skills.
And the top of the list is not random hobbyists -- it's the vendors.
Vercel publishing their own React best-practices skill.
Anthropic publishing frontend-design. Microsoft publishing Azure deploy flows.

These are the recipes the platform owners THEMSELVES want you running.

Even if you don't install one -- open it on GitHub.
Look at the YAML frontmatter, look at how they structure the steps.
That's free training data for writing your own.

And because skills are an open standard -- the same skill runs in
Claude Code, Cursor, Codex, whatever you use.

CLICK -- callout. Don't reinvent. Browse, copy, adapt.

TRANSITION: OK. Context is the foundation. Now the second bucket -- feedback loops.
-->

---
transition: fade
---

<PartSlide
  part="4"
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

<div v-click class="mt-12 text-center text-lg op-80">
Every red check is a signal the agent can chase.<br/>
<span style="color: #ff6bed">The faster the signal, the faster the loop.</span>
</div>

<!--
This is the most important slide in the whole feedback section.

An agent with a failing test loops until it is green.
Without tests, it ships whatever compiles.

CLICK -- Every red check is a signal. Faster signal, faster loop.

The slower your tests, the slower the agent. Keep them fast.

TRANSITION: Let's walk the first 5 layers. Modern frontend tooling.
-->

---

# Layer 1 — Type safety

<div class="text-sm op-60 mb-4">The first lie-detector. Catch the bug before it runs.</div>

<div class="grid grid-cols-2 gap-6">

<div>

```ts
// tsconfig.json
{
  "compilerOptions": {
    "strict": true,
    "noUncheckedIndexedAccess": true,
    "exactOptionalPropertyTypes": true
  }
}
```

</div>

<div>

```ts
// At every untyped boundary
import { z } from "zod"

const User = z.object({
  id: z.string().uuid(),
  email: z.email(),
})

const user = User.parse(await res.json())
```

</div>

</div>

<div v-click class="mt-6 text-center text-base op-80">
TypeScript trusts the types you write.<br/>
<strong style="color: #ff6bed">Zod / Valibot / ArkType check that runtime data still matches.</strong>
</div>

<!--
Layer 1 -- type safety.

Strict tsconfig is non-negotiable.
noUncheckedIndexedAccess and exactOptionalPropertyTypes catch
the bugs the default strict mode lets through.

But types are a compile-time fiction. At every untyped boundary --
fetch responses, route params, env vars, form input --
parse with Zod or Valibot.

CLICK -- TypeScript trusts the types you write. Schemas check
the runtime data actually matches.

With parsing in place, the agent stops reaching for `as`.

TRANSITION: Layer 2 -- lint and format. Fast enough to run on every keystroke.
-->

---

# Layer 2 — Lint & format

<div class="text-sm op-60 mb-4">Oxlint + Oxfmt. Fast enough to run on every keystroke.</div>

<div class="grid grid-cols-2 gap-6">

<Card glow>
<div class="text-xs op-60 mb-1">Oxlint</div>
<div class="text-2xl font-bold mb-2" style="color: #ff6bed">~50× faster</div>
<div class="text-xs op-70">Rust-based. Covers the high-value rules. Pair with ESLint for the long tail.</div>
</Card>

<Card glow>
<div class="text-xs op-60 mb-1">Oxfmt</div>
<div class="text-2xl font-bold mb-2" style="color: #ff6bed">~30× faster</div>
<div class="text-xs op-70">Prettier-compatible defaults. Drop-in replacement.</div>
</Card>

</div>

<div v-click class="mt-6">

```bash
# Vite+ wraps both behind one CLI
vp check     # type + lint + format
vp test      # vitest
vp build     # rolldown
```

</div>

<!--
Layer 2 -- lint and format.

Oxlint is roughly 50x faster than ESLint. Oxfmt 30x faster than Prettier.
That speed matters: lint becomes something you can run on every keystroke,
not something the agent batches at the end.

Oxlint's rule set is smaller than ESLint's, but it covers the high-value cases.
Run it as the fast first pass; keep ESLint for the rules Oxlint doesn't ship yet.

CLICK -- Vite+ is VoidZero's unified toolchain. One CLI, one config,
wraps Vite, Rolldown, Vitest, Oxlint, Oxfmt, Tsdown.

TRANSITION: Layer 3 -- the tests themselves.
-->

---

# Layer 3 — Unit tests

<div class="text-sm op-60 mb-4">Vitest. Watch mode. ESM-native. Same matchers as Jest.</div>

```ts
// formatPrice.test.ts
import { describe, it, expect } from "vitest"
import { formatPrice } from "./formatPrice"

describe("formatPrice", () => {
  it("formats EUR with two decimals", () => {
    expect(formatPrice(1234.5, "EUR")).toBe("€1,234.50")
  })

  it("rounds to nearest cent", () => {
    expect(formatPrice(1.005, "EUR")).toBe("€1.01")
  })
})
```

<div v-click class="mt-6 text-center text-base op-80">
Pure functions, hooks, stores, composables.<br/>
<strong style="color: #ff6bed">The cheapest signal. Most logic lives here.</strong>
</div>

<!--
Layer 3 -- unit tests with Vitest.

Pure functions. Hooks. Stores. Composables.
Anything you can call without mounting a component.

Vitest runs in watch mode while you code, and runs everything in CI.
Aim for high coverage of pure modules. Don't chase coverage on UI glue --
that's what the next two layers are for.

CLICK -- Cheapest signal. Most logic lives here.
The agent gets a green or red within milliseconds of saving.

TRANSITION: Layer 4 -- components, but in a REAL browser.
-->

---

# Layer 4 — Component tests

<div class="text-sm op-60 mb-4">Vitest browser mode. Real Chromium via Playwright. No more jsdom.</div>

```ts
// Button.browser.test.ts
import { render } from "vitest-browser-vue"
import { expect, test } from "vitest"
import Button from "./Button.vue"

test("shows tooltip on hover", async () => {
  const screen = render(Button, { props: { tooltip: "Save" } })
  await screen.getByRole("button").hover()
  await expect.element(screen.getByText("Save")).toBeVisible()
})
```

<div v-click class="mt-6 grid grid-cols-2 gap-4">

<Card glow>
<div class="text-xs op-60 mb-1">Works in browser mode</div>
<div class="text-sm">Hover, focus, layout, intersection observers, scroll.</div>
</Card>

<Card variant="muted">
<div class="text-xs op-60 mb-1">Broken in jsdom</div>
<div class="text-sm">All of the above. Half your CSS. Most pointer events.</div>
</Card>

</div>

<!--
Layer 4 -- component tests in a REAL browser.

The biggest win in 2026. Vitest browser mode runs your component tests
in a real Chromium via Playwright instead of jsdom.

Hover states. Focus. Layout. Intersection observers. Scroll behaviour.
All work as they do in production.

CLICK -- Browser mode handles all the things jsdom faked.
The agent can finally trust that "passes in tests" means
"works in the browser".

TRANSITION: Layer 5 -- mock the network ONCE.
-->

---

# Layer 5 — API mocking

<div class="text-sm op-60 mb-4">MSW. Define handlers once. Use them everywhere.</div>

```ts
// src/mocks/handlers.ts
import { http, HttpResponse } from "msw"

export const handlers = [
  http.get("/api/users/:id", ({ params }) =>
    HttpResponse.json({ id: params.id, email: "ada@example.com" })
  ),
]
```

<div v-click class="mt-6 text-center">

<div class="inline-grid grid-cols-4 gap-3 text-xs">
  <Card glow><div class="font-bold">Vitest</div></Card>
  <Card glow><div class="font-bold">Browser mode</div></Card>
  <Card glow><div class="font-bold">Playwright</div></Card>
  <Card glow><div class="font-bold">Dev server</div></Card>
</div>

<div class="mt-4 text-base op-80">
One source of truth.<br/>
<strong style="color: #ff6bed">Not three drifting fixture folders.</strong>
</div>

</div>

<!--
Layer 5 -- API mocking with MSW.

Hard-coded fixtures go stale. Tests that hit a real backend are flaky.
MSW intercepts at the network layer -- fetch, XHR, GraphQL --
with a service worker in the browser and a request interceptor in Node.

CLICK -- The same handlers run in Vitest, browser mode, Playwright,
AND the dev server. One source of truth. Not three drifting fixture folders.

Pair MSW with Zod schemas at the same boundary and your mocks are
typed AND schema-validated. The agent can't lie to itself about the API shape.

TRANSITION: That's 5 of 15. The rest are on the blog.
-->

---

# 15 layers of feedback

<div class="text-center text-sm op-60 mb-4">You've seen 5. There are 10 more. Every layer is a signal the agent can chase.</div>

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
You've seen the first 5: types, lint, unit, component, API mocking.

The other 10: contract testing, E2E, a11y, visual regression, performance,
dead code, i18n drift, preview deploys, AI code review, observability.

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

<div class="grid grid-cols-2 gap-4">

<div>

<div class="text-xs font-bold mb-2" style="color: #ff6bed">.claude/settings.json</div>

```json
{
  "hooks": {
    "PreToolUse": [{
      "matcher": "Bash",
      "hooks": [{
        "type": "command",
        "command": ".claude/hooks/block-destructive.sh"
      }]
    }]
  }
}
```

<div class="text-xs font-bold mb-2 mt-3" style="color: #ff6bed">block-destructive.sh</div>

```bash
#!/usr/bin/env bash
CMD=$(jq -r '.tool_input.command')
if [[ "$CMD" =~ rm[[:space:]]+-rf|git[[:space:]]+push.*--force ]]; then
  echo "Blocked: destructive command" >&2
  exit 2   # tells the agent: NOT allowed, try again
fi
```

</div>

<div>

<div class="text-xs font-bold mb-2" style="color: rgba(255,255,255,0.6)">What the agent sees</div>

```text
Agent: Bash("rm -rf node_modules")

Hook → exit 2
  stderr: Blocked: destructive command

Agent: "I was blocked. Let me try
        pnpm store prune instead."

Agent: Bash("pnpm store prune") ✓
```

<div v-click class="mt-4">

<Card variant="muted">
<div class="text-xs op-60 mb-1">Five more guards I run, same pattern</div>
<div class="text-xs op-80">enforce pnpm · protect <code>.nuxt/</code> &amp; <code>*.d.ts</code> · block <code>.env</code> reads · <code>SessionStart</code> orient · <code>PostToolUse</code> oxfmt — the one carve-out</div>
</Card>

</div>

</div>

</div>

<div v-click class="mt-4 text-center text-sm op-80 max-w-3xl mx-auto">
  Don't put typecheck / lint / tests in <code>PostToolUse</code>. <span style="color: #ff6bed">That's what Lefthook is for.</span>
</div>

<!--
Lefthook is the gate at commit time.
Hooks are the GUARDS mid-loop -- inside Claude Code itself.

Walk the LEFT slowly.

settings.json wires a PreToolUse hook on every Bash call.
The hook is just a shell script. Reads the command from stdin,
greps for rm -rf or force push. Exit code 2 = blocked.
Exit 2 is the magic number: the agent sees it as "NOT allowed,
try something else." Anything non-zero would just be an error.

RIGHT -- what the agent actually sees.
Tried rm -rf. Got blocked. Reasoned: "okay, try pnpm store prune."
Ran THAT. Green.

CLICK -- I have five more guards built the same way:
- Enforce pnpm. No npm/yarn slipping into the lockfile.
- Protect generated files. Never hand-edit .nuxt/ or components.d.ts.
- Block .env reads, including cat/head/jq escape hatches. Point at .env.example.
- SessionStart -- orient the agent: project type, branch, nuxi prepare if stale.
- The one PostToolUse carve-out: oxfmt. Normalization, not feedback. Milliseconds, not seconds.

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
  part="5"
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

<div class="text-center text-xs op-50 mb-3">Real layout from <code>alexanderop/workoutTracker</code></div>

<div class="grid grid-cols-2 gap-8 mt-2">

<div>

<FolderTree
  root
  title="src/"
  :structure="`src/
  views/
  router/
  components/
  composables/
  lib/
  db/
  stores/
  types/
  features/
    workout/
      components/
      composables/
      utils/
    timers/
      components/
      composables/
    exercises/
    settings/
    templates/`"
/>

</div>

<div class="flex flex-col justify-center gap-4">

<Card variant="muted">
<div class="text-sm op-80">Shared layers stay shared: <code>components</code>, <code>composables</code>, <code>lib</code>, <code>db</code>, <code>stores</code>, <code>types</code>.</div>
</Card>

<Card variant="muted">
<div class="text-sm op-80">Each feature is one folder — <code>workout/</code> alone has 24 components and 7 composables.</div>
</Card>

<Card glow>
<div class="text-sm"><strong style="color: #ff6bed">No <code>workout</code> imports from <code>timers</code>.</strong> The folder boundary <em>is</em> the contract.</div>
</Card>

</div>

</div>

<!--
The big idea, grounded in a real project.

This is the actual src/ layout of my workout tracker.
Ten features under features/. Shared layers above.
Views and router at the top.

The workout feature alone is 24 components and 7 composables.
That used to be 24 components scattered across src/components/workout/
and 7 composables in src/composables/. The agent had to grep across
three folders to find anything related to workouts.

Now workout/ is one folder. timers/ is one folder.
And critically -- workout does NOT import from timers.
If they need to share something, it goes up to lib/ or composables/.

TRANSITION: Let me show you what that wall does to the agent.
-->

---

# Same task, two structures

<div class="text-center text-sm op-60 mb-4">"Add a rest-timer reminder to the active workout" — same agent, same task</div>

<div class="grid grid-cols-2 gap-6">

<div>

<div class="text-xs op-50 mb-2">LEFT — Flat (the old layout)</div>

<FolderTree
  root
  title="src/"
  :structure="`src/
  components/
    workout/
      WorkoutActiveMode.vue
      WorkoutHeader.vue
      WorkoutAmrapView.vue
    settings/
    exercise/
  composables/
    useWorkout.ts
    useWorkoutMode.ts
    useRestTimer.ts
    timers/
      useAmrapTimer.ts
  stores/
    workout.ts`"
/>

</div>

<div>

<div class="text-xs op-50 mb-2">RIGHT — Feature-sliced (today)</div>

<FolderTree
  root
  title="src/"
  :structure="`src/
  features/
    workout/
      components/
        WorkoutActiveMode.vue
        WorkoutHeader.vue
      composables/
        useWorkoutMode.ts
        useWorkoutPersistence.ts
    timers/
      components/
      composables/
    exercises/
    settings/`"
/>

</div>

</div>

<div class="mt-4 grid grid-cols-2 gap-6 text-xs">
  <div class="text-center op-60">workout logic spread across <code>components/</code>, <code>composables/</code>, <code>stores/</code></div>
  <div class="text-center" style="color: #ff6bed"><code>features/workout/</code> is one folder. Cross-feature edges go through <code>lib/</code>.</div>
</div>

<!--
Same app -- my workout tracker -- two snapshots in time.

LEFT is what src/ used to look like.
WorkoutActiveMode in components/workout/.
useWorkoutMode in composables/.
Workout store somewhere else.
A change to "active workout" touches three folders.

RIGHT is the layout today.
features/workout is the unit.
Everything Workout* lives there.
If timers and workout need to share something --
say, the rest-timer state -- it gets lifted to lib/.

TRANSITION: Now watch what the agent does in each.
-->

---

# The agent traces

<div class="grid grid-cols-2 gap-4 mt-2">

<div>

<div class="text-xs font-bold mb-2" style="color: rgba(255,255,255,0.6)">LEFT — flat structure</div>

```text
Grep("workout")              → 80+ hits, 9 folders
Read WorkoutActiveMode.vue   → not the state
Read WorkoutHeader.vue       → wrong file
Grep("useWorkout")           → 30 hits, half tests
Read composables/useWorkout  → found state
Read stores/workout.ts       → found mutations
Read composables/useRest...  → timer coupling?
Edit WorkoutActiveMode.vue
Edit useWorkoutMode.ts
Edit stores/workout.ts
Bash: vitest                 → 90s, 2 fails
Read timers.spec.ts          → coupling via store
Edit useAmrapTimer.ts        → fix coupling
Bash: vitest                 → 90s, green
```

<div class="mt-3 text-center">
  <span class="text-lg font-bold" style="color: #ef4444">12 tool calls · ~3 min</span>
  <div class="text-xs op-60 mt-1">+ one accidental coupling</div>
</div>

</div>

<div>

<div class="text-xs font-bold mb-2" style="color: #ff6bed">RIGHT — modular monolith</div>

```text
Glob("src/features/workout/**") → 31 files
Read features/workout/
     composables/useWorkoutMode.ts
Read features/workout/
     components/WorkoutActiveMode.vue
Edit useWorkoutMode.ts
Edit WorkoutActiveMode.vue
Bash: vitest src/features/workout → 4s, green
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

TRANSITION: So what are the actual rules? Let me draw them.
-->

---
transition: fade-out
---

<div class="h-full flex items-center justify-center">
  <img src="/who-can-import-what.png" class="max-h-full max-w-full rounded-lg shadow-lg" />
</div>

<!--
Three rules. That's it.

ONE -- arrows only point down. lib can't import hooks.
components can't import features. The layer order is fixed.

TWO -- inside features/, siblings can't see each other.
cart cannot import checkout. If they share something,
the shared thing belongs in lib or components, not in
one feature reaching into another.

THREE -- app/ is the only place that sees the whole graph.
That's where wiring happens -- routes, providers, the
shell. Nothing else gets that view.

If you can keep these three rules in your head, the codebase
stays navigable. But you won't -- and the agent definitely won't.
So we make a machine enforce them.

TRANSITION: Here's the machine.
-->

---

# Make the boundary executable

<div class="text-center text-sm op-60 mb-4">A convention is a vibe. A lint rule is a wall.</div>

<div class="max-w-3xl mx-auto">

<div class="text-xs font-bold mb-2" style="color: #ff6bed">ESLint — the real <code>eslint.config.ts</code></div>

```ts {*}{maxHeight:'360px'}
// workoutTracker/eslint.config.ts
{
  name: 'app/feature-boundaries',
  files: ['src/**/*.{ts,vue}'],
  rules: {
    'import-x/no-restricted-paths': ['error', {
      zones: [
        // cross-feature isolation
        { target: './src/features/workout',
          from: './src/features',
          except: ['./workout'] },
        { target: './src/features/timers',
          from: './src/features',
          except: ['./timers'] },
        // ...one per feature

        // shared can't reach into features
        { target: ['./src/components', './src/composables',
                   './src/lib', './src/stores'],
          from: ['./src/features', './src/views'] },
      ],
    }],
  },
}
```

</div>

<div class="mt-4 text-center text-sm op-70">
  Every PR — mine, the agent's — fails CI the moment <strong style="color: #ff6bed">workout reaches into timers.</strong>
</div>

<!--
A convention is a vibe.
A lint rule is a wall.

This is the actual eslint.config.ts in my workout tracker.
import-x/no-restricted-paths. One zone per feature
saying "you can be imported from yourself and nothing else
under features/". Plus the inverse: shared layers cannot
import from features or views.

That is the contract. Every PR -- mine, the agent's --
fails CI the moment workout reaches into timers.

TRANSITION: But what if you have already switched to oxlint?
-->

---

# On oxlint? Write the wall yourself.

<div class="text-center text-sm op-60 mb-4">No <code>no-restricted-paths</code> rule — so generate a JS plugin.</div>

<div class="grid grid-cols-2 gap-6">

<div>

<div class="text-xs font-bold mb-2" style="color: #ff6bed">Prompt the agent</div>

```text {*}{maxHeight:'150px'}
Generate scripts/oxlint-plugin-boundaries.mjs:
 1. Read tsconfig paths.
 2. Classify importer + target by layer.
 3. Block cross-feature imports.
 4. Block upward imports (lib → features).
Wire it via jsPlugins.
```

<div class="text-xs font-bold mt-3 mb-2" style="color: #ff6bed">Wire it: <code>.oxlintrc.json</code></div>

```json
{
  "jsPlugins": [
    "./scripts/oxlint-plugin-boundaries.mjs"
  ],
  "rules": {
    "boundaries/no-cross-feature": "error"
  }
}
```

</div>

<div>

<div class="text-xs font-bold mb-2" style="color: #ff6bed">200 lines later — the agent ships</div>

```js {*}{maxHeight:'340px'}
// scripts/oxlint-plugin-boundaries.mjs
const noCrossFeature = {
  create(context) {
    return {
      ImportDeclaration(node) {
        const from = classify(context.filename)
        const to   = classify(node.source.value)
        if (!allowed(from, to)) {
          context.report({
            node,
            message: `${from.layer} → ${to.layer} forbidden`,
          })
        }
      },
    }
  },
}

export default {
  meta: { name: 'boundaries' },
  rules: { 'no-cross-feature': noCrossFeature },
}
```

</div>

</div>

<div class="mt-4 text-center text-sm op-70">
  The agent wrote the rule. <strong style="color: #ff6bed">Now the rule polices the agent.</strong>
</div>

<!--
If you have already switched to oxlint, you hit a wall:
it does not ship no-restricted-paths.

So I told the agent: generate a custom oxlint JS plugin.

oxlint exposes a JS plugin API. ESLint-compatible visitor
pattern -- create(context) returns node visitors,
context.report flags violations. Export a plugin with rules,
register it under jsPlugins, turn the rule on.

200 lines, one prompt, committed.

The point is the loop, not the linter.
The agent wrote the rule.
Now the rule polices the agent.

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

TRANSITION: Here is what the loop looks like in practice.
-->

---
layout: image
image: /afk/pipeline.png
backgroundSize: contain
---


<!--
Six phases. HITL at the edges. AFK in the middle.

Spec -- I align with the business. Human in the loop.
Slice -- agent breaks the PRD into vertical sub-tickets.
Ralph loop -- one agent per slice, fresh context every iteration, TDD inside.
Refactor -- a dedicated pass. The step LLMs always skip.
QA -- a QA agent drives the real browser.
Review -- I read the PR. HITL again.

Human judgment at the edges. Agent execution in the middle.
This is the glimpse -- full write-up on my blog if you want the long version.

TRANSITION: The most important thing in this loop is what I do when it goes wrong.
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

<div v-click class="mt-6 max-w-3xl mx-auto">

<Card variant="muted">
<div class="text-sm op-80">
The reverse also matters: <strong style="color: #ff6bed">delete rules newer models have outgrown.</strong> A constraint that helped an older model can hold a newer one back.
</div>
<div class="text-xs op-50 mt-3">Anthropic recommends a "meaningful configuration review every three to six months" — <em>How Claude Code works in large codebases</em>.</div>
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

TRANSITION: Thank you.
-->

---
layout: end
transition: fade
---

# Thank You!

<div class="flex flex-col items-center gap-6 mt-12">
  <img src="/qr-blog.png" class="w-64 h-64 bg-white p-3 rounded-lg" />
  <div class="text-lg op-80">
    <span style="color: #ff6bed">alexop.dev</span> · <span class="op-70">@alexanderopalic</span>
  </div>
</div>

<!--
[breathe] [look up]

Thank you!

Scan the QR for the blog -- AGENTS.md starter, the quality pipeline write-up,
the AFK loop deep dive, all there.

Come find me to chat. I want to hear what your AGENTS.md looks like.

[pause]
-->
