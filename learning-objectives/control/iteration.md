---
layout: post
title: Iteration
permalink: /control/iteration
description: "Control Structures · Use loops for game object arrays and animation frames."
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

# Iteration

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #10B981; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #10B981; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Use loops for game object arrays and animation frames.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #10B981; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: for, forEach, while loops</div>
  </div>

</div>

## What it is

Iteration means repeating an action over a sequence of values. JavaScript offers several looping constructs: `for` for index-based loops, `forEach` for callback-based iteration over arrays, `for...of` for value-based iteration, and `while` for condition-based loops. Each has its own ergonomic sweet spot.

## Why it matters

Games are inherently iterative — the game loop runs 60 times per second, and inside each frame you iterate over every active entity. Without efficient looping, a level with dozens of objects would visibly hitch every frame.

## How GateGame implements it

The `spline()` helper uses `Array.map()` to iterate over each `[relX, relY]` pair and convert it to pixel coordinates. Inside the engine's game loop, `gameObjects.forEach(obj => obj.update())` runs every frame to advance physics on every active entity. The level-load code uses `for...of` to iterate the `this.classes` array and instantiate each entry.

## Code Example

```js
// for...of loop over the classes array
for (const obj of this.classes) {
  if (obj.class === Npc) {
    if (obj.data.interact) {
      obj.data.interact();
    }
  }
}

// Array.map() inside spline() — iterates over coordinate pairs
splinePoints: points.map(([px, py]) => ({
  x: Math.round(px * width),
  y: Math.round(py * height)
})),
```

## Key Takeaway

> Pick the loop that matches the shape of your data: `forEach`/`map` for transforming arrays, `for...of` for cleanly iterating without indexes, `while` for condition-driven work.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/oop/constructor-chaining" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Constructor Chaining</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #10B981; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/control/conditionals" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Conditionals</div></a>
</nav>
