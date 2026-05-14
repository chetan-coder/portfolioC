---
layout: post 
title: Portfolio Home 
hide: true
show_reading_time: false
---

# :contentReference[oaicite:0]{index=0} — CS111 Portfolio

## 🎮 Slime Escape — Full Development Journey

This portfolio documents my full progression through CS111. I started with a simple slime movement system that was visually broken, and gradually built a complete three-level game integrated into a shared engine architecture.

Each section shows **real game runner code (%%js blocks)** paired with explanations of what changed and why it mattered.

---

# Part 1: The Bug — Broken Sprite Direction Mapping

My first working version had basic WASD movement, but the slime faced the wrong direction depending on input. The physics were correct — only the sprite mapping was wrong.

### ❌ Wrong Mapping Version

%%js

// GAME_RUNNER: Slime moves but faces incorrect directions due to wrong sprite row mapping

import GameControl from '/assets/js/GameEnginev1/essentials/GameControl.js';
import GameEnvBackground from '/assets/js/GameEnginev1/essentials/GameEnvBackground.js';
import Player from '/assets/js/GameEnginev1/essentials/Player.js';

class GameLevelBug {
  constructor(gameEnv) {
    const path = gameEnv.path;

    const bgData = {
      name: 'bg',
      src: path + '/images/gamebuilder/bg/alien_planet.jpg',
      pixels: { height: 772, width: 1134 }
    };

    const playerData = {
      id: 'player',
      src: path + '/images/gamebuilder/sprites/slime.png',
      SCALE_FACTOR: 5,
      STEP_FACTOR: 1000,
      ANIMATION_RATE: 50,
      INIT_POSITION: { x: 100, y: 435 },
      pixels: { height: 225, width: 225 },
      orientation: { rows: 4, columns: 4 },

      down: { row: 0, start: 0, columns: 3 },
      left: { row: 2, start: 0, columns: 3 }, // wrong
      right: { row: 1, start: 0, columns: 3 },
      up: { row: 3, start: 0, columns: 3 }
    };

    this.classes = [
      { class: GameEnvBackground, data: bgData },
      { class: Player, data: playerData }
    ];
  }
}

export const gameLevelClasses = [GameLevelBug];
export { GameControl };

---

### 🧠 What was happening?

The sprite sheet rows were misread. Movement worked, but visuals were reversed, making the character feel “broken” even though logic was correct.

---

# Part 2: The Fix — Correct Sprite Sheet Mapping

After inspecting the sprite sheet, I corrected the row assignments. This immediately fixed all movement directions.

### ✅ Fixed Version

%%js

// GAME_RUNNER: Correct sprite mapping fixes all movement directions

import GameControl from '/assets/js/GameEnginev1/essentials/GameControl.js';
import GameEnvBackground from '/assets/js/GameEnginev1/essentials/GameEnvBackground.js';
import Player from '/assets/js/GameEnginev1/essentials/Player.js';

class GameLevelFixed {
  constructor(gameEnv) {
    const path = gameEnv.path;

    const bgData = {
      name: 'bg',
      src: path + '/images/gamebuilder/bg/alien_planet.jpg',
      pixels: { height: 772, width: 1134 }
    };

    const playerData = {
      id: 'player',
      src: path + '/images/gamebuilder/sprites/slime.png',
      SCALE_FACTOR: 5,
      STEP_FACTOR: 1000,
      ANIMATION_RATE: 50,
      INIT_POSITION: { x: 100, y: 300 },
      pixels: { height: 225, width: 225 },
      orientation: { rows: 4, columns: 4 },

      down: { row: 2, start: 0, columns: 3 },
      left: { row: 0, start: 0, columns: 3 },
      right: { row: 1, start: 0, columns: 3 },
      up: { row: 3, start: 0, columns: 3 }
    };

    this.classes = [
      { class: GameEnvBackground, data: bgData },
      { class: Player, data: playerData }
    ];
  }
}

export const gameLevelClasses = [GameLevelFixed];
export { GameControl };

---

