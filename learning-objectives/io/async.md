---
layout: post
title: Asynchronous I/O
permalink: /io/async
description: "Input / Output · Use async/await or Promises for API calls."
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

# Asynchronous I/O

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #A855F7; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #A855F7; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Use async/await or Promises for API calls.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #A855F7; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: async/await or .then() chains</div>
  </div>

</div>

## What it is

Asynchronous operations don't block the main thread. JavaScript represents them with Promises, which can be consumed using `.then()` chains or the cleaner `async/await` syntax. `await` pauses an `async` function until the Promise resolves, without freezing the whole JS runtime.

## Why it matters

The game loop runs at 60 frames per second. If a network request blocked the main thread, the game would freeze whenever a request was in flight. Async I/O keeps the game responsive while requests run in the background.

## How GateGame implements it

All Leaderboard and NPC AI fetches use `async/await`. The level transition uses `requestAnimationFrame` (async via the browser) and `setTimeout` to schedule a fade-out before swapping levels — neither blocks the game loop. The player can keep moving while a leaderboard refresh runs.

## Code Example

```js
// Async transition to next level, scheduled without blocking
requestAnimationFrame(() => {
  fade.style.opacity = '1';
  setTimeout(() => {
    topGame.transitionToLevel();
  }, 800);
});

// async/await keeps the function readable
async function submitScore(score) {
  const res = await fetch('/api/leaderboard', { /* ... */ });
  return await res.json();
}
```

## Key Takeaway

> `async/await` reads like sequential code but doesn't block the game loop. The level keeps running at 60fps while the network does its thing.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/io/api" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">API Integration</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #A855F7; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/io/json-parsing" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">JSON Parsing</div></a>
</nav>
