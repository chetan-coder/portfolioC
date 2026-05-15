---
layout: post
title: Source-Level Debugging
permalink: /debug/sources
description: "Debugging · Set breakpoints in DevTools, step through code execution."
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

# Source-Level Debugging

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #EF4444; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EF4444; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Set breakpoints in DevTools, step through code execution.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EF4444; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Demo: Use Sources tab to pause and inspect code flow</div>
  </div>

</div>

## What it is

The Sources panel in Chrome DevTools shows your JavaScript files. Click any line number to set a breakpoint — execution pauses there, and you can step line-by-line, inspect variables, evaluate expressions, and trace the call stack.

## Why it matters

Some bugs require pausing at the exact moment a value changes. `console.log` only tells you what a value was at logging time; the debugger lets you walk through the steps that led there.

## How GateGame implements it

I set a breakpoint inside the Exit Warden's `interact()` to step through dialogue invocation — confirmed the right callback was firing on 'Step Through' but not on 'Not yet'. Stepping into `addButtons()` revealed the issue was in the button binding, not in the dialogue logic itself.

## Code Example

```js
// Sources panel breakpoint set on this line:
this.dialogueSystem.addButtons([
  { text: "Step Through", primary: true, action: () => { /* ... */ } },
  { text: "Not yet",      action: () => this.dialogueSystem.closeDialogue() }
]);
// Execution pauses here, then F10 steps line by line
```

## Key Takeaway

> Breakpoints + step-over (F10) + step-into (F11) is the precision toolkit. Use them when `console.log` can't tell you *when* a value changed.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/debug/hitbox" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Hit Box Visualization</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #EF4444; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/debug/network" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Network Debugging</div></a>
</nav>
