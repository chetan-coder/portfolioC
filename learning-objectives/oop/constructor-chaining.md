---
layout: post
title: Constructor Chaining
permalink: /oop/constructor-chaining
description: "Object-Oriented Programming · Use super() to chain constructors and forward initialization data."
hide: true
show_reading_time: true
---

<div style="margin: 8px 0 24px;">
  <a href="{{site.baseurl}}/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px; border: 1px solid rgba(255,255,255,0.15); border-radius: 6px; font-size: 0.85rem; color: inherit; transition: all 0.2s;">
    ← Back to Portfolio
  </a>
</div>

<div style="display: inline-block; background: #3B82F61A; color: #3B82F6; border: 1px solid #3B82F666; border-radius: 6px; padding: 4px 10px; font-size: 0.8rem; font-weight: 600; margin-bottom: 8px;">
  🏛️ Object-Oriented Programming
</div>

# Constructor Chaining

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #3B82F6; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #3B82F6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Use super() to chain constructors and forward initialization data.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #3B82F6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: super(data, gameEnv) calls</div>
  </div>

</div>

## What it is

A subclass constructor must call `super(...)` before it can use `this`. The `super()` call invokes the parent class's constructor, letting the parent do its initialization first. Arguments passed to `super()` are forwarded up the chain.

## Why it matters

Without `super()` the parent never initializes — the child would start life half-built, missing whatever the parent normally sets up (position, sprite handle, engine binding). JavaScript actually throws a `ReferenceError` if you try to access `this` in a subclass constructor before calling `super()`.

## How GateGame implements it

`GameLevelMazeSub` calls `super(gameEnv)` immediately so the base `GameLevel` can register the level with the engine and bind the canvas context. Each entity subclass (`Player`, `Npc`, `SplineBarrier`) does the same with `super(data, gameEnv)` — the base class handles all the universal entity setup (position, sprite loading, hit box), the subclass adds its own fields after.

## Code Example

```js
class GameLevelMazeSub extends GameLevel {
  constructor(gameEnv) {
    super(gameEnv);            // ← required first call
    this.classes = [ /* ... */ ];
  }
}
```

## Key Takeaway

> `super()` is non-optional in subclasses — and the right place to forward initialization data so the parent can do its job.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/oop/method-overriding" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Method Overriding</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #3B82F6; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/control/iteration" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Iteration</div></a>
</nav>
