---
layout: post
title: Code Comments
permalink: /docs/comments
description: "Documentation · JSDoc comments for classes and methods."
hide: true
show_reading_time: true
---

<div style="margin: 8px 0 24px;">
  <a href="{{site.baseurl}}/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px; border: 1px solid rgba(255,255,255,0.15); border-radius: 6px; font-size: 0.85rem; color: inherit; transition: all 0.2s;">
    ← Back to Portfolio
  </a>
</div>

<div style="display: inline-block; background: #FACC151A; color: #FACC15; border: 1px solid #FACC1566; border-radius: 6px; padding: 4px 10px; font-size: 0.8rem; font-weight: 600; margin-bottom: 8px;">
  📝 Documentation
</div>

# Code Comments

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #FACC15; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #FACC15; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">JSDoc comments for classes and methods.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #FACC15; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: Comment density >10%</div>
  </div>

</div>

## What it is

JavaScript supports single-line comments (`// ...`) and block comments (`/* ... */`). JSDoc is a convention using `/** ... */` blocks with `@param`, `@returns`, and other tags — many editors (VS Code in particular) read these and provide hover-help.

## Why it matters

Comments make code teachable. Future-you and future teammates need to understand intent, not just syntax. A function that takes obscure parameters becomes self-documenting with a JSDoc block above it.

## How GateGame implements it

The `spline()` helper has a comment block explaining what the parameters mean and what the return shape is. Each major section of `GameLevelMazeSub` has a header comment describing what it sets up. Comment density across the file is tracked above the 10% bar to satisfy the CS 111 rubric.

## Code Example

```js
// ── Spline barrier helper ─────────────────────────────────────
// points: array of [relX, relY] pairs (0.0-1.0 relative to screen)
// SplineBarrier reads data.splinePoints (pixel coords),
// so we convert here.
function spline(id, points) {
  return {
    id,
    splinePoints: points.map(([px, py]) => ({
      x: Math.round(px * width),
      y: Math.round(py * height)
    })),
    lineWidth: 22,
  };
}
```

## Key Takeaway

> Comment the *why* and the *contract*, not the *what*. `// adds 1 to x` is noise; `// points are relative 0-1, we convert to pixels` is gold.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/io/json-parsing" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">JSON Parsing</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #FACC15; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/docs/mini-lesson" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Mini-Lesson Documentation</div></a>
</nav>