### 📊 Bug vs Fix Comparison

| Issue | Before | After |
|------|--------|------|
| Sprite direction | Incorrect | Correct |
| Player feel | Confusing | Natural |
| Debug state | Guessing | Data-driven fix |
| Root cause | Misread sprite sheet | Correct mapping applied |

---

# Part 3: NPCs + Collision Barriers

Once movement worked, I expanded the system with NPC interaction and invisible collision barriers.

A key engine rule: `fromOverlay: true` is required or collisions won’t register.

%%js

// GAME_RUNNER: NPC interaction + invisible collision system

import GameControl from '/assets/js/GameEnginev1/essentials/GameControl.js';
import GameEnvBackground from '/assets/js/GameEnginev1/essentials/GameEnvBackground.js';
import Player from '/assets/js/GameEnginev1/essentials/Player.js';
import Npc from '/assets/js/GameEnginev1/essentials/Npc.js';
import Barrier from '/assets/js/GameEnginev1/essentials/Barrier.js';

class GameLevelExpanded {
  constructor(gameEnv) {
    const path = gameEnv.path;

    const bgData = {
      name: 'bg',
      src: path + '/images/gamebuilder/bg/alien_planet.jpg',
      pixels: { height: 772, width: 1134 }
    };

    const npcData = {
      id: 'npc',
      greeting: 'Working...',
      src: path + '/images/gamify/r2_idle.png',
      SCALE_FACTOR: 5,
      INIT_POSITION: { x: 500, y: 300 },
      pixels: { height: 223, width: 505 },
      orientation: { rows: 1, columns: 3 },
      dialogues: ['Working...']
    };

    const barrier = {
      id: 'barrier',
      x: 309,
      y: 89,
      width: 28,
      height: 252,
      visible: false,
      fromOverlay: true
    };

    this.classes = [
      { class: GameEnvBackground, data: bgData },
      { class: Player, data: playerData },
      { class: Npc, data: npcData },
      { class: Barrier, data: barrier }
    ];
  }
}

export const gameLevelClasses = [GameLevelExpanded];
export { GameControl };

---

### 🧠 Key Learning

- NPCs reuse the same object-based architecture as players
- Barriers are data objects, not hardcoded logic
- Engine behavior depends on configuration flags

---

# Part 4: DevTools Debugging Workflow

### Console Debugging

| Error | Meaning |
|------|--------|
| 404 | Missing file path |
| CORS | Server blocking request |
| Connection refused | Backend offline |

### Application Tab (State Inspection)

| Stored Key | Purpose |
|------------|--------|
| player_name | user identity |
| coinsCollected | progression tracking |

---

# Part 5: CS111 Concepts in Real Game Code

### 📊 Concept Mapping

| Concept | Class Example | Game Usage |
|--------|--------------|------------|
| Variables | x, y values | player position |
| Conditionals | if/else | collisions |
| Loops | forEach | entity system |
| Arrays | lists | this.classes |
| Objects | key-value data | configs |
| Classes | templates | levels |
| Booleans | true/false | game states |
| Functions | reusable logic | interactions |

---

### 🎮 Game Systems Built

| System | Mechanic | Concept Used |
|--------|----------|-------------|
| Movement | WASD control | variables + sprites |
| Collision | barriers | conditionals |
| NPCs | dialogue | objects + classes |
| Levels | progression | architecture design |

---

# Final Reflection

| Stage | What I Built | What I Learned |
|------|-------------|----------------|
| Sprite Bug | Broken movement visuals | Data mapping matters more than code complexity |
| Fix Phase | Correct animation system | Debugging is inspection, not guessing |
| NPC System | Interactive objects | Reusable architecture design |
| Barriers | Collision system | Engine flags control behavior |
| DevTools | Debugging tools | Real-time state inspection is essential |
| Full Game | 3-level system | Systems thinking > isolated logic |

---

## Final Takeaway

This project showed me that game development is not about writing more code — it’s about structuring systems correctly. Once I understood how data flows through the engine, everything became easier to build, debug, and expand.

---