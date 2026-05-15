---
layout: post
title: Inheritance (Basic)
permalink: /oop/inheritance
description: "Object-Oriented Programming · Create class hierarchy with 2+ levels (e.g. GameObject → Character → Player)."
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

# Inheritance (Basic)

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #3B82F6; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #3B82F6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Create class hierarchy with 2+ levels (e.g. GameObject → Character → Player).</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #3B82F6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: extends keyword, inheritance chain</div>
  </div>

</div>

## What it is

Inheritance lets one class extend another using the `extends` keyword. The child class automatically gets the parent's properties and methods, and can add new ones or override existing ones. Multi-level inheritance chains the relationship — a grandchild inherits from its parent, which inherits from its grandparent.

## Why it matters

Inheritance is code reuse at the architecture level. Position, velocity, sprite rendering, and physics belong on a base class because *every* entity needs them. Without inheritance, you'd duplicate that boilerplate in every single class.

## How GateGame implements it

My class hierarchy goes three levels deep. `GameLevelMazeSub extends GameLevel` for the level itself. Inside the level, the entity chain is `GameObject → Character → Player` (and similarly for `Npc`). The engine's `GameObject` handles position and the abstract draw lifecycle; `Character` adds animation frames and physics defaults; `Player` adds keyboard input and score tracking on top. Three levels comfortably exceeds the 2+ requirement.

## Code Example

```js
// Level inherits from the engine's GameLevel
class GameLevelMazeSub extends GameLevel {
  constructor(gameEnv) {
    super(gameEnv);
    // ... instantiate this.classes
  }
}

// Entity chain (provided by the engine):
// GameObject → Character → Player
```

## Key Takeaway

> A 3-level chain (`GameObject → Character → Player`) means the physics code lives in exactly one place — and every entity gets it for free.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/oop/instantiation-objects" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Instantiation & Objects</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #3B82F6; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/oop/method-overriding" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Method Overriding</div></a>
</nav>
