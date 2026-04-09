---
theme: seriph
title: You probably don't need NgRx
info: |
  Thomas Toledo

  But you probably do need clearer state boundaries.
layout: cover
background: /pptx-assets/image1.jpeg
class: text-white
drawings:
  persist: false
transition: slide-left
mdc: true
colorSchema: dark
duration: 25min
---

# You probably don't need NgRx

### But you probably do need clearer state boundaries.

<div class="mt-16 text-sm uppercase tracking-[0.35em] opacity-75">
  Thomas Toledo
</div>

<div class="mt-3 text-base opacity-80">
  Senior Frontend Developer / Angular / React / TypeScript
</div>

---
layout: center
class: bg-slate-950
---

# In this talk

<div class="mt-10 grid grid-cols-2 gap-6 text-left text-lg">
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="text-xs uppercase tracking-[0.3em] text-slate-400">01</div>
    <div class="mt-3 font-semibold">Why teams default to NgRx</div>
  </div>
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="text-xs uppercase tracking-[0.3em] text-slate-400">02</div>
    <div class="mt-3 font-semibold">The different kinds of state</div>
  </div>
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="text-xs uppercase tracking-[0.3em] text-slate-400">03</div>
    <div class="mt-3 font-semibold">Smaller defaults in Angular</div>
  </div>
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="text-xs uppercase tracking-[0.3em] text-slate-400">04</div>
    <div class="mt-3 font-semibold">When NgRx earns its cost</div>
  </div>
</div>

<div class="mt-6 rounded-xl border border-slate-200 p-5 text-left text-lg">
  <div class="text-xs uppercase tracking-[0.3em] text-slate-400">05</div>
  <div class="mt-3 font-semibold">Two concrete examples</div>
</div>

---
layout: two-cols
layoutClass: gap-12
class: bg-slate-950
---

# Who am I?

- Thomas Toledo
- Senior Frontend Developer
- Angular / React / TypeScript
- I build and maintain complex frontend applications
- I care about architecture, clarity, and pragmatic state management
- I write and teach about Angular

::right::

<div class="mt-18 rounded-2xl border border-slate-200 p-6 text-left">
  <div class="text-xs uppercase tracking-[0.3em] text-slate-400">Find me</div>
  <div class="mt-4 text-lg font-semibold">thomastoledo.github.io</div>
  <div class="mt-2 text-lg font-semibold">linkedin.com/in/thomastoledo</div>
</div>

---
layout: two-cols
layoutClass: gap-10
class: bg-slate-950 text-white
---

# NgRx summary

<div class="mt-6 text-lg leading-8 opacity-90">
  The Store pattern gives us explicit actions, reducers, selectors, and effects.
</div>

<div class="mt-6 text-lg leading-8 opacity-90">
  It solves real coordination problems, but it also introduces real architectural weight.
</div>

<div class="mt-8 text-sm uppercase tracking-[0.3em] opacity-60">
  Reference
</div>

<div class="mt-2 text-base">
  https://ngrx.io/guide/store
</div>

::right::

<div class="flex h-full items-center justify-center py-4">
  <div class="w-full rounded-2xl border border-white/10 bg-white/3 p-5 shadow-2xl">
    <img
      src="/pptx-assets/image2.png"
      alt="NgRx state management lifecycle"
      class="mx-auto max-h-[500px] w-full object-contain"
    />
  </div>
</div>

---
class: bg-slate-950
---

# Why teams default to NgRx

<div class="mt-8 grid grid-cols-2 gap-5 text-left">
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="font-semibold">It feels like the safe default</div>
    <div class="mt-2 text-sm opacity-75">It is familiar, documented, and widely adopted across Angular teams.</div>
  </div>
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="font-semibold">We want to look scalable</div>
    <div class="mt-2 text-sm opacity-75">A store can feel like architecture maturity even before the app really needs it.</div>
  </div>
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="font-semibold">We want one mental model</div>
    <div class="mt-2 text-sm opacity-75">One tool for every state problem sounds cleaner than choosing boundaries case by case.</div>
  </div>
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="font-semibold">We are solving future problems early</div>
    <div class="mt-2 text-sm opacity-75">Teams often install NgRx to prepare for complexity that has not arrived yet.</div>
  </div>
</div>

<div class="mt-8 rounded-2xl border border-rose-200 bg-rose-50 p-6 text-left text-slate-950">
  <div class="text-xs uppercase tracking-[0.3em] text-rose-500">The reflex</div>
  <div class="mt-3 text-xl font-semibold leading-8">
    The habit is often stronger than the actual coordination problem.
  </div>
</div>

---
class: bg-slate-950
---

# Example 1: Search, filters, and pagination

<div class="mt-2 text-sm opacity-70">
  Context: search input, filters, sorting, pagination, API results, and maybe shareable URL state.
</div>

