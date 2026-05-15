---
layout: post
title: Mini-Lesson Documentation
permalink: /docs/mini-lesson
description: "Documentation · Comic / visual post with embedded runtime game demo."
hide: true
show_reading_time: true
---

<div style="margin: 8px 0 24px;">
  <a href="{{site.baseurl}}/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px; border: 1px solid rgba(255,255,255,0.15); border-radius: 6px; font-size: 0.85rem; color: inherit; transition: all 0.2s;">
    ← Back to Portfolio
  </a>
</div>

<div style="display: inline-block; background: #FACC151A; color: #FACC15; border: 1px solid #FACC1566; border-radius: 6px; padding: 4px 10px; font-size: 0.8rem; font-weight: 600; margin-bottom: 8px;">
  📝 Documentation
</div>

# Mini-Lesson Documentation

<div style="background: linear-gradient(135deg, #111827, #1F2937); border-left: 4px solid #FACC15; border-radius: 10px; padding: 16px 20px; margin: 20px 0 28px; display: grid; grid-template-columns: 1fr; gap: 12px;">

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #FACC15; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Project Evidence Required</div>
    <div style="color: #e2e8f0; line-height: 1.5;">Comic / visual post with embedded runtime game demo.</div>
  </div>

  <div>
    <div style="font-size: 0.75rem; font-weight: 700; color: #FACC15; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;">Assessment Method</div>
    <div style="color: #e2e8f0; font-family: ui-monospace, Menlo, monospace; font-size: 0.9rem;">Portfolio review: Mini-lesson in personal portfolio</div>
  </div>

</div>

## What it is

A mini-lesson is a focused, visual explanation of a single concept — usually built with diagrams, annotated screenshots, and an embedded runtime demo. The format is closer to a comic strip than a textbook: short panels, visual emphasis, and concrete examples.

## Why it matters

Most learners don't absorb dense paragraphs. A visual format with an embedded demo lets the reader *play* with the concept instead of just reading about it — which is how understanding actually sticks.

## How GateGame implements it

My portfolio's lesson pages — JS Basics, JS Variables, Networking, and Gamerunner — walk through foundational concepts with visual aids and embedded runtime demos linked from the homepage. The Class Progress section also showcases each game as a runnable demonstration of the concept it teaches.

## Code Example

```js
<!-- The portfolio homepage links to these mini-lessons -->
<a href="/code/javascript">JS Basics</a>
<a href="/game/essentials/variables">JS Variables</a>
<a href="/network/stack">Networking</a>
<a href="/gamerunner">Gamerunner</a>
```

## Key Takeaway

> Show, don't tell. A working demo embedded in the page does what three paragraphs of prose can't.

---

<nav style="display: flex; gap: 12px; flex-wrap: wrap; margin: 32px 0 16px; align-items: stretch;">
  <a href="{{site.baseurl}}/docs/comments" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">← Previous</div><div style="font-weight: 600; margin-top: 2px;">Code Comments</div></a>
  <a href="{{site.baseurl}}/" style="text-decoration: none; padding: 10px 20px; background: #FACC15; color: white; border-radius: 8px; font-weight: 700; align-self: center;">
    🏠 Home
  </a>
  <a href="{{site.baseurl}}/docs/highlights" style="text-decoration: none; padding: 10px 16px; border: 1px solid rgba(255,255,255,0.2); border-radius: 8px; color: inherit; flex: 1; min-width: 200px; text-align: right;"><div style="font-size: 0.7rem; color: #9ca3af; text-transform: uppercase; letter-spacing: 0.5px;">Next →</div><div style="font-weight: 600; margin-top: 2px;">Code Highlights</div></a>
</nav>
