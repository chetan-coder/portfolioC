---
layout: post
title: Canvas Rendering
permalink: /io/canvas
description: "Input / Output · Draw sprites, backgrounds, platforms using the Canvas API."
hide: true
show_reading_time: true
---

<div style="margin: 8px 0 24px;">
  <a href="{{site.baseurl}}/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px; border: 1px solid rgba(255,255,255,0.15); border-radius: 6px; font-size: 0.85rem; color: inherit; transition: all 0.2s;">
    ← Back to Portfolio
  </a>
</div>

<div style="display: inline-block; background: #A855F71A; color: #A855F7; border: 1px solid #A855F766; border-radius: 6px; padding: 4px 10px; font-size: 0.8rem; font-weight: 600; margin-bottom: 8px;">
  🎮 Input / Output
</div>

# Canvas Rendering

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #A855F7; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #A855F7; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Draw sprites, backgrounds, platforms using the Canvas API.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #A855F7; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: draw() method implementations</div>
  </div>

</div>

## What it is

The HTML5 `<canvas>` element gives you a 2D drawing surface controlled by JavaScript. You get the context via `canvas.getContext('2d')`, then call methods like `ctx.drawImage()`, `ctx.fillRect()`, `ctx.beginPath()`, `ctx.stroke()`. Each frame you clear and redraw.

## Why it matters

The canvas is *the* visible output of the game. Everything the player sees comes from `draw()` calls. Layer order matters — background first, then platforms, then characters, then HUD on top.

## How GateGame implements it

Each entity's `draw()` method uses `ctx.drawImage()` with source rectangle (which frame of the spritesheet) and destination rectangle (where on the canvas). Splines render via `ctx.beginPath()` + `ctx.moveTo()` + `ctx.lineTo()` + `ctx.stroke()`. When debug mode is on, `ctx.strokeRect()` outlines hit boxes for visual debugging.

## Code Example

```js
// Sprite render with source rect + destination rect
draw() {
  this.ctx.drawImage(
    this.spriteSheet,
    sx, sy, sw, sh,                            // source frame
    this.position.x, this.position.y,
    this.width, this.height                    // destination
  );
}

// Debug hitbox rendering
this.ctx.strokeStyle = 'red';
this.ctx.strokeRect(this.x, this.y, this.width, this.height);
```

## Key Takeaway

> Each frame: clear → background → platforms → characters → HUD. Order is layering; first drawn is back-most.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/io/keyboard" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Keyboard Input</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #A855F7; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/io/gameenv" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">GameEnv Configuration</div></a>
</nav>
