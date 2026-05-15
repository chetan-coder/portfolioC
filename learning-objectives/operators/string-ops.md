---
layout: post
title: String Operations
permalink: /operators/string-ops
description: "Operators · Path concatenation and on-screen text display."
hide: true
show_reading_time: true
---

<div style="margin: 8px 0 24px;">
  <a href="{{site.baseurl}}/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px; border: 1px solid rgba(255,255,255,0.15); border-radius: 6px; font-size: 0.85rem; color: inherit; transition: all 0.2s;">
    ← Back to Portfolio
  </a>
</div>

<div style="display: inline-block; background: #14B8A61A; color: #14B8A6; border: 1px solid #14B8A666; border-radius: 6px; padding: 4px 10px; font-size: 0.8rem; font-weight: 600; margin-bottom: 8px;">
  ➕ Operators
</div>

# String Operations

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #14B8A6; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #14B8A6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Path concatenation and on-screen text display.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #14B8A6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: Template literals, concatenation</div>
  </div>

</div>

## What it is

Strings can be combined with `+` (concatenation) or built with template literals using backticks and `${expression}` placeholders. Template literals are usually cleaner because they let you embed variables and expressions inline without breaking the string apart.

## Why it matters

Game text is dynamic. Sprite paths depend on frame indexes; HUD text depends on score; dialogue often interpolates the player's name. String operations let you build these dynamic strings cleanly.

## How GateGame implements it

Asset path concatenation builds image URLs from a base directory plus a filename. Template literals would build HUD text like `` `Score: ${score}` `` or dialogue like `` `Welcome, ${playerName}!` ``. The dialogue system itself joins strings of speaker name + body text for display.

## Code Example

```js
// Concatenation
const baseUrl = '/assets/sprites';
const path = baseUrl + '/octopus.png';

// Template literal (preferred for interpolation)
const hud  = `Score: ${score}  Lives: ${lives}`;
const line = `Welcome, ${playerName}! The maze awaits.`;
```

## Key Takeaway

> Use template literals (`` `${...}` ``) when interpolating; reserve `+` concatenation for joining two static halves of a path or label.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/operators/mathematical" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Mathematical Operators</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #14B8A6; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/operators/boolean-expressions" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Boolean Expressions</div></a>
</nav>
