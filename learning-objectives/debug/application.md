---
layout: post
title: Application Debugging
permalink: /debug/application
description: "Debugging · Examine cookies, localStorage, session data for login/state."
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

# Application Debugging

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #EF4444; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EF4444; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Examine cookies, localStorage, session data for login/state.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EF4444; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Demo: Application tab inspection of stored data</div>
  </div>

</div>

## What it is

The Application panel in DevTools inspects all client-side storage: cookies, `localStorage`, `sessionStorage`, IndexedDB, service workers, and cached resources. Each entry is shown as a key-value table you can edit live.

## Why it matters

Bugs involving persistent state (login sessions, saved settings, cached scores) require looking at the actual stored values. The Application tab lets you confirm or invalidate hypotheses about what's stored where.

## How GateGame implements it

Used the Application tab to verify the OCS session cookie was set after login, confirm the leaderboard's local-cache entry was being updated after each score submission, and clear stale localStorage entries while testing edge cases.

## Code Example

```js
// Code that writes to localStorage (verified in Application tab):
localStorage.setItem('lastScore', JSON.stringify({
  player: 'aarav',
  score: 4200,
  ts: Date.now()
}));

// Application tab → Local Storage → your-domain shows the entry
```

## Key Takeaway

> When state seems wrong, *look* at the state. The Application tab is the truth source for everything client-stored.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/debug/network" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Network Debugging</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #EF4444; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/debug/element" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Element Inspection</div></a>
</nav>
