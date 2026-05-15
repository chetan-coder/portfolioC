---
layout: post
title: Method Overriding
permalink: /oop/method-overriding
description: "Object-Oriented Programming · Override parent methods (update(), draw(), handleCollision())."
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

# Method Overriding

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #3B82F6; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #3B82F6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Override parent methods (update(), draw(), handleCollision()).</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #3B82F6; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Code review: Polymorphic implementations</div>
  </div>

</div>

## What it is

Method overriding happens when a child class defines a method with the same name as one in the parent class. The child's version replaces the parent's — but the child can still invoke the parent's version via `super.methodName()` if it wants to augment rather than replace.

## Why it matters

Overriding is how subclasses customize behavior without rewriting everything. The base `update()` handles generic physics, but the `Player.update()` override adds keyboard reading on top. Same method name, different behavior per class — that's polymorphism, and it's what makes object-oriented design powerful.

## How GateGame implements it

In Maze of Shadows, the `Player` overrides `update()` to read WASD input before delegating to the base physics. The NPC classes override `interact()` to trigger their own dialogue trees — Exit Warden offers a level transition, Shadow NPC offers maze hints. Each `draw()` override handles sprite-specific rendering like horizontal flipping based on facing direction.

## Code Example

```js
// Exit Warden overrides interact() with its own dialogue logic
interact: function() {
  this.dialogueSystem.showDialogue(
    "You followed the path all the way here. Are you ready to move on?",
    "Exit Warden",
    this.spriteData.src
  );
  this.dialogueSystem.addButtons([
    { text: "Step Through", primary: true, action: () => { /* transition */ } },
    { text: "Not yet",      action: () => this.dialogueSystem.closeDialogue() }
  ]);
}
```

## Key Takeaway

> Same method name, different behavior per subclass. Polymorphism is how one engine handles many entity types without an `if/else` chain.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/oop/inheritance" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Inheritance (Basic)</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #3B82F6; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/oop/constructor-chaining" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Constructor Chaining</div></a>
</nav>
