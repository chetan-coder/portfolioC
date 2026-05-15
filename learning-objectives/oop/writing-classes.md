---
layout: post
title: Writing Classes
permalink: /oop/writing-classes
description: "Object-Oriented Programming · Create minimum 2 custom character classes extending base classes."
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

# Writing Classes

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #3B82F6; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #3B82F6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Create minimum 2 custom character classes extending base classes.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #3B82F6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: Player.js, NPC.js, Enemy.js</div>
  </div>

</div>

## What it is

A class in JavaScript is a blueprint for creating objects with shared state and behavior. ES6 introduced the `class` keyword, which provides a clean syntax for defining constructors, instance properties, and methods. Every object created from a class is called an *instance*.

## Why it matters

In a game you often have many entities of the same type — multiple enemies, multiple platforms, multiple NPCs. Without classes you would copy-paste the same setup code dozens of times. Classes let you write the shared logic once and stamp out instances cheaply.

## How GateGame implements it

In the Maze of Shadows sublevel, I worked with three custom classes — `Player`, `Npc`, and `SplineBarrier` — each extending a base engine class. Each class encapsulates its sprite data, animation frames, and behavior in one file. The `GameLevelMazeSub` class itself extends `GameLevel`, giving us a clean hierarchy from level down to individual entity. This satisfies the 2+ custom classes requirement with three concrete implementations.

## Code Example

```js
// Three custom classes instantiated in GameLevelMazeSub
{ class: Player, data: sprite_data_octopus },
{ class: Npc,    data: sprite_data_shadow  },
{ class: Npc,    data: sprite_data_lantern },
{ class: SplineBarrier, data: seg1 },
```

## Key Takeaway

> Classes turn repetitive setup into a reusable pattern. Three custom classes in this level → every new enemy is one small subclass away.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <div style="flex: 1; min-width: 200px;"></div>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #3B82F6; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/oop/methods-parameters" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Methods & Parameters</div></a>
</nav>
