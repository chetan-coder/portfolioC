---
layout: post
title: API Integration
permalink: /io/api
description: "Input / Output · Implement Leaderboard API (POST/GET scores)."
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

# API Integration

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #A855F7; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #A855F7; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Implement Leaderboard API (POST/GET scores).</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #A855F7; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: Fetch calls with error handling</div>
  </div>

</div>

## What it is

The Fetch API lets JavaScript make HTTP requests to remote servers. `fetch(url, options)` returns a Promise that resolves to a Response object. POST requests typically include a JSON body; GET requests append parameters to the URL.

## Why it matters

Modern games are connected. Leaderboards, save state, multiplayer, AI services — they all live on servers. Without API integration, the game can't share data with anything outside the browser tab.

## How GateGame implements it

The Leaderboard API uses POST to submit scores at level completion and GET to retrieve the top 10 for display. Every fetch is wrapped in a try/catch so a network failure doesn't crash the game. The NPC AI integration uses the same pattern — POST the player's input, receive a generated dialogue response.

## Code Example

```js
try {
  const response = await fetch('/api/leaderboard', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ score, player })
  });
  const data = await response.json();
  renderLeaderboard(data);
} catch (error) {
  console.error('Leaderboard API error:', error);
  showFallbackUI();
}
```

## Key Takeaway

> Fetch + JSON + try/catch is the canonical pattern. Always wrap in try/catch — the network *will* fail eventually.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/io/gameenv" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">GameEnv Configuration</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #A855F7; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/io/async" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Asynchronous I/O</div></a>
</nav>
