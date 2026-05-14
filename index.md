---
layout: post 
title: Portfolio Home 
hide: true
show_reading_time: false
---

> Hi! My name is Chetan Tiduwar, and I strive towards becoming a skilled computer scientist, building games, tools, and experiences through code.

### Development Environment

> Coding starts with tools, explore these tools and procedures with a click.

<div style="display: flex; flex-wrap: wrap; gap: 10px;">
    <a href="https://opencodingsociety.com" style="text-decoration: none; display: inline-flex; align-items: center; gap: 8px; padding: 10px 14px; border: 1px solid #FA8072; border-radius: 6px; font-weight: 700; color: black;">
        <img src="{{ '/favicon.ico' | relative_url }}" style="width: 16px; height: 16px;">
        OCS
    </a>
    <a href="https://github.com/Open-Coding-Society/portfolio" style="text-decoration: none; display: inline-flex; align-items: center; gap: 8px; padding: 10px 14px; border: 1px solid #FFF; border-radius: 6px; font-weight: 700; color: black;">
        GitHub
    </a>
    <a href="https://vscode.dev/" style="text-decoration: none; display: inline-flex; align-items: center; gap: 8px; padding: 10px 14px; border: 1px solid #000000; border-radius: 6px; font-weight: 700; color: black;">
        VSCode.dev
    </a>
</div>

<br>

### My Lessons

<div style="display: flex; flex-wrap: wrap; gap: 10px;">
    <a href="{{site.baseurl}}/code/javascript" class="btn" style="background-color: var(--green); color: black;">
        JS Basics
    </a>
    <a href="{{site.baseurl}}/game/essentials/variables" class="btn" style="background-color: var(--blue); color: black;">
        JS Variables
    </a>
    <a href="{{site.baseurl}}/gamerunner" class="btn" style="background-color: var(--warn); color: black;">
        Gamerunner
    </a>
    <a href="{{site.baseurl}}/network/stack" class="btn" style="background-color: var(--orange); color: black;">
        Networking
    </a>
</div>

<br>

### Class Progress

<div style="display: flex; flex-wrap: wrap; gap: 10px;">
    <a href="{{site.baseurl}}/snake" class="btn" style="color: black;">Snake</a>

    <a href="{{site.baseurl}}/gamify/parallax" class="btn" style="background-color: var(--green); color: black;">
        Fish
    </a>

    <a href="{{site.baseurl}}/gamify" class="btn" style="background-color: var(--teal); color: black;">
        Gamify
    </a>

    <a href="{{site.baseurl}}/cs-pathway" class="btn" style="background-color: var(--orange); color: black;">
        CS Pathway
    </a>

    <a href="https://gates.opencodingsociety.com/gamify/gategamev2"
       class="btn"
       style="background-color: #8B5CF6; color: black;">
        Gate Game
    </a>
</div>

<br>

### My Projects

<div style="display: flex; flex-wrap: wrap; gap: 10px;">
    <a href="{{site.baseurl}}/exam-predictor" class="btn" style="background-color: var(--blue); color: black;">
        Exam Predictor
    </a>
    <a href="{{site.baseurl}}/grade-predictor" class="btn" style="background-color: var(--green); color: black;">
        Grade Predictor
    </a>
    <a href="{{site.baseurl}}/study-tracker" class="btn" style="background-color: var(--teal); color: black;">
        Study Tracker
    </a>
    <a href="{{site.baseurl}}/score-predictor" class="btn" style="background-color: var(--orange); color: black;">
        Score Predictor
    </a>
</div>

<br><br><br>

<div markdown="0">
<h3>About Gate Game 🗼</h3>

<blockquote>
Gate Game is a multi-level platformer game built with JavaScript using an object-oriented game engine. I contributed by building the <strong>Maze of Shadows</strong> sublevel.
</blockquote>

<pre><code>
{ class: Player, data: sprite_data_octopus },
{ class: Npc, data: sprite_data_shadow },
</code></pre>

<pre><code>
function spline(id, points) {
  return {
    id,
    splinePoints: points.map(([px, py]) => ({
      x: Math.round(px * width),
      y: Math.round(py * height)
    }))
  };
}
</code></pre>

<pre><code>
requestAnimationFrame(() => {
  setTimeout(() => {
    topGame.transitionToLevel();
  }, 800);
});
</code></pre>

</div>

<div style="display: flex; flex-wrap: wrap; gap: 14px; margin-top: 10px;">

    <a href="{{site.baseurl}}/snake"
       class="btn"
       style="background: linear-gradient(135deg, #111827, #1F2937); color: black;">
       🐍 Snake
    </a>

    <a href="{{site.baseurl}}/gamify/parallax"
       class="btn"
       style="background: linear-gradient(135deg, #064E3B, #10B981); color: black;">
       🐟 Fish
    </a>

    <a href="{{site.baseurl}}/gamify"
       class="btn"
       style="background: linear-gradient(135deg, #0F172A, #14B8A6); color: black;">
       🎮 Gate Game
    </a>

    <a href="{{site.baseurl}}/cs-pathway"
       class="btn"
       style="background: linear-gradient(135deg, #7C2D12, #F97316); color: black;">
       🚀 CS Pathway
    </a>

    <a href="https://gates.opencodingsociety.com/gamify/gategamev2"
       class="btn"
       style="background: linear-gradient(135deg, #1E1B4B, #7C3AED); color: black;">
       🗼 Gate Game
    </a>

</div>