---
layout: post
title: Mathematical Operators
permalink: /operators/mathematical
description: "Operators · Physics calculations (gravity, velocity, collision)."
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

# Mathematical Operators

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #14B8A6; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #14B8A6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Physics calculations (gravity, velocity, collision).</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #14B8A6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: +, -, *, / in physics</div>
  </div>

</div>

## What it is

JavaScript's arithmetic operators are `+`, `-`, `*`, `/`, `%` (modulo), and `**` (exponentiation). They follow standard precedence rules and operate on numbers (and, for `+`, strings). The `Math` object provides supporting functions like `Math.round()`, `Math.floor()`, and `Math.sqrt()`.

## Why it matters

Physics is arithmetic. Position updates are addition. Gravity is acceleration applied via addition each frame. Collision response often involves subtraction (move out of overlap) and multiplication (scale velocity). Modulo wraps sprite animation indexes.

## How GateGame implements it

Inside `spline()`, multiplication scales relative coordinates to canvas pixels: `px * width`. `Math.round()` converts the resulting float to a clean integer for crisp rendering. The engine's physics adds velocity to position each frame, applies gravity by adding to velocity, and uses subtraction to push entities out of overlapping barriers.

## Code Example

```js
// Math operators in spline(): multiply to scale, round to integer
splinePoints: points.map(([px, py]) => ({
  x: Math.round(px * width),     // multiply, then round
  y: Math.round(py * height)
})),

// Physics-style example: gravity + velocity
this.y  += this.vy;              // position += velocity
this.vy += gravity;              // velocity += gravity (each frame)
```

## Key Takeaway

> Math operators are the verbs of physics. Position moves by addition, gravity accumulates into velocity, scaling happens by multiplication.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/data-types/objects" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Objects (JSON)</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #14B8A6; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/operators/string-ops" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">String Operations</div></a>
</nav>
