---
layout: post
title: Hit Box Visualization
permalink: /debug/hitbox
description: "Debugging · Draw / visualize collision boundaries to refine detection."
hide: true
show_reading_time: true
---

<div style="margin: 8px 0 24px;">
  <a href="{{site.baseurl}}/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px; border: 1px solid rgba(255,255,255,0.15); border-radius: 6px; font-size: 0.85rem; color: inherit; transition: all 0.2s;">
    ← Back to Portfolio
  </a>
</div>

<div style="display: inline-block; background: #EF44441A; color: #EF4444; border: 1px solid #EF444466; border-radius: 6px; padding: 4px 10px; font-size: 0.8rem; font-weight: 600; margin-bottom: 8px;">
  🐛 Debugging
</div>

# Hit Box Visualization

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #EF4444; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EF4444; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Draw / visualize collision boundaries to refine detection.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EF4444; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Demo: Toggle hit box display, adjust collision rectangles</div>
  </div>

</div>

## What it is

Hit box visualization means rendering the collision shape of every game object directly onto the canvas, usually as a colored outline overlay. It's a debug-only mode toggled by a flag or keypress.

## Why it matters

Collision bugs are often invisible until you can see the actual geometry. A sprite that looks fine might have a hit box that's 2 pixels too wide, causing false collisions. Visualizing it makes the bug obvious.

## How GateGame implements it

When `gameEnv.debug` is true, every entity's `draw()` adds a `ctx.strokeRect()` call after its sprite. This outlines each hit box in red on top of the rendered sprite. The same technique reveals the spline barriers' actual click-paths so you can see exactly where the maze walls sit.

## Code Example

```js
draw() {
  // Render the sprite as normal
  this.ctx.drawImage(this.spriteSheet, sx, sy, sw, sh,
    this.x, this.y, this.width, this.height);

  // Debug overlay: outline the hit box
  if (this.gameEnv.debug) {
    this.ctx.strokeStyle = 'red';
    this.ctx.lineWidth   = 2;
    this.ctx.strokeRect(this.x, this.y, this.width, this.height);
  }
}
```

## Key Takeaway

> If a collision bug isn't obvious, draw the hit boxes. Most of the time the geometry tells you exactly what's wrong.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/debug/console" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Console Debugging</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #EF4444; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/debug/sources" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Source-Level Debugging</div></a>
</nav>
