---
layout: post
title: Instantiation & Objects
permalink: /oop/instantiation-objects
description: "Object-Oriented Programming · Instantiate game objects in GameLevel configuration."
hide: true
show_reading_time: true
---

<div style="margin: 8px 0 24px;">
  <a href="{{site.baseurl}}/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px; border: 1px solid rgba(255,255,255,0.15); border-radius: 6px; font-size: 0.85rem; color: inherit; transition: all 0.2s;">
    ← Back to Portfolio
  </a>
</div>

<div style="display: inline-block; background: #3B82F61A; color: #3B82F6; border: 1px solid #3B82F666; border-radius: 6px; padding: 4px 10px; font-size: 0.8rem; font-weight: 600; margin-bottom: 8px;">
  🏛️ Object-Oriented Programming
</div>

# Instantiation & Objects

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #3B82F6; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #3B82F6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Instantiate game objects in GameLevel configuration.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #3B82F6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: GameLevel setup objects</div>
  </div>

</div>

## What it is

Instantiation is the act of creating a real, running instance from a class blueprint — done via the `new` keyword. Object literals (`{ key: value, ... }`) are JavaScript's most compact way to bundle configuration data, and they're what we pass to constructors to customize each instance.

## Why it matters

A class is just a blueprint until something instantiates it. In game development, instantiation is where the abstract becomes concrete — where a `Player` class definition becomes the actual octopus on screen. Doing it via object literals (data-driven design) means designers can change the game by editing data instead of code.

## How GateGame implements it

In `GameLevelMazeSub`, I built a `this.classes` array of object literals. Each entry pairs a class with its data: `{ class: Player, data: sprite_data_octopus }`. The engine walks this array and instantiates each entry at level load. To add a new enemy, I append one more object literal — no engine changes required.

## Code Example

```js
this.classes = [
  { class: GameEnvBackground, data: image_data_cave   },
  { class: Player,            data: sprite_data_octopus },
  { class: SplineBarrier,     data: seg1               },
  { class: SplineBarrier,     data: seg2               },
  { class: Coin,              data: sprite_data_coin   },
  { class: Npc,               data: sprite_data_shadow },
  { class: Npc,               data: sprite_data_warden },
];
```

## Key Takeaway

> Object literals + an array of `{class, data}` pairs = a level you can redesign by editing data, not engine code.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/oop/methods-parameters" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Methods & Parameters</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #3B82F6; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/oop/inheritance" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Inheritance (Basic)</div></a>
</nav>
