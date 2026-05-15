---
layout: post
title: Conditionals
permalink: /control/conditionals
description: "Control Structures · Implement collision detection and state transitions."
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

# Conditionals

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #10B981; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #10B981; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Implement collision detection and state transitions.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #10B981; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: if/else, nested conditions</div>
  </div>

</div>

## What it is

Conditionals — `if`, `else if`, `else` — branch program execution based on whether an expression evaluates to truthy or falsy. They're the most fundamental control structure in any imperative language.

## Why it matters

Every decision the game makes is a conditional. Did the player land on a platform or fall through? Is the NPC in dialogue range? Is the level complete? Each is an `if`. Without conditionals, the game has no choices, no reactions, no logic.

## How GateGame implements it

Conditionals run constantly throughout Maze of Shadows. They check whether the player has collided with a SplineBarrier, whether dialogue is currently open, whether the Exit Warden's collision triggers the level-transition prompt, and which button (`Step Through` vs `Not yet`) the player clicked.

## Code Example

```js
// Conditional inside the level-iteration loop
for (const obj of this.classes) {
  if (obj.class === Npc) {           // class match
    if (obj.data.interact) {         // method exists
      obj.data.interact();           // safe to call
    }
  }
}
```

## Key Takeaway

> Conditionals are the moments the game makes a choice. Every interactive game is, structurally, a tree of `if`s.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/control/iteration" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Iteration</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #10B981; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/control/nested-conditions" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Nested Conditions</div></a>
</nav>
