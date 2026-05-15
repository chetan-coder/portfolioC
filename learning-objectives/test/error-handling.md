---
layout: post
title: API Error Handling
permalink: /test/error-handling
description: "Testing & Verification · Try/catch blocks for API calls, network error handling."
hide: true
show_reading_time: true
---

<div style="margin: 8px 0 24px;">
  <a href="{{site.baseurl}}/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px; border: 1px solid rgba(255,255,255,0.15); border-radius: 6px; font-size: 0.85rem; color: inherit; transition: all 0.2s;">
    ← Back to Portfolio
  </a>
</div>

<div style="display: inline-block; background: #EC48991A; color: #EC4899; border: 1px solid #EC489966; border-radius: 6px; padding: 4px 10px; font-size: 0.8rem; font-weight: 600; margin-bottom: 8px;">
  ✅ Testing & Verification
</div>

# API Error Handling

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #EC4899; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EC4899; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Try/catch blocks for API calls, network error handling.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EC4899; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: Error handling for fetch failures</div>
  </div>

</div>

## What it is

Error handling is the defensive code that catches failures and recovers gracefully. In JavaScript, `try/catch` wraps risky code; `.catch()` handles rejected Promises; `if (!response.ok)` checks for HTTP error statuses (since fetch only rejects on network failures, not 4xx/5xx responses).

## Why it matters

Networks fail. APIs go down. Wifi cuts out. Without error handling, any of these crashes the game. With error handling, the game shows a friendly message and keeps running.

## How GateGame implements it

Every fetch is wrapped in `try/catch`. On error, the leaderboard shows 'Couldn't connect — try again later' instead of throwing. The NPC AI falls back to a canned response if the request times out. I tested this by killing wifi mid-fetch and confirming the game stayed playable.

## Code Example

```js
try {
  const response = await fetch('/api/leaderboard', {
    method: 'POST',
    body: JSON.stringify({ score, player })
  });
  if (!response.ok) {
    throw new Error(`HTTP ${response.status}`);
  }
  const data = await response.json();
  renderLeaderboard(data);
} catch (error) {
  console.error('Leaderboard API error:', error);
  showOfflineFallback();  // ← game stays playable
}
```

## Key Takeaway

> Every fetch goes inside `try/catch`. Plan for failure — the network *will* let you down eventually.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/test/integration" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Integration Testing</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #EC4899; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <div style="flex: 1; min-width: 200px;"></div>
</nav>
