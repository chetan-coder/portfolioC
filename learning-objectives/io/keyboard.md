---
layout: post
title: Keyboard Input
permalink: /io/keyboard
description: "Input / Output · Arrow keys, Space, WASD controls using event listeners."
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

# Keyboard Input

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #A855F7; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #A855F7; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Arrow keys, Space, WASD controls using event listeners.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #A855F7; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Testing: Key event handlers respond correctly</div>
  </div>

</div>

## What it is

Browsers fire `keydown` and `keyup` DOM events whenever the user presses or releases a key. You register handlers with `addEventListener('keydown', handler)`. Each event has a `.key` property (the human-readable key name) and `.code` (the physical key location).

## Why it matters

Keyboard input is the primary way the player drives the game. Low-latency, smooth, simultaneous-key-aware input is what separates good controls from clunky ones.

## How GateGame implements it

Player movement in Maze of Shadows uses WASD via DOM event listeners on `keydown` and `keyup`. The handler sets boolean flags (`keys.w = true`), and the game's `update()` reads those flags each frame — this is what allows holding two keys at once (e.g. move right while jumping) instead of one-input-per-frame.

## Code Example

```js
// Listener pattern: keydown sets a flag, update() reads it
const keys = {};
document.addEventListener('keydown', (e) => { keys[e.key.toLowerCase()] = true;  });
document.addEventListener('keyup',   (e) => { keys[e.key.toLowerCase()] = false; });

// In Player.update() each frame
if (keys['w']) { this.vy -= jumpForce; }
if (keys['a']) { this.x  -= speed;     }
if (keys['d']) { this.x  += speed;     }
```

## Key Takeaway

> Set flags in the event handler, *read* flags in `update()`. This decouples input timing from game-loop timing and supports simultaneous keys.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/operators/boolean-expressions" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Boolean Expressions</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #A855F7; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/io/canvas" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Canvas Rendering</div></a>
</nav>
