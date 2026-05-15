---
layout: post
title: Code Highlights
permalink: /docs/highlights
description: "Documentation · Annotate key code snippets (OOP, APIs, collision)."
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

# Code Highlights

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #FACC15; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #FACC15; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Annotate key code snippets (OOP, APIs, collision).</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #FACC15; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Portfolio review: Highlighted code examples with explanations</div>
  </div>

</div>

## What it is

Code highlights are specific, pulled-out snippets from a larger codebase, presented in the portfolio with annotations explaining what each piece is doing and why it's interesting. They're a curated tour of the most important code, not a full source dump.

## Why it matters

Reviewers can't read every line. Highlights direct attention to the work that best demonstrates competency. They also make the portfolio scannable — someone evaluating the rubric can hit the high notes in minutes.

## How GateGame implements it

The 'About GateGame' section on my portfolio homepage highlights four key code patterns from the Maze of Shadows level: inheritance & instantiation, methods with parameters (the `spline()` helper), control structures + data types (the segment array), and async I/O (the level-transition pattern). Each is shown as a code block with a short explanation.

## Code Example

```js
// One of four highlighted snippets on the homepage:
// "Methods & Parameters — converts relative coords to pixel values"
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

> Pull out the 4-5 snippets that best prove the rubric. Annotate each so the reviewer doesn't have to guess what's interesting.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/docs/mini-lesson" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Mini-Lesson Documentation</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #FACC15; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/debug/console" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Console Debugging</div></a>
</nav>
