---
theme: seriph
title: You probably don't need NgRx
info: |
  Thomas Toledo

  But you probably do need clearer state boundaries.
seoMeta:
  ogTitle: You probably don't need NgRx
  ogDescription: But you probably do need clearer state boundaries.
  ogImage: https://thomastoledo.github.io/you-probably-dont-need-ngrx/og-image.png
  ogUrl: https://thomastoledo.github.io/you-probably-dont-need-ngrx/
  twitterCard: summary_large_image
  twitterTitle: You probably don't need NgRx
  twitterDescription: But you probably do need clearer state boundaries.
  twitterImage: https://thomastoledo.github.io/you-probably-dont-need-ngrx/og-image.png
layout: cover
background: /pptx-assets/image1.jpeg
class: text-white
drawings:
  persist: false
transition: slide-left | slide-right
mdc: true
colorSchema: dark
routerMode: hash
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
transition: slide-up | slide-down
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
transition: slide-left | slide-right
---

# Why teams default to NgRx

<div class="mt-8 grid grid-cols-2 gap-5 text-left">
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="font-semibold">It feels like the safe default</div>
    <div class="mt-2 text-sm opacity-75">It is familiar, documented, and widely adopted across Angular teams.</div>
  </div>
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="font-semibold">We want to look scalable</div>
    <div class="mt-2 text-sm opacity-75">A store can make the app feel more serious even before the app really needs it.</div>
  </div>
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="font-semibold">We want one mental model</div>
    <div class="mt-2 text-sm opacity-75">One tool for every state problem sounds cleaner than deciding case by case where state should live.</div>
  </div>
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="font-semibold">We are solving future problems early</div>
    <div class="mt-2 text-sm opacity-75">Teams often install NgRx to prepare for complexity that has not arrived yet.</div>
  </div>
</div>

<div class="mt-8 rounded-2xl border border-rose-200 bg-rose-50 p-6 text-left text-slate-950">
  <div class="text-xs uppercase tracking-[0.3em] text-rose-500">The reflex</div>
  <div class="mt-3 text-xl font-semibold leading-8">
    The habit is often stronger than the actual problem.
  </div>
</div>

---
class: bg-slate-950
transition: slide-left | slide-right
---

# Example 1: Search, filters, and pagination

<div class="mt-2 text-sm opacity-70">
  Context: search input, filters, sorting, pagination, API results, and maybe filters saved in the URL.
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
      <li>Results belong to a data service, not automatically an app-wide store.</li>
      <li>All of this still belongs to one screen or feature.</li>
    </ul>
  </div>
</div>

<div class="mt-8 rounded-2xl border border-emerald-200 bg-emerald-50 p-5 text-left text-slate-950">
  <div class="font-semibold text-lg">Use instead</div>
  <div class="mt-2 text-base leading-7">
    Component Signals for local UI, query params for URL-backed filters, and a feature data service for fetching results.
  </div>
</div>

---
layout: center
class: bg-slate-950
transition: slide-up | slide-down
---

# Schema: keep the state small

```mermaid {scale: 0.8}
flowchart LR
  User([User])
  Page[Search Page]
  Filters[Filters and Sort UI<br/>local Signals]
  Route[Query Params<br/>filters in the URL]
  Service[Feature Data Service]
  API[(Backend API)]
  Results[Results List]

  User --> Page
  Page --> Filters
  Filters <--> Route
  Filters --> Service
  Route --> Service
  Service --> API
  Service --> Results
  Results --> Page
```

<div class="mt-6 text-center text-base opacity-80">
  Keep each kind of state in the place that already fits: local UI in the component, URL filters in the route, and backend data in a feature service.
</div>

---
class: bg-slate-950
transition: slide-up | slide-down
---

# Different kinds of state

<div class="mt-8 grid grid-cols-2 gap-5 text-left">
  <div class="rounded-xl border border-slate-200 p-5">
    <div class="font-semibold">UI state</div>
    <div class="mt-2 text-sm opacity-75">Open or closed modals, active tabs, loading flags, selected rows, short-lived interactions.</div>
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
    <div class="mt-2 text-sm opacity-75">Cart contents, saved filters, step-by-step progress, business rules, state shared across screens.</div>
  </div>
</div>

<div class="mt-8 text-lg font-semibold">
  Not every kind of state needs the same tool, or even the same place to live.
</div>

---
class: bg-slate-950
transition: slide-left | slide-right
---

# Smaller defaults first

