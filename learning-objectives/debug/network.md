---
layout: post
title: Network Debugging
permalink: /debug/network
description: "Debugging · Examine Network tab for API calls, CORS errors, response status."
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

# Network Debugging

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #EF4444; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EF4444; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Examine Network tab for API calls, CORS errors, response status.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EF4444; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Demo: Inspect fetch requests, response data, error messages</div>
  </div>

</div>

## What it is

The Network panel in DevTools shows every HTTP request your page makes — URL, method, status, request headers, response headers, request body, response body, and timing. You can replay requests, copy them as curl, and filter by type.

## Why it matters

API issues are usually invisible from the JavaScript side. A fetch might fail silently from a CORS preflight, or return a 400 because of a content-type mismatch. The Network tab shows the actual exchange so you can see what's wrong.

## How GateGame implements it

When the leaderboard fetch started failing, the Network tab revealed a CORS error: the response was missing `Access-Control-Allow-Origin`. Fixed on the backend. Another time a 400 turned out to be because the request was sent with `text/plain` instead of `application/json`. Both bugs were diagnosed entirely from the Network tab.

## Code Example

```js
// The fetch under inspection in the Network tab:
const response = await fetch('/api/leaderboard', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },  // ← critical
  body: JSON.stringify({ score, player })
});
// Network tab showed: 400 Bad Request, CORS blocked, etc.
```

## Key Takeaway

> When fetches fail, the Network tab tells you the real story. Status code, headers, payload — all visible side-by-side.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/debug/sources" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Source-Level Debugging</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #EF4444; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/debug/application" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Application Debugging</div></a>
</nav>
