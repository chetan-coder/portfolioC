---
layout: post
title: Booleans
permalink: /data-types/booleans
description: "Data Types · Flags such as isJumping, isPaused, isVulnerable."
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

# Booleans

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #F97316; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #F97316; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Flags such as isJumping, isPaused, isVulnerable.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #F97316; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: Boolean logic</div>
  </div>

</div>

## What it is

A boolean is a `true` or `false` value. JavaScript also treats many other values as truthy or falsy when used in conditionals — `0`, `''`, `null`, `undefined`, and `NaN` are falsy; everything else is truthy.

## Why it matters

Booleans are the on/off switches that drive game state. Is the dialogue open? Is the player paused? Is this barrier visible right now? Each is a boolean, and combining them lets you express any state machine.

## How GateGame implements it

SplineBarriers have a `visible: true` boolean that controls whether they render. The dialogue system tracks `isDialogueOpen()` to decide whether to pause input. Dialogue buttons mark one option as `primary: true` to style it differently. The 'Step Through' callback inside the Exit Warden uses booleans to gate the level transition.

## Code Example

```js
// Boolean flags throughout the level config
return {
  id,
  splinePoints: [...],
  visible: true,                 // ← shows on canvas
  color: '#8B4513',
  lineWidth: 22,
};

// Dialogue button with a boolean style flag
{ text: "Step Through", primary: true, action: () => { /*...*/ } }
```

## Key Takeaway

> Booleans turn complex game state into readable English: `if (this.isOnGround && !this.isJumping)`. Use them liberally.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/data-types/strings" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Strings</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #F97316; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/data-types/arrays" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Arrays</div></a>
</nav>
