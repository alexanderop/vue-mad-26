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

TRANSITION: Quick context...
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

TRANSITION: Let me show you why I care.
-->

---
layout: statement
transition: fade-out
---

# Since March 2025 I have been AI hooked

<!--
[pause]

March 2025. I tried Claude Code seriously for the first time.
Something broke in my head.

I want to show you what happened next.
Not to brag -- to convince you the change is real.

TRANSITION: The receipts.
-->

---

# The receipts

<div class="grid grid-cols-3 gap-6 mt-8">

<Card glow>
<div class="text-xs op-50 mb-2">June 2025</div>
<div class="text-4xl font-bold" style="color: #ff6bed">0 → 48</div>
<div class="text-sm mt-2 op-80">pull requests in one month, after 17 months of zero</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-2">2025 vs 2024</div>
<div class="text-4xl font-bold" style="color: #ff6bed">5.7×</div>
<div class="text-sm mt-2 op-80">total GitHub contributions, year over year</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-2">The new baseline</div>
<div class="text-4xl font-bold" style="color: #ff6bed">~10×</div>
<div class="text-sm mt-2 op-80">sustained for 12 months — a step function, not a slope</div>
</Card>

</div>

<div class="mt-10 text-center op-60 text-sm">
  Same person. Same hours. Same brain. <span style="color: #ff6bed">Different workflow.</span>
</div>

<!--
This is my GitHub.

Zero PRs for seventeen months -- 48 in June alone.
5.7x the contributions in 2025 versus 2024.
A new baseline ten times the old one, holding steady.

This is not a slope. It is a step function.
Something switched.

TRANSITION: But this is a Vue talk. So...
-->

---

# The Vue twist

<div class="grid grid-cols-2 gap-8 mt-6">

<div>

<Card variant="muted">
<div class="text-sm op-50 mb-2">New Vue repos / year</div>
<div class="flex items-end gap-6 mt-3">
  <div>
    <div class="text-3xl font-bold op-50">28</div>
    <div class="text-xs op-50 mt-1">2024</div>
  </div>
  <div class="text-2xl op-30">→</div>
  <div>
    <div class="text-3xl font-bold" style="color: #ff6bed">47</div>
    <div class="text-xs op-50 mt-1">2025</div>
  </div>
</div>
<div class="mt-3 text-xs op-60">My most prolific Vue year. Ever.</div>
</Card>

</div>

<div>

<Card glow>
<div class="text-sm op-50 mb-2">Most-starred Vue repo</div>
<div class="text-2xl font-bold mt-2" style="color: #ff6bed">excalidrawNuxt</div>
<div class="mt-2 flex items-center gap-3 text-sm op-80">
  <div class="i-ph-star-fill" style="color: #ff6bed" />
  <span>25 stars</span>
  <span class="op-50">·</span>
  <span>created Feb 2026</span>
</div>
<div class="mt-3 text-xs op-60">After the AI pivot. Not before.</div>
</Card>

</div>

</div>

<div v-click class="mt-6 text-center text-lg">
  Post-pivot Vue projects average <strong style="color: #ff6bed">~4.5× more commits</strong> than pre-pivot ones.
</div>

<!--
Here is the part nobody tells you.

AI did not replace my Vue work. It AMPLIFIED it.

The deeper I went into AI tooling, the MORE Vue I shipped.
The BETTER Vue I shipped.
The MORE people starred it.

CLICK -- 4.5x more commits per project after the pivot.

TRANSITION: But here's the part I'm less proud of...
-->

---
layout: statement
transition: fade-out
---

# 47 new repos. Almost none finished.

<v-click>

# Always 80%. Never shipped.

</v-click>

<v-click>

# Last year's goal: understand AI.<br/>This year's goal: pick one. Finish it.

</v-click>

<!--
[honest pause]

Time for the receipts I am less proud of.

47 new repos. Almost none made it past 80%.
There is always a next idea, a next experiment, a next "what if".
The dopamine is in starting, not in shipping.

CLICK -- 80% is the worst place to leave a project.
The last 20% is where the real work lives.
Polish. Edge cases. Docs. The boring part.

CLICK -- But here is the reframe.

Last year was supposed to be exploration.
The goal was to UNDERSTAND how to use AI -- not to ship a product.
47 unfinished repos was the COST of learning fast.

This year the goal changes. Pick ONE thing. Take it to 100%.
Because shipping is the skill agents do not replace --
they amplify it, but only if you have the discipline to finish.

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
  { title: 'Discoverability', subtitle: 'Can the agent find the right code?' },
  { title: 'Feedback Loops', subtitle: 'Does it know when it is wrong?' },
  { title: 'Context', subtitle: 'Does it know why things exist?' },
  { title: 'Where this is heading', subtitle: 'The role merge' }
]" />

<!--
Six beats.

Problem first. Then what an agent really is.
Then three concrete buckets you can act on Monday.
Then where this is going.

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
<div class="text-2xl font-bold mb-3" style="color: #ff6bed">Discoverability</div>
<div class="text-sm op-80">Can the agent find the right code?</div>
<div class="mt-4 text-xs op-50">Modular monolith. Monorepo structure. Naming.</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-2">02</div>
<div class="text-2xl font-bold mb-3" style="color: #ff6bed">Feedback loops</div>
<div class="text-sm op-80">Does the agent know when it is wrong?</div>
<div class="mt-4 text-xs op-50">Tests. Linting. Types. Your backpressure.</div>
</Card>

