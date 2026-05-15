---
layout: post
title: Integration Testing
permalink: /test/integration
description: "Testing & Verification · Test API integration (Leaderboard, NPC AI) with live backend."
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

# Integration Testing

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #EC4899; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EC4899; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Test API integration (Leaderboard, NPC AI) with live backend.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EC4899; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Demo: Successful score saving and AI responses</div>
  </div>

</div>

## What it is

Integration testing verifies that separate subsystems work together end-to-end. The game alone might work; the API alone might work; the integration tests whether they cooperate correctly under real conditions.

## Why it matters

Each piece can pass its own unit tests and still fail when combined. Contract mismatches (the API expects `score`, the game sends `points`) are the classic integration bug. Testing against the live backend is the only way to catch them before the player does.

## How GateGame implements it

Ran the full flow: complete the maze → submit score to live Leaderboard API → confirm 200 response → reload leaderboard → see the score in the list. Also tested NPC dialogue against the live AI backend with a variety of inputs to make sure responses arrived within a reasonable timeout.

## Code Example

```js
// Integration test plan:
//   1. Play level to completion (live game)
//   2. POST score to /api/leaderboard (live backend)
//   3. Confirm 200 response status
//   4. GET /api/leaderboard
//   5. Verify submitted score appears in list
```

## Key Takeaway

> Test against the live backend, not a mock. Mocks lie. The network is where the contract really gets tested.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/test/gameplay" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Gameplay Testing</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #EC4899; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/test/error-handling" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">API Error Handling</div></a>
</nav>
