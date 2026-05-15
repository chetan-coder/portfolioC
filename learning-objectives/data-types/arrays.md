---
layout: post
title: Arrays
permalink: /data-types/arrays
description: "Data Types · Game object collections and level data."
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

# Arrays

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #F97316; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #F97316; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Game object collections and level data.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #F97316; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: Array operations</div>
  </div>

</div>

## What it is

Arrays are ordered, indexed collections created with `[]`. They support a huge set of methods: `.push()`, `.pop()`, `.map()`, `.filter()`, `.forEach()`, `.find()`, and many more. Arrays can hold values of any type, including other arrays and objects.

## Why it matters

Arrays group entities so you can iterate over them. The entire level definition is fundamentally one array of game-object configs. Spline barriers are arrays of points. Dialogue button sets are arrays of options. Without arrays, every entity would need its own variable name.

## How GateGame implements it

The `this.classes` array holds every instantiable entity in the level. Each spline segment is built from an array of `[relX, relY]` coordinate pairs. The Exit Warden's dialogue options are an array of button config objects passed to `addButtons()`. The engine iterates these arrays each frame.

## Code Example

```js
// Array of coordinate pairs defining the maze path
const seg1 = spline('seg1', [
  [0.03, 0.945],
  [0.09, 0.940],
  [0.20, 0.920],
  [0.28, 0.895],
]);

// Array of game objects to instantiate
this.classes = [
  { class: Player, data: sprite_data_octopus },
  { class: Npc,    data: sprite_data_warden  },
];
```

## Key Takeaway

> Arrays are how you go from 'one of this thing' to 'a collection of these things' without inventing 50 variable names.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/data-types/booleans" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Booleans</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #F97316; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/data-types/objects" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Objects (JSON)</div></a>
</nav>