<div class="mt-8 grid grid-cols-2 gap-6 text-left text-sm leading-6">
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="font-semibold">Why teams often over-engineer this</div>
    <ul class="mt-4 space-y-2">
      <li>There seem to be many moving parts.</li>
      <li>Several user interactions affect the same screen.</li>
      <li>It feels safer to centralize everything.</li>
      <li>It looks like "a lot of state".</li>
    </ul>
  </div>
  <div class="rounded-2xl border border-emerald-200 bg-emerald-50 p-5 text-slate-950">
    <div class="font-semibold">Why I still would not start with NgRx</div>
    <ul class="mt-4 space-y-2">
      <li>Most of it is UI state plus server state.</li>
      <li>Filters can live in query params.</li>
      <li>Results belong to a data service, not automatically a global store.</li>
      <li>The boundary is still one feature.</li>
    </ul>
  </div>
</div>

<div class="mt-8 rounded-2xl border border-emerald-200 bg-emerald-50 p-5 text-left text-slate-950">
  <div class="font-semibold text-lg">Use instead</div>
  <div class="mt-2 text-base leading-7">
    Component Signals for local interactions, query params for shareable filters, and a feature data service for fetching results.
  </div>
</div>

---
class: bg-slate-950
---

# Different kinds of state

<div class="mt-8 grid grid-cols-2 gap-5 text-left">
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="font-semibold">UI state</div>
    <div class="mt-2 text-sm opacity-75">Open or closed modals, active tabs, loading flags, selected rows, transient interactions.</div>
  </div>
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="font-semibold">Form state</div>
    <div class="mt-2 text-sm opacity-75">Inputs, validation, dirty status, step progress, and temporary draft values.</div>
  </div>
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="font-semibold">Server state</div>
    <div class="mt-2 text-sm opacity-75">Backend data, caching, refetching, loading, error handling, synchronization.</div>
  </div>
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="font-semibold">Client or domain state</div>
    <div class="mt-2 text-sm opacity-75">Cart contents, persisted filters, workflow progress, business rules, cross-page coordination.</div>
  </div>
</div>

<div class="mt-8 text-lg font-semibold">
  Not every kind of state needs the same tool, or even the same boundary.
</div>

---
class: bg-slate-950
---

# Smaller defaults first

<div class="mt-8 grid grid-cols-2 gap-5 text-left">
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="text-xs uppercase tracking-[0.3em] text-slate-400">UI state</div>
    <div class="mt-3 text-xl font-semibold">Component state and Signals</div>
    <div class="mt-3 text-sm leading-6 opacity-75">Keep ephemeral state close to the component that owns the interaction.</div>
  </div>
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="text-xs uppercase tracking-[0.3em] text-slate-400">Form state</div>
    <div class="mt-3 text-xl font-semibold">Angular forms</div>
    <div class="mt-3 text-sm leading-6 opacity-75">Forms already model validation, dirtiness, submission, and step-by-step progress well.</div>
  </div>
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="text-xs uppercase tracking-[0.3em] text-slate-400">Server state</div>
    <div class="mt-3 text-xl font-semibold">Route state plus a data service</div>
    <div class="mt-3 text-sm leading-6 opacity-75">Use query params for shareable state and keep fetching or caching close to the feature.</div>
  </div>
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="text-xs uppercase tracking-[0.3em] text-slate-400">Feature workflow</div>
    <div class="mt-3 text-xl font-semibold">Feature service or SignalStore</div>
    <div class="mt-3 text-sm leading-6 opacity-75">Share state inside the feature before you promote it to a global event-driven system.</div>
  </div>
</div>

<div class="mt-8 rounded-2xl border border-emerald-200 bg-emerald-50 p-6 text-left text-slate-950">
  <div class="text-2xl font-semibold leading-9">
    The best alternative is usually not a different store.
  </div>
  <div class="mt-2 text-xl leading-8 opacity-85">
    It is a smaller state boundary.
  </div>
</div>

---
class: bg-slate-950
---

# Hidden cost of NgRx

<div class="mt-6 space-y-5 text-left">
  <div class="rounded-xl border border-slate-200 p-4">
    <strong>Conceptual overhead</strong> - Actions, reducers, selectors, effects, facades, conventions, and more architectural rules to teach.
  </div>
  <div class="rounded-xl border border-slate-200 p-4">
    <strong>Scattered logic</strong> - One user interaction can be split across multiple files and abstractions.
  </div>
  <div class="rounded-xl border border-slate-200 p-4">
    <strong>Onboarding cost</strong> - Developers may need to learn the state architecture before they can change product behavior safely.
  </div>
  <div class="rounded-xl border border-slate-200 p-4">
    <strong>Globalization pressure</strong> - Once the store exists, teams are tempted to push more and more state into it.
  </div>
</div>

<div class="mt-8 text-lg font-semibold">
  You are paying for coordination machinery, whether or not the app truly needs that machinery yet.
</div>

---
class: bg-slate-950
---

# When NgRx earns its cost

