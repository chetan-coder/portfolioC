---
layout: post
title: Methods & Parameters
permalink: /oop/methods-parameters
description: "Object-Oriented Programming · Implement methods with parameters (e.g. collisionHandler(other, direction))."
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

# Methods & Parameters

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #3B82F6; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #3B82F6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Implement methods with parameters (e.g. collisionHandler(other, direction)).</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #3B82F6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: Method signatures with 2+ parameters</div>
  </div>

</div>

## What it is

Methods are functions defined inside a class. Parameters are the inputs they accept; return values are the outputs they produce. Methods with parameters are how an object's behavior becomes flexible — the same method handles many different cases depending on what you pass in.

## Why it matters

A method that takes no parameters can only do one specific thing. A method that takes parameters can adapt: `collisionHandler(other, direction)` handles any collision against any direction, not just one hard-coded case. This is what makes code reusable.

## How GateGame implements it

The `spline()` helper takes two parameters — an `id` string and a `points` array of `[relX, relY]` pairs — and returns a fully-configured barrier object. Internally it maps each relative coordinate to pixel space using `Math.round(px * width)`. NPC `interact()` methods accept dialogue strings, button arrays, and callbacks, making each NPC's behavior data-driven rather than hard-coded.

## Code Example

```js
// Parameters: id (string) + points (array of [x,y] pairs)
// Returns: a barrier config object the engine consumes
function spline(id, points) {
  return {
    id,
    splinePoints: points.map(([px, py]) => ({
      x: Math.round(px * width),
      y: Math.round(py * height)
    })),
    visible: true,
    color: '#8B4513',
    lineWidth: 22,
  };
}
```

## Key Takeaway

> Parameters convert one specific function into a tool that handles many cases. `spline('seg1', [...])` and `spline('seg2', [...])` reuse the same logic.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/oop/writing-classes" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Writing Classes</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #3B82F6; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/oop/instantiation-objects" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Instantiation & Objects</div></a>
</nav>