<Card glow>
<div class="text-xs op-50 mb-2">03</div>
<div class="text-2xl font-bold mb-3" style="color: #ff6bed">Context</div>
<div class="text-sm op-80">Does the agent know why things exist?</div>
<div class="mt-4 text-xs op-50">Docs. AGENTS.md. ADRs.</div>
</Card>

</div>

<!--
Three buckets. These recur in the whole rest of the talk.

Discoverability: can it FIND the right code?
Feedback: does it know when it broke something?
Context: does it know the rules of your house?

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

TRANSITION: Concrete. In Vue. Starting with discoverability.
-->

---
transition: fade
---

<PartSlide
  part="2"
  title="Discoverability"
  subtitle="One folder = one feature"
/>

<!--
[scan room]

Bucket one. The folder structure is the API the agent uses to read your code.
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

TRANSITION: That covers discoverability. Now feedback.
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

TRANSITION: Last bucket. The biggest unlock.
-->

---
transition: fade
---

<PartSlide
  part="4"
  title="Context"
  subtitle="AGENTS.md is the unlock"
/>

<!--
[scan room]

Bucket three. The one that compounds.
-->

---

# The headline demo: same prompt, two repos

<div class="grid grid-cols-2 gap-6 mt-6">

<Card variant="muted">
<div class="text-xs font-bold mb-2" style="color: rgba(255,255,255,0.6)">RUN 1 — no AGENTS.md</div>
<div class="text-sm op-80 mb-3">Same prompt. Same Vue project. No conventions doc.</div>
<ul class="text-xs space-y-1 op-70">
  <li>· Invents an API endpoint that does not exist</li>
  <li>· Ignores the design system, inlines Tailwind</li>
  <li>· Imports composables from the wrong package</li>
  <li>· Uses Options API in a Composition-API codebase</li>
  <li>· Adds its own utility library "just in case"</li>
</ul>
</Card>

<Card glow>
<div class="text-xs font-bold mb-2" style="color: #ff6bed">RUN 2 — with AGENTS.md</div>
<div class="text-sm op-80 mb-3">Same prompt. Same project. Conventions described.</div>
<ul class="text-xs space-y-1 op-70">
  <li>· Uses the existing repo client</li>
  <li>· Imports from `@repo/ui` primitives</li>
  <li>· Drops the file in `packages/features/cart/`</li>
  <li>· Uses `&lt;script setup&gt;` and Pinia like the rest</li>
  <li>· Adds nothing it does not need</li>
</ul>
</Card>

</div>

<div v-click class="mt-8 text-center text-lg">
  Your AGENTS.md is the <strong style="color: #ff6bed">onboarding doc you never wrote</strong> for humans.<br/>
  The agent reads it before every keystroke.
</div>

<!--
[breathe]

This is the moment.

Same prompt, two repos.

LEFT -- the agent makes things up. It has no idea what your conventions are.
The output compiles, but you would not merge it.

RIGHT -- with AGENTS.md, the agent matches your patterns.
Looks like a teammate wrote it.

CLICK -- This is the onboarding doc you never wrote for humans either.
The agent reads it on every turn.

TRANSITION: What goes in it?
-->

---

# What goes in AGENTS.md

<div class="grid grid-cols-2 gap-4 mt-6">

<Card glow>
<div class="text-sm font-bold mb-2" style="color: #ff6bed">Folder conventions</div>
<div class="text-xs op-70">"Features live in <code>packages/features/*</code>."</div>
</Card>

<Card glow>
<div class="text-sm font-bold mb-2" style="color: #ff6bed">Naming rules</div>
<div class="text-xs op-70">Composables start with <code>use</code>. Stores are Pinia. No <code>useStore()</code> from components.</div>
</Card>

<Card glow>
<div class="text-sm font-bold mb-2" style="color: #ff6bed">Design system rules</div>
<div class="text-xs op-70">Never inline Tailwind. Use <code>@repo/ui</code> primitives.</div>
</Card>

<Card glow>
<div class="text-sm font-bold mb-2" style="color: #ff6bed">Test conventions</div>
<div class="text-xs op-70">Vitest. Page objects. No DOM selectors in tests.</div>
</Card>

<Card glow class="col-span-2">
<div class="text-sm font-bold mb-2" style="color: #ff6bed">ADRs link</div>
<div class="text-xs op-70">"Read <code>docs/adr/*</code> before touching <code>auth/</code> or <code>payments/</code>." The agent will. Humans should too.</div>
</Card>

</div>

<!--
Five blocks. That is most of it.

Folder conventions. Naming. Design system. Tests. ADRs.

This is not magic. It is the brief you would give a new hire.
You just have not written it down because nobody asked.

The agent asks every time.

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

TRANSITION: One more bucket -- and then the bigger picture.
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

TRANSITION: Zoom out. Where is this all heading?
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

TRANSITION: That changes the shape of a team.
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
