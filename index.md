---
layout: post 
title: Portfolio Home 
hide: true
show_reading_time: false
---

> Hi! My name is Chetan Tiduwar, and I strive towards becoming a skilled computer scientist, building games, tools, and experiences through code.

# 🎮 Gate Game Runner

> Play the live Gate Game directly from my portfolio homepage.

<div style="margin-top:20px; margin-bottom:30px; border-radius:16px; overflow:hidden; border:3px solid #7C3AED; box-shadow:0 0 20px rgba(124,58,237,0.4);">
<iframe 
    src="https://gates.opencodingsociety.com/gamify/gategamev2"
    width="100%" 
    height="700"
    frameborder="0"
    allowfullscreen
    style="background:black;">
</iframe>
</div>

<div style="display:flex; gap:12px; flex-wrap:wrap; margin-bottom:30px;">
    <a href="https://gates.opencodingsociety.com/gamify/gategamev2"
       class="btn"
       style="background:#7C3AED; color:black; font-weight:bold;">
       ▶ Launch Fullscreen Game
    </a>

    <a href="https://github.com/Phantom-deploy/pagesr"
       class="btn"
       style="background:#22C55E; color:black; font-weight:bold;">
       💻 Source Code
    </a>
</div>

---

## Development Environment

> Coding starts with tools. Explore these tools and procedures with a click.

<div style="display: flex; flex-wrap: wrap; gap: 10px;">

<a href="https://opencodingsociety.com"
   class="btn"
   style="background-color:#FA8072; color:black;">
   OCS
</a>

<a href="https://github.com/Open-Coding-Society/portfolio"
   class="btn"
   style="background-color:#D1D5DB; color:black;">
   GitHub
</a>

<a href="https://vscode.dev/"
   class="btn"
   style="background-color:#007ACC; color:black;">
   VSCode.dev
</a>

</div>

<br>

## My Lessons

> Foundations in Tech are essential. Click to see some of my lesson creations.

<div style="display: flex; flex-wrap: wrap; gap: 10px;">

<a href="{{site.baseurl}}/code/javascript"
   class="btn"
   style="background-color: var(--green); color:black;">
   JS Basics
</a>

<a href="{{site.baseurl}}/game/essentials/variables"
   class="btn"
   style="background-color: var(--blue); color:black;">
   JS Variables
</a>

<a href="{{site.baseurl}}/gamerunner"
   class="btn"
   style="background-color: var(--warn); color:black;">
   Gamerunner
</a>

<a href="{{site.baseurl}}/network/stack"
   class="btn"
   style="background-color: var(--orange); color:black;">
   Networking
</a>

</div>

<br>

## Class Progress

> Here is my game progress through coding.

<div style="display: flex; flex-wrap: wrap; gap: 10px;">

<a href="{{site.baseurl}}/snake"
   class="btn"
   style="color:black;">
   Snake
</a>

<a href="{{site.baseurl}}/gamify/parallax"
   class="btn"
   style="background-color: var(--green); color:black;">
   Fish
</a>

<a href="{{site.baseurl}}/gamify"
   class="btn"
   style="background-color: var(--teal); color:black;">
   Gamify
</a>

<a href="{{site.baseurl}}/cs-pathway"
   class="btn"
   style="background-color: var(--orange); color:black;">
   CS Pathway
</a>

<a href="https://gates.opencodingsociety.com/gamify/gategamev2"
   class="btn"
   style="background-color:#8B5CF6; color:black;">
   Gate Game
</a>

</div>

<br>

# About Gate Game 🗼

Gate Game is a multi-level platformer game built with JavaScript using an object-oriented game engine. I contributed by building multiple mechanics, debugging systems, and game logic integrations throughout the project.

---

# Part 4: Debugging With DevTools

Once the game was running, things still broke — just silently. The browser's DevTools became my main diagnostic tool.

## Console — Reading Errors

| Error | Meaning |
|---|---|
| 404 | Wrong file path or file doesn't exist |
| ERR_CONNECTION_REFUSED | Server is offline |
| CORS policy blocked | Server rejected a cross-origin request |
| User initialization failed (non-critical) | Auth failed but game still runs |

The CORS errors came from the game on `gates.opencodingsociety.com` calling `flask.opencodingsociety.com/api/id`. Different subdomains, and Flask wasn't configured to allow it. Once I understood that, I stopped trying to fix it in game code.

---

## Application Panel — Game State

The Application tab shows what the game is storing in localStorage.

