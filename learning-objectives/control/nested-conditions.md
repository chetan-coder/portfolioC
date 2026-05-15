---
layout: post
title: Nested Conditions
permalink: /control/nested-conditions
description: "Control Structures · Complex game logic (e.g. power-up + collision + direction)."
hide: true
show_reading_time: true
---

<div style="margin: 8px 0 24px;">
  <a href="{{site.baseurl}}/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px; border: 1px solid rgba(255,255,255,0.15); border-radius: 6px; font-size: 0.85rem; color: inherit; transition: all 0.2s;">
    ← Back to Portfolio
  </a>
</div>

<div style="display: inline-block; background: #10B9811A; color: #10B981; border: 1px solid #10B98166; border-radius: 6px; padding: 4px 10px; font-size: 0.8rem; font-weight: 600; margin-bottom: 8px;">
  🔁 Control Structures
</div>

# Nested Conditions

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #10B981; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #10B981; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Complex game logic (e.g. power-up + collision + direction).</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #10B981; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: Multi-level conditionals</div>
  </div>

</div>

## What it is

Nested conditions are `if` statements inside other `if` statements. They're used when a check only makes sense after a previous check has passed — e.g. you can only ask 'did the player land on top?' if you've already confirmed 'did the player collide at all?'.

## Why it matters

Some logic genuinely can't be flattened into a single compound expression. If condition B is only meaningful when condition A is true, nesting reflects that dependency clearly. A flat chain of `&&` operators would conceal the structure.

## How GateGame implements it

NPC interaction logic uses nested conditionals. The outer check verifies the iterated object is the right class (`obj.class === Npc`); the inner check confirms an `interact` method exists before calling it. This prevents `undefined is not a function` errors when an entity in the array doesn't have an `interact` handler.

## Code Example

```js
// Nested: class check → method existence check → call
for (const obj of this.classes) {
  if (obj.class === Npc) {            // outer: is this an NPC?
    if (obj.data.interact) {          // inner: does it have interact()?
      if (player.isNear(obj)) {       // deeper: is player in range?
        obj.data.interact();
      }
    }
  }
}
```

## Key Takeaway

> Nest when each check depends on the previous one passing. Flatten when the conditions are independent.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/control/conditionals" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Conditionals</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #10B981; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/data-types/numbers" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Numbers</div></a>
</nav>
