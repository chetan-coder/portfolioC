---
layout: post
title: JSON Parsing
permalink: /io/json-parsing
description: "Input / Output · Parse API responses (leaderboard data, AI responses)."
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

# JSON Parsing

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #A855F7; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #A855F7; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Parse API responses (leaderboard data, AI responses).</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #A855F7; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: JSON.parse(), object destructuring</div>
  </div>

</div>

## What it is

JSON (JavaScript Object Notation) is the standard text format for sending structured data over the network. `JSON.parse(str)` converts a JSON string into a JavaScript object; `response.json()` is the Promise-based version for Fetch responses. Destructuring (`const { a, b } = obj`) extracts named properties cleanly.

## Why it matters

APIs communicate in JSON. Parsing is required to use the data. Destructuring makes the parsed-data access readable instead of writing `data.scores[0].value` every time.

## How GateGame implements it

Leaderboard responses come back as JSON arrays like `[{ user: 'aarav', score: 4200 }, ...]`. `await response.json()` parses them into usable JS arrays. Destructuring extracts the top score cleanly: `const { scores } = await response.json()`. The NPC AI response is similarly parsed and destructured for `message` and `emotion` fields.

## Code Example

```js
// Parse a fetch response
const res  = await fetch('/api/leaderboard');
const data = await res.json();                   // parse JSON → JS object
const topScore = data.scores[0].value;

// Destructure for cleaner access
const { scores } = await res.json();
const [first, second, third] = scores;
```

## Key Takeaway

> `response.json()` does the parsing for you. Destructure into clean local variables instead of dot-chaining everywhere.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/io/async" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Asynchronous I/O</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #A855F7; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/docs/comments" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Code Comments</div></a>
</nav>