```js
gategame_player_name → Aryan
escaperoom_coinsCollect... → 16
```

If data wasn't loading right, I could check here to see what was actually stored versus what the code expected.

---

# Part 5: The Group Game — 3-Level Slime Escape

My team built a complete three-level game on the shared class game engine. You play as a slime trying to reach the sea.

| Version | Link | What It Is |
|---|---|---|
| Standalone | pages.opencodingsociety.com/gategame | Original self-contained build |
| Platform | gategame-integration | Integrated into the shared Gamify engine |

Getting the standalone game working was one challenge. Getting it running inside the shared platform was harder because exports had to match the engine API perfectly.

---

## Level 1: Cannonball Dodge

Cannonballs fire from the right. Use W/S to dodge.

```js
if (playerHitbox.overlaps(cannonball)) {
    player.x = 0;
} else {
    player.x += 300;
}
```

A single conditional controlled the entire mechanic.

---

## Level 2: Escape Room Maze

Navigate a maze with an NPC guide.

```js
barriers.forEach(b => this.classes.push({
    class: Barrier,
    data: b
}));
```

The maze is entirely data-driven.

---

## Level 3: Zone Catch

Players move into safe colored zones before the timer expires.

```js
if (getPixelColor(player) === safeColor) {
    playerSafe = true;
}

if (currentRound >= 6) {
    showGoldenGate();
}
```

This level combined loops, conditionals, pixel scanning, and boolean state management.

---

# Part 6: CS111 Concepts — How They Showed Up in Game Code

| Concept | In Class | In the Game |
|---|---|---|
| Variables | Store a value | playerX, SCALE_FACTOR |
| Data Types | String, Number, Boolean | Positions, flags, configs |
| Conditionals | if/else | Hit detection |
| Loops | for, forEach | Game loop |
| Arrays | Lists | Game object arrays |
| Objects | Key-value data | Config objects |
| Classes | Blueprints | Level classes |
| Boolean Flags | True/False state | playerSafe |
| Functions | Reusable logic | launchCannonball() |

The thing that made it click: every mechanic in the game is just a CS concept applied to a specific problem.

---

# Boolean State Management

```js
let playerSafe     = false;
let timerRunning   = true;
let goldenGateOpen = false;
let gameOver       = false;

if (!playerSafe && timerExpired) {
    gameOver = true;
}

if (currentRound >= 6) {
    goldenGateOpen = true;
}
```

Managing state across multiple rounds became one of the biggest debugging lessons in the project.

---

# Final Reflections

| What I Did | What I Learned |
|---|---|
| Wrong sprite rows | Read sprite sheets before mapping |
| Fixed row mapping | Debugging is reading, not guessing |
| Added NPC + Barrier | Config patterns transfer across objects |
| DevTools Console | CORS is server-side |
| DevTools Application | localStorage reveals real state |
| Cannonball Dodge | Conditionals control mechanics |
| Escape Room Maze | Arrays make levels editable |
| Zone Catch | Pixel scanning + boolean logic |
| Snake | Arrays power simple mechanics |
| Fish Parallax | Loops + math create visual effects |
| Shipped standalone game | Built a complete product |
| Gamify integration | Fit code into shared architecture |
| Networking unit | Explained debugging errors |

> I came in knowing what variables and loops were. I'm leaving knowing how to use them to build something.

---

<div style="display: flex; flex-wrap: wrap; gap: 14px; margin-top: 20px;">

<a href="{{site.baseurl}}/snake"
   class="btn"
   style="background: linear-gradient(135deg, #111827, #1F2937); color:black;">
   🐍 Snake
</a>

<a href="{{site.baseurl}}/gamify/parallax"
   class="btn"
   style="background: linear-gradient(135deg, #064E3B, #10B981); color:black;">
   🐟 Fish
</a>

<a href="{{site.baseurl}}/gamify"
   class="btn"
   style="background: linear-gradient(135deg, #0F172A, #14B8A6); color:black;">
   🎮 Gamify
</a>

<a href="{{site.baseurl}}/cs-pathway"
   class="btn"
   style="background: linear-gradient(135deg, #7C2D12, #F97316); color:black;">
   🚀 CS Pathway
</a>

<a href="https://gates.opencodingsociety.com/gamify/gategamev2"
   class="btn"
   style="background: linear-gradient(135deg, #1E1B4B, #7C3AED); color:black;">
   🗼 Gate Game
</a>

</div>