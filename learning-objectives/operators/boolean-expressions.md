---
layout: post
title: Boolean Expressions
permalink: /operators/boolean-expressions
description: "Operators · Compound conditions in game logic."
hide: true
show_reading_time: true
---

<div style="margin: 8px 0 24px;">
  <a href="{{site.baseurl}}/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px; border: 1px solid rgba(255,255,255,0.15); border-radius: 6px; font-size: 0.85rem; color: inherit; transition: all 0.2s;">
    ← Back to Portfolio
  </a>
</div>

<div style="display: inline-block; background: #14B8A61A; color: #14B8A6; border: 1px solid #14B8A666; border-radius: 6px; padding: 4px 10px; font-size: 0.8rem; font-weight: 600; margin-bottom: 8px;">
  ➕ Operators
</div>

# Boolean Expressions

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #14B8A6; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #14B8A6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Compound conditions in game logic.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #14B8A6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: &&, ||, !</div>
  </div>

</div>

## What it is

Boolean operators combine truthy/falsy values: `&&` (AND, true only if both sides are true), `||` (OR, true if either side is true), `!` (NOT, flips the value). They short-circuit, meaning JavaScript stops evaluating as soon as the result is determined.

## Why it matters

Game logic rarely depends on a single condition. 'Player is alive AND not paused AND in range' is a compound boolean. Short-circuiting also lets you write defensive checks like `obj && obj.method && obj.method()` to avoid null-reference errors.

## How GateGame implements it

Damage gating combines multiple conditions: `if (collision && !this.isVulnerable && enemy.isAlive)`. Input checks use OR: `if (key === 'ArrowUp' || key === 'w')`. Defensive method calls use short-circuit AND: `obj.data.interact && obj.data.interact()` ensures we don't crash on entities without an `interact` method.

## Code Example

```js
// Damage gate: ALL three conditions must hold
if (collision && !this.isVulnerable && enemy.isAlive) {
  this.takeDamage();
}

// Multiple keys map to same action
if (key === 'ArrowUp' || key === 'w' || key === ' ') {
  player.jump();
}

// Short-circuit guard against missing method
obj.data.interact && obj.data.interact();
```

## Key Takeaway

> Compound booleans express game rules clearly. Short-circuiting (`a && b.method()`) is a defensive coding superpower.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/operators/string-ops" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">String Operations</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #14B8A6; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/io/keyboard" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Keyboard Input</div></a>
</nav>
