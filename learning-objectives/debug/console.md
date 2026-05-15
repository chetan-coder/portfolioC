---
layout: post
title: Console Debugging
permalink: /debug/console
description: "Debugging · Use console.log to track game state, variables, method calls."
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

# Console Debugging

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #EF4444; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EF4444; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Use console.log to track game state, variables, method calls.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EF4444; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: Strategic logging in update/collision methods</div>
  </div>

</div>

## What it is

`console.log()`, `console.warn()`, `console.error()`, and `console.table()` print messages and values to the browser's developer console. Logs can include any JavaScript value — objects, arrays, even DOM nodes — and the console renders them interactively.

## Why it matters

This is the fastest way to see what your code is doing without pausing it. When a value seems wrong, a `console.log` at the right place can reveal the bug in seconds.

## How GateGame implements it

During development I sprinkled `console.log("Initializing GameLevelMazeSub...")` calls to confirm level-load timing. NPC `interact()` methods log when they fire to verify the proximity check is working. Logging is guarded behind a debug flag so production builds stay quiet.

## Code Example

```js
console.log("Initializing GameLevelMazeSub...");
console.log("player pos", this.player.x, this.player.y);

// Guarded so production stays quiet
if (gameEnv.debug) {
  console.log('collision', other.constructor.name, direction);
}
```

## Key Takeaway

> Log generously during dev, guard it behind a flag for production. A well-placed `console.log` is faster than any debugger.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/docs/highlights" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Code Highlights</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #EF4444; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/debug/hitbox" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Hit Box Visualization</div></a>
</nav>