<div class="mt-6 grid grid-cols-2 gap-4 text-left">
  <div class="rounded-2xl border border-slate-200 p-4">
    <div class="text-[10px] uppercase tracking-[0.25em] text-slate-400">UI state</div>
    <div class="mt-2 text-lg font-semibold leading-7">Component state and Signals</div>
    <div class="mt-2 text-xs leading-5 opacity-75">Keep short-lived state close to the component that owns the interaction.</div>
  </div>
  <div class="rounded-2xl border border-slate-200 p-4">
    <div class="text-[10px] uppercase tracking-[0.25em] text-slate-400">Form state</div>
    <div class="mt-2 text-lg font-semibold leading-7">Angular forms</div>
    <div class="mt-2 text-xs leading-5 opacity-75">Forms already model validation, dirtiness, submission, and step-by-step progress well.</div>
  </div>
  <div class="rounded-2xl border border-slate-200 p-4">
    <div class="text-[10px] uppercase tracking-[0.25em] text-slate-400">Server state</div>
    <div class="mt-2 text-lg font-semibold leading-7">Route state plus a data service</div>
    <div class="mt-2 text-xs leading-5 opacity-75">Use query params for URL state and keep fetching or caching close to the feature.</div>
  </div>
  <div class="rounded-2xl border border-slate-200 p-4">
    <div class="text-[10px] uppercase tracking-[0.25em] text-slate-400">Shared feature state</div>
    <div class="mt-2 text-lg font-semibold leading-7">Feature service or SignalStore</div>
    <div class="mt-2 text-xs leading-5 opacity-75">Keep shared state inside the feature before turning it into an app-wide event system.</div>
  </div>
</div>

---
class: bg-slate-950
---

# Hidden cost of NgRx

<div class="mt-6 space-y-5 text-left">
  <div class="rounded-xl border border-slate-200 p-4">
    <strong>More things to learn</strong> - Actions, reducers, selectors, effects, and extra patterns the team needs to understand.
  </div>
  <div class="rounded-xl border border-slate-200 p-4">
    <strong>Scattered logic</strong> - One user interaction can be split across multiple files and abstractions.
  </div>
  <div class="rounded-xl border border-slate-200 p-4">
    <strong>Onboarding cost</strong> - Developers may need to learn the state architecture before they can change product behavior safely.
  </div>
  <div class="rounded-xl border border-slate-200 p-4">
    <strong>Everything drifts into the store</strong> - Once the store exists, teams are tempted to put more and more state into it.
  </div>
</div>

<div class="mt-8 text-lg font-semibold">
  You are paying for extra machinery, whether or not the app truly needs it yet.
</div>

---
class: bg-slate-950
---

# When NgRx is worth it

<div class="mt-8 grid grid-cols-2 gap-5 text-left">
  <div class="rounded-xl bg-slate-50 p-5 text-slate-950">State is shared across far-apart parts of the app</div>
  <div class="rounded-xl bg-slate-50 p-5 text-slate-950">The allowed steps in the flow must stay clear and consistent</div>
  <div class="rounded-xl bg-slate-50 p-5 text-slate-950">Traceability matters: you need to explain why something happened</div>
  <div class="rounded-xl bg-slate-50 p-5 text-slate-950">One action triggers several follow-up actions</div>
  <div class="rounded-xl bg-slate-50 p-5 text-slate-950">Many developers need the same rules and patterns</div>
  <div class="rounded-xl bg-slate-50 p-5 text-slate-950">You are modeling a process, not just a screen</div>
</div>

---
class: bg-slate-950
transition: slide-up | slide-down
---

# A few loaded words

<div class="mt-8 grid grid-cols-2 gap-5 text-left text-sm leading-6">
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="font-semibold">Business transitions</div>
    <div class="mt-2 opacity-75">
      The allowed step changes in a flow.
    </div>
    <div class="mt-3 text-slate-300">
      Example: an order can go from <strong>cart</strong> to <strong>paid</strong> to <strong>shipped</strong>, but not directly from <strong>cart</strong> to <strong>shipped</strong>.
    </div>
  </div>
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="font-semibold">Chaining several actions</div>
    <div class="mt-2 opacity-75">
      One event triggers several external actions.
    </div>
    <div class="mt-3 text-slate-300">
      Example: after payment succeeds, save the order, reserve stock, clear the cart, and send a confirmation email.
    </div>
  </div>
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="font-semibold">Traceability</div>
    <div class="mt-2 opacity-75">
      Being able to answer "what happened and why?"
    </div>
    <div class="mt-3 text-slate-300">
      Example: why did this order end up canceled, or why did this user lose their discount?
    </div>
  </div>
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="font-semibold">Auditing or replay</div>
    <div class="mt-2 opacity-75">
      Looking back at the sequence later, or replaying it.
    </div>
    <div class="mt-3 text-slate-300">
      Example: support or compliance can review the steps that led to a refund, duplicate charge, or failed checkout.
    </div>
  </div>