<div class="mt-8 grid grid-cols-2 gap-5 text-left">
  <div class="rounded-xl bg-slate-50 p-5 text-slate-950">State is shared across distant parts of the app</div>
  <div class="rounded-xl bg-slate-50 p-5 text-slate-950">Business transitions need to be explicit and consistent</div>
  <div class="rounded-xl bg-slate-50 p-5 text-slate-950">Traceability, auditing, or replay matter</div>
  <div class="rounded-xl bg-slate-50 p-5 text-slate-950">Several side effects need orchestration</div>
  <div class="rounded-xl bg-slate-50 p-5 text-slate-950">Multiple teams need strong conventions</div>
  <div class="rounded-xl bg-slate-50 p-5 text-slate-950">The app behaves like a system, not just a UI</div>
</div>

---
class: bg-slate-950
---

# Example 2: Multi-step checkout

<div class="mt-2 text-sm opacity-70">
  Context: cart, shipping, delivery, payment, summary, back-and-forth navigation, partial save, and business rules that may grow over time.
</div>

<div class="mt-8 grid grid-cols-2 gap-6 text-left text-sm leading-6">
  <div class="rounded-2xl border border-amber-200 bg-amber-50 p-5 text-slate-950">
    <div class="font-semibold">Start here</div>
    <ul class="mt-4 space-y-2">
      <li>Angular forms for each step</li>
      <li>A feature service or SignalStore for the checkout session</li>
      <li>Keep state inside the checkout feature</li>
      <li>Persist a draft only if the product really needs it</li>
    </ul>
  </div>
  <div class="rounded-2xl border border-sky-200 bg-sky-50 p-5 text-slate-950">
    <div class="font-semibold">Move to NgRx when</div>
    <ul class="mt-4 space-y-2">
      <li>Rules and transitions multiply</li>
      <li>Many side effects need orchestration</li>
      <li>Several distant features participate in the workflow</li>
      <li>Traceability and recoverability become business-critical</li>
    </ul>
  </div>
</div>

<div class="mt-8 rounded-2xl border border-sky-200 bg-sky-50 p-5 text-left text-slate-950">
  <div class="font-semibold text-lg">Recommendation</div>
  <div class="mt-2 text-base leading-7">
    Start feature-local. Graduate to NgRx when the checkout becomes a business system rather than just a feature flow.
  </div>
</div>

---
class: bg-slate-950
---

# Quick decision framework

<div class="mt-8 grid grid-cols-3 gap-5 text-left text-sm leading-6">
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="text-xs uppercase tracking-[0.3em] text-slate-400">Keep it local</div>
    <ul class="mt-4 space-y-2">
      <li>One screen or one interaction</li>
      <li>Mostly UI or form state</li>
      <li>Short-lived and easy to explain</li>
      <li>Component state is enough</li>
    </ul>
  </div>
  <div class="rounded-2xl border border-amber-200 bg-amber-50 p-5 text-slate-950">
    <div class="text-xs uppercase tracking-[0.3em] text-amber-600">Keep it in the feature</div>
    <ul class="mt-4 space-y-2">
      <li>A few screens share the state</li>
      <li>There is a bounded workflow</li>
      <li>Lifetime stays inside one feature</li>
      <li>Use a feature service or SignalStore</li>
    </ul>
  </div>
  <div class="rounded-2xl border border-sky-200 bg-sky-50 p-5 text-slate-950">
    <div class="text-xs uppercase tracking-[0.3em] text-sky-700">Reach for NgRx</div>
    <ul class="mt-4 space-y-2">
      <li>Distant shared state</li>
      <li>Business-critical transitions</li>
      <li>Hard orchestration across features</li>
      <li>Traceability becomes important</li>
    </ul>
  </div>
</div>

<div class="mt-8 text-lg font-semibold">
  The question is not "do we have state?" It is "where should this state live?"
</div>

---
layout: center
background: /pptx-assets/image1.jpeg
class: text-white
---

<div class="text-4xl leading-tight italic">
  "I freaking love NgRx"
</div>

<div class="mt-8 text-sm uppercase tracking-[0.35em] opacity-75">
  Thomas Toledo
</div>

---
layout: cover
background: /pptx-assets/image1.jpeg
class: text-white
---

# NgRx is not the default. It is a trade-off.

<div class="mx-auto mt-8 max-w-4xl rounded-2xl border border-white/20 bg-black/25 p-8 text-left backdrop-blur-sm">
  <ul class="space-y-4 text-2xl leading-9">
    <li>Keep local state local</li>
    <li>Keep feature state inside the feature</li>
    <li>Don't confuse server state with app state</li>
    <li>Reach for NgRx when the complexity is real</li>
  </ul>
</div>

<div class="mt-12 text-center">
  <div class="text-2xl font-semibold">You probably don't need NgRx.</div>
  <div class="mt-2 text-xl opacity-85">You do need clear state boundaries.</div>
</div>
