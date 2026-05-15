---
layout: post
title: Gameplay Testing
permalink: /test/gameplay
description: "Testing & Verification · Test level completion, character interactions, collision detection."
hide: true
show_reading_time: true
---

<div style="margin: 8px 0 24px;">
  <a href="{{site.baseurl}}/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px; border: 1px solid rgba(255,255,255,0.15); border-radius: 6px; font-size: 0.85rem; color: inherit; transition: all 0.2s;">
    ← Back to Portfolio
  </a>
</div>

<div style="display: inline-block; background: #EC48991A; color: #EC4899; border: 1px solid #EC489966; border-radius: 6px; padding: 4px 10px; font-size: 0.8rem; font-weight: 600; margin-bottom: 8px;">
  ✅ Testing & Verification
</div>

# Gameplay Testing

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #EC4899; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EC4899; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Test level completion, character interactions, collision detection.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #EC4899; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Live demo: Play through level without critical bugs</div>
  </div>

</div>

## What it is

Gameplay testing is manually playing the game from start to finish, looking for issues that an automated test can't catch — collision misalignment, control responsiveness, pacing, fairness. It's the test that requires a human in the loop.

## Why it matters

Automated tests verify code behavior; gameplay testing verifies the *experience*. Some bugs are only obvious when you *feel* them — a jump that feels floaty, a hit box that connects too easily, a transition that lags. Only playing catches these.

## How GateGame implements it

After every meaningful change I played the Maze of Shadows level start-to-finish. I verified the octopus can traverse the entire winding spline path without clipping through walls, that each NPC's dialogue triggers on the right proximity, that the Exit Warden's transition fires after picking 'Step Through', and that 'Not yet' cleanly closes the dialogue.

## Code Example

```js
// Gameplay test checklist (run after every change):
//   ☑ player walks full maze path without clipping
//   ☑ Shadow NPC dialogue triggers on collision
//   ☑ Lantern NPC dialogue triggers on collision
//   ☑ Exit Warden offers Step Through / Not yet
//   ☑ Step Through fires fade + level transition
//   ☑ Not yet closes dialogue cleanly
```

## Key Takeaway

> A short checklist run after every change catches the regressions that automated tests miss. It also forces you to play your own game, which is its own kind of feedback.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/debug/element" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Element Inspection</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #EC4899; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/test/integration" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Integration Testing</div></a>
</nav>
