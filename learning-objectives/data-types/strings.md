---
layout: post
title: Strings
permalink: /data-types/strings
description: "Data Types · Character names, sprite paths, game states."
hide: true
show_reading_time: true
---

<div style="margin: 8px 0 24px;">
  <a href="{{site.baseurl}}/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px; border: 1px solid rgba(255,255,255,0.15); border-radius: 6px; font-size: 0.85rem; color: inherit; transition: all 0.2s;">
    ← Back to Portfolio
  </a>
</div>

<div style="display: inline-block; background: #F973161A; color: #F97316; border: 1px solid #F9731666; border-radius: 6px; padding: 4px 10px; font-size: 0.8rem; font-weight: 600; margin-bottom: 8px;">
  🧮 Data Types
</div>

# Strings

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #F97316; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #F97316; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Character names, sprite paths, game states.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #F97316; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: String manipulation</div>
  </div>

</div>

## What it is

Strings are sequences of characters wrapped in single quotes (`'...'`), double quotes (`"..."`), or backticks (`` `...` `` for template literals). They support concatenation with `+`, interpolation inside template literals, and a rich set of methods like `.split()`, `.replace()`, `.toUpperCase()`.

## Why it matters

Strings label every named thing in the game — file paths to assets, dialogue text shown to the player, state machine values, NPC names. Without strings, you couldn't load a sprite or display a single line of dialogue.

## How GateGame implements it

Sprite paths like `'assets/sprites/octopus.png'` tell the loader which image to fetch. Dialogue strings carry the actual words the player reads: `"You followed the path all the way here. Are you ready to move on?"`. Spline IDs like `'seg1'` and `'seg2'` identify each segment of the maze path. Color values like `'#8B4513'` are strings the canvas API parses.

## Code Example

```js
// String IDs, paths, dialogue, color hex
const id     = 'seg1';
const color  = '#8B4513';
const path   = 'assets/sprites/octopus.png';
const greet  = "You followed the path all the way here.";
```

## Key Takeaway

> Strings name and describe everything the game knows about. Template literals (backticks) make dynamic strings clean: `` `${name}: ${score}` ``.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/data-types/numbers" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Numbers</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #F97316; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/data-types/booleans" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Booleans</div></a>
</nav>