</div>

---
layout: center
class: bg-slate-950
transition: slide-up | slide-down
---

# When the flow gets big enough for NgRx

```mermaid {scale: 0.75}
flowchart LR
  Cart[Cart Step]
  Shipping[Shipping Step]
  Payment[Payment Step]
  Summary[Summary Step]
  Store[(NgRx Store)]
  Effects[Effects]
  API[(Backend APIs)]
  Rules[Business Rules<br/>and transitions]
  Audit[Traceability]

  Cart -->|dispatch| Store
  Shipping -->|dispatch| Store
  Payment -->|dispatch| Store
  Summary -->|select| Store
  Store --> Rules
  Rules --> Store
  Store --> Effects
  Effects --> API
  Effects --> Store
  Store --> Audit
```

<div class="mt-6 text-center text-base opacity-80">
  This is where NgRx starts paying for itself: several parts of the app need to stay in sync through shared events, rules, and follow-up actions.
</div>

---
class: bg-slate-950
transition: slide-left | slide-right
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
      <li>Rules and allowed state changes multiply</li>
      <li>One action triggers many external effects</li>
      <li>Several separate parts of the app take part in the flow</li>
      <li>You need to explain and recover what happened</li>
    </ul>
  </div>
</div>

<div class="mt-8 rounded-2xl border border-sky-200 bg-sky-50 p-5 text-left text-slate-950">
  <div class="font-semibold text-lg">Recommendation</div>
  <div class="mt-2 text-base leading-7">
    Start inside the checkout feature. Move to NgRx if checkout turns into a core business flow with lots of rules.
  </div>
</div>

---
class: bg-slate-950
transition: slide-up | slide-down
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
      <li>There is a flow with a clear start and end</li>
      <li>It only matters inside one feature</li>
      <li>Use a feature service or SignalStore</li>
    </ul>
  </div>
  <div class="rounded-2xl border border-sky-200 bg-sky-50 p-5 text-slate-950">
    <div class="text-xs uppercase tracking-[0.3em] text-sky-700">Reach for NgRx</div>
    <ul class="mt-4 space-y-2">
      <li>Distant shared state</li>
      <li>Important business steps</li>
      <li>Hard-to-follow logic across screens and API calls</li>
      <li>You need to explain what happened</li>
    </ul>
  </div>
</div>

<div class="mt-8 text-lg font-semibold">
  The question is not "do we have state?" It is "where should it live?"
</div>

---
class: bg-slate-950
transition: slide-left | slide-right
---

# If not NgRx, then what?

<div class="mt-8 grid grid-cols-2 gap-5 text-left">
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="font-semibold">Angular Signals + services</div>
    <div class="mt-2 text-sm leading-6 opacity-75">
      Usually the best default for local state and feature state.
    </div>
  </div>
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="font-semibold">NgRx SignalStore</div>
    <div class="mt-2 text-sm leading-6 opacity-75">
      A more structured option when a feature needs more shape, but not the full Store pattern.
    </div>
  </div>
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="font-semibold">NGXS</div>
    <div class="mt-2 text-sm leading-6 opacity-75">
      Another Angular-focused store option with a simpler mental model for some teams.
    </div>
  </div>
  <div class="rounded-2xl border border-slate-200 p-5">
    <div class="font-semibold">Elf</div>
    <div class="mt-2 text-sm leading-6 opacity-75">
      Lightweight and modular if you want a store approach with less framework weight.
    </div>
  </div>
</div>

<div class="mt-8 rounded-2xl border border-emerald-200 bg-emerald-50 p-5 text-left text-slate-950">
  <div class="text-lg font-semibold leading-7">
    The best alternative is often not a different state library.
  </div>
  <div class="mt-1 text-base leading-6 opacity-85">
    It is a smaller state boundary and a simpler default.
  </div>
</div>

---
layout: center
background: /pptx-assets/image1.jpeg
class: text-white
transition: slide-up | slide-down
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
transition: slide-left | slide-right
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

---
layout: center
background: /pptx-assets/image1.jpeg
class: text-white
transition: slide-up | slide-down
---

<div class="text-5xl font-semibold leading-tight">
  Thank you
</div>

<div class="mt-8 text-lg opacity-85">
  Questions?
</div>
