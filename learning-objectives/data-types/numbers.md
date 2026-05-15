---
layout: post
title: Numbers
permalink: /data-types/numbers
description: "Data Types · Position, velocity, score tracking."
hide: true
show_reading_time: true
---

<div style="margin: 8px 0 24px;">
  <a href="{{site.baseurl}}/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px; border: 1px solid rgba(255,255,255,0.15); border-radius: 6px; font-size: 0.85rem; color: inherit; transition: all 0.2s;">
    ← Back to Portfolio
  </a>
</div>

<div style="display: inline-block; background: #F973161A; color: #F97316; border: 1px solid #F9731666; border-radius: 6px; padding: 4px 10px; font-size: 0.8rem; font-weight: 600; margin-bottom: 8px;">
  🧮 Data Types
</div>

# Numbers

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #F97316; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #F97316; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Position, velocity, score tracking.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #F97316; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: Numeric properties</div>
  </div>

</div>

## What it is

JavaScript has a single numeric type — `number` — which represents both integers and floating-point values. Numbers can be added, subtracted, multiplied, divided, and compared. There's also `Math.round()`, `Math.floor()`, `Math.random()`, and friends for common operations.

## Why it matters

Every quantitative aspect of a game is a number: position, velocity, score, lives, frame count, timer. Floats matter for smoothness (subpixel motion looks better than integer steps); integers matter for counters that shouldn't drift.

## How GateGame implements it

The Maze of Shadows uses floats between 0.0 and 1.0 for relative spline coordinates (so the level scales with canvas size), then converts them to integer pixel coordinates with `Math.round(px * width)`. The canvas dimensions, line widths, and player positions are all numbers updated continuously.

## Code Example

```js
const width  = 1280;                     // integer canvas width
const height = 720;                      // integer canvas height
const seg1 = spline('seg1', [
  [0.03, 0.945],                         // float: relative position
  [0.09, 0.940],
  [0.20, 0.920],
]);
// Inside spline(): floats → pixel integers
x: Math.round(0.03 * 1280),              // → 38
```

## Key Takeaway

> Floats give you precision and resolution independence; `Math.round()` converts them to clean pixel coordinates when you need crisp rendering.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/control/nested-conditions" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Nested Conditions</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #F97316; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/data-types/strings" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Strings</div></a>
</nav>
