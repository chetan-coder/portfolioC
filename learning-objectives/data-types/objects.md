---
layout: post
title: Objects (JSON)
permalink: /data-types/objects
description: "Data Types · Configuration objects and sprite data."
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

# Objects (JSON)

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #F97316; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #F97316; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Configuration objects and sprite data.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #F97316; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: Object literals</div>
  </div>

</div>

## What it is

Objects are unordered collections of key-value pairs created with `{}`. They're JavaScript's most flexible data structure — properties can be added, removed, or reassigned at runtime. Object literals look like JSON and are the natural way to express configuration.

## Why it matters

Object literals are how you turn game design into data. Every sprite, every NPC, every barrier is described by an object with a few well-known fields. The engine reads these objects and acts on them. Change the data, change the game.

## How GateGame implements it

Every entity in the level is configured by an object literal. The `spline()` helper returns one. Sprite data like `sprite_data_octopus` is an object. The `this.classes` entries each pair a class reference with a data object. Dialogue buttons are objects with `text`, `primary`, and `action` fields.

## Code Example

```js
// Object literal returned from spline()
return {
  id,
  splinePoints: [...],
  visible: true,
  color: '#8B4513',
  lineWidth: 22,
};

// Object literal for a dialogue button
{ text: "Step Through", primary: true, action: () => { /*...*/ } }
```

## Key Takeaway

> Object literals are the syntax of configuration. If a piece of your game has more than two adjustable knobs, it's probably an object.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/data-types/arrays" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Arrays</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #F97316; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/operators/mathematical" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Mathematical Operators</div></a>
</nav>
