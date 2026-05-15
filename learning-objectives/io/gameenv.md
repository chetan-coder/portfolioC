---
layout: post
title: GameEnv Configuration
permalink: /io/gameenv
description: "Input / Output · Set canvas size, difficulty levels, game settings."
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

# GameEnv Configuration

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #A855F7; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #A855F7; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Set canvas size, difficulty levels, game settings.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #A855F7; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: GameEnv.create() and GameSetup.js</div>
  </div>

</div>

## What it is

`GameEnv` is the engine's central configuration object. It holds the canvas reference, dimensions, gravity, difficulty settings, and a debug flag. Every game object holds a reference to it via the `gameEnv` parameter passed through `super()`.

## Why it matters

Centralizing configuration means one edit changes the whole game's behavior. Without a central env, every class would need its own copy of constants like canvas width, and changing the difficulty would require touching dozens of files.

## How GateGame implements it

The `GameLevelMazeSub` constructor receives `gameEnv` and forwards it to `super(gameEnv)` so the base level can bind it. Every entity in `this.classes` receives the same `gameEnv` when instantiated. Inside entities, code like `this.gameEnv.canvas.width` reads the live canvas size, so layouts scale automatically if the canvas is resized.

## Code Example

```js
class GameLevelMazeSub extends GameLevel {
  constructor(gameEnv) {
    super(gameEnv);                  // forward gameEnv to base
    const width  = gameEnv.canvas.width;   // read canvas dims
    const height = gameEnv.canvas.height;
    // ... use width/height in spline() calls
  }
}
```

## Key Takeaway

> One env object, threaded through every constructor via `super(data, gameEnv)`, gives the whole game a single source of truth for configuration.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/io/canvas" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Canvas Rendering</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #A855F7; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/io/api" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">API Integration</div></a>
</nav>
