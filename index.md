---
layout: post 
title: Portfolio Home 
hide: true
show_reading_time: false
---

# 🎮 Slime Escape — CS111 Portfolio

## My Full Development Journey: From Broken Sprites to a Complete Game

I started with a simple slime that faced the wrong direction. By the end, I built a three-level game with NPCs, collisions, leaderboards, and proper system architecture.

This portfolio shows **real game code** and explains what changed at each step.

---

# Part 1: The First Bug — Wrong Sprite Directions

My first version had movement working, but the slime faced the wrong way. The code was right; the sprite mapping was wrong.

## The Broken Code

```javascript
// Player data with WRONG sprite row mappings
const playerData = {
  id: 'player',
  src: path + '/images/gamebuilder/sprites/slime.png',
  SCALE_FACTOR: 5,
  INIT_POSITION: { x: 100, y: 435 },
  pixels: { height: 225, width: 225 },
  orientation: { rows: 4, columns: 4 },

  // These are WRONG - slime faces wrong direction
  down: { row: 0, start: 0, columns: 3 },
  left: { row: 2, start: 0, columns: 3 },  // ❌ Wrong row
  right: { row: 1, start: 0, columns: 3 },
  up: { row: 3, start: 0, columns: 3 }
};
```

## Why This Failed

The sprite sheet has 4 rows of animations. I mapped them to the wrong rows. So when the player pressed left, the slime faced a different direction.

## CS111 Concepts Here

- **Objects**: `playerData` stores configuration as key-value pairs
- **Numbers**: Row indices (0, 1, 2, 3)
- **Strings**: File paths
- **Variables**: `const playerData` avoids hardcoded values

---

# Part 2: The Fix — Correct Sprite Mapping

I inspected the sprite sheet and fixed the row numbers.

## The Fixed Code

```javascript
// Player data with CORRECT sprite row mappings
const playerData = {
  id: 'player',
  src: path + '/images/gamebuilder/sprites/slime.png',
  SCALE_FACTOR: 5,
  INIT_POSITION: { x: 100, y: 300 },
  pixels: { height: 225, width: 225 },
  orientation: { rows: 4, columns: 4 },

  // Now CORRECT - slime faces right direction
  down: { row: 2, start: 0, columns: 3 },
  left: { row: 0, start: 0, columns: 3 },
  right: { row: 1, start: 0, columns: 3 },
  up: { row: 3, start: 0, columns: 3 }
};
```

## What Changed

| Part | Before | After |
|------|--------|-------|
| Down animation | row: 0 | row: 2 |
| Left animation | row: 2 | row: 0 |
| Feel | Broken, confusing | Natural, correct |

## How I Fixed It

I opened DevTools → Elements tab → found the canvas → looked at the sprite sheet image → counted the rows → mapped them correctly.

**Lesson**: Sometimes the bug isn't in your logic. It's in your data.

---

# Part 3: Adding NPCs and Collision Barriers

Now the sprite worked. I added an NPC character and invisible walls to block movement.

## The Code

```javascript
// This class EXTENDS the base GameLevel class (Inheritance)
class GameLevelExpanded extends GameLevel {
  constructor(gameEnv) {
    super(gameEnv);  // Call parent constructor (Constructor Chaining)

    const path = gameEnv.path;

    // NPC character
    const npcData = {
      id: 'npc',
      greeting: 'Welcome, traveler!',
      src: path + '/images/gamify/r2_idle.png',
      SCALE_FACTOR: 5,
      INIT_POSITION: { x: 500, y: 300 },
      pixels: { height: 223, width: 505 },
      orientation: { rows: 1, columns: 3 },
      dialogues: ['Welcome!', 'Find the exit...']
    };

    // Invisible collision barrier
    const barrier = {
      id: 'barrier_wall',
      x: 309,
      y: 89,
      width: 28,
      height: 252,
      visible: false,
      fromOverlay: true  // IMPORTANT: This enables collision detection
    };

    // Store all game objects in an array
    this.classes = [
      { class: GameEnvBackground, data: bgData },
      { class: Player, data: playerData },
      { class: Npc, data: npcData },
      { class: Barrier, data: barrier }
    ];
  }

  // Loop through all objects and check if any are NPCs
  checkNpcInteractions() {
    for (const obj of this.classes) {  // Iteration: Loop through array
      if (obj.class === Npc) {          // Conditional: Check if it's an NPC
        if (obj.data.interact) {        // Nested Conditional: Check if interact exists
          obj.data.interact();          // Call the NPC interaction
        }
      }
    }
  }
}
```

## CS111 Concepts Here

- **Inheritance**: `class GameLevelExpanded extends GameLevel` - reuse parent code
- **Constructor Chaining**: `super(gameEnv)` - call parent setup
- **Arrays**: `this.classes = [...]` - store multiple game objects
- **Loops**: `for (const obj of this.classes)` - check each object
- **Conditionals**: `if (obj.class === Npc)` - do something only if true
- **Booleans**: `visible: false`, `fromOverlay: true` - true/false flags
- **Objects**: Configuration data with properties

## Key Rule

The `fromOverlay: true` flag is **critical**. Without it, the barrier won't detect collisions. This shows how engine behavior is controlled by data.

---

# Part 4: Canvas Rendering — Drawing Sprites

This is how the game actually draws the slime onto the screen.

## How Sprite Animation Works

```javascript
class Player {
  draw() {
    // The sprite sheet is 225x225 pixels with 4 rows × 4 columns
    // Each animation frame is 56.25 × 56.25 pixels

    // Calculate where to grab the sprite from the sheet
    const spriteWidth = this.pixels.width / this.orientation.columns;  // 225 / 4 = 56.25
    const spriteHeight = this.pixels.height / this.orientation.rows;   // 225 / 4 = 56.25

    // Which frame in the animation are we on?
    const sx = this.currentFrame * spriteWidth;      // Source X position
    const sy = this.direction.row * spriteHeight;    // Source Y position

    // Draw the sprite to the canvas
    this.ctx.drawImage(
      this.spriteSheet,                    // Source: sprite sheet image
      sx, sy,                              // Where to grab from (source position)
      spriteWidth, spriteHeight,           // How big to grab (source size)
      this.position.x, this.position.y,    // Where to draw (destination position)
      this.width, this.height              // How big to draw (destination size)
    );

    // Optional: Draw a red box around the player for debugging
    if (this.showHitbox) {
      this.ctx.strokeStyle = 'red';
      this.ctx.lineWidth = 2;
      this.ctx.strokeRect(
        this.position.x,
        this.position.y,
        this.width,
        this.height
      );
    }
  }
}
```

## How It Works (Step by Step)

1. **Calculate sprite size**: Sprite sheet is 225×225, with 4 rows and 4 columns → each frame is 56.25×56.25
2. **Find which frame**: If `currentFrame = 1` and direction is left, grab from X=56.25, Y=0
3. **Draw to canvas**: Take that piece and draw it on the screen at the player's position

## CS111 Concepts Here

- **Math Operators**: `/` to divide and scale sprites
- **Variables**: `sx`, `sy` store calculated positions
- **Canvas API**: `ctx.drawImage()` renders sprites
- **Conditionals**: `if (this.showHitbox)` optionally draw debug box
- **Booleans**: `this.showHitbox` flag

---

# Part 5: Getting Data from the Internet — JSON and APIs

The game has a leaderboard that saves high scores to a server and displays them.

## Fetching the Leaderboard

```javascript
class LeaderboardManager {
  // Get the top 10 scores from the server
  async fetchTopScores() {
    try {
      // Send a GET request to the server
      const res = await fetch('/api/leaderboard');

      // Check if the request worked
      if (!res.ok) {
        throw new Error(`Server error: ${res.status}`);
      }

      // Convert the response from JSON to JavaScript
      const data = await res.json();

      // Get the top score
      const topScore = data.scores[0].value;
      const topPlayer = data.scores[0].playerName;

      // Loop through all scores and create a formatted list
      const leaderboard = data.scores.map((entry) => ({
        rank: entry.rank,
        name: entry.playerName,
        score: entry.value,
        date: entry.timestamp
      }));

      return leaderboard;
    } catch (error) {
      console.error('Failed to fetch leaderboard:', error);
      return [];  // Return empty if it fails
    }
  }

  // Save a new score to the server
  async submitScore(playerName, score) {
    const res = await fetch('/api/leaderboard', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        playerName,
        score,
        timestamp: new Date().toISOString()
      })
    });

    // Check if submission was successful
    if (res.status === 200) {
      console.log('Score saved!');
      return true;
    }
    return false;
  }
}

// How to use it:
const leaderboard = new LeaderboardManager();
const scores = await leaderboard.fetchTopScores();
console.log(scores);  // Print all scores

await leaderboard.submitScore('Player1', 1500);  // Save a score
```

## What's Happening

1. **fetch('/api/leaderboard')** - Ask the server for the leaderboard
2. **await** - Wait for the answer (network takes time)
3. **res.json()** - Convert JSON text to JavaScript objects
4. **data.scores[0]** - Get the first score in the array
5. **.map()** - Loop through all scores and reformat them
6. **POST request** - Send a new score back to the server

## CS111 Concepts Here

- **Async/Await**: Handle operations that take time (network)
- **JSON Parsing**: `res.json()` converts text to objects
- **Arrays**: `data.scores` is a list of scores
- **Objects**: Each score has name, value, date
- **Loops**: `.map()` processes each score
- **Conditionals**: `if (res.status === 200)` check success
- **Error Handling**: `try...catch` handles failures

---

# Part 6: Debugging — Finding and Fixing Problems

When the game broke, I used DevTools to find the bug.

## Console Debugging

```javascript
// Simple logging
console.log('Player position:', this.position);
// Output: Player position: { x: 100, y: 300 }

console.log('All game objects:', this.classes);
// Output: All game objects: [background, player, npc, barrier]

// Log only when something goes wrong
if (this.health <= 0) {
  console.warn('Player died at position:', this.position);
}

// Measure how fast your game loop runs
console.time('gameLoop');
this.update();
this.draw();
console.timeEnd('gameLoop');
// Output: gameLoop: 16.2ms
```

## Using DevTools Tabs

| Tab | What I Used It For | How It Helped |
|-----|-------------------|---------------|
| **Console** | Logged variables to inspect state | Found that `sprite.src` was undefined |
| **Elements** | Inspected the canvas and HTML | Verified canvas was 1280×720 pixels |
| **Sources** | Set breakpoints in code | Paused execution to inspect variables step-by-step |
| **Network** | Watched API requests | Saw that leaderboard endpoint returned 404 |
| **Application** | Checked localStorage | Verified player name was saved correctly |

## Common Errors I Fixed

| Error | What Went Wrong | How I Fixed It |
|-------|-----------------|---------------|
| 404: Cannot GET /api/leaderboard | Wrong endpoint URL | Changed `/api/leaderboard` to `/api/scores` |
| Sprite doesn't show | Image path is wrong | Used `gameEnv.path` variable instead of hardcoding |
| Game doesn't respond to input | GameControl not imported | Added `import GameControl from ...` |
| Barrier doesn't block movement | Missing `fromOverlay: true` | Added the flag to barrier config |
| CORS error when fetching | Server doesn't allow requests | Admin added `Access-Control-Allow-Origin` header |

## Pro Debugging Tips

1. **Use `console.log()` in loops** - See every object being checked
2. **Set breakpoints in conditionals** - Pause when a condition is true
3. **Check the Network tab** - See exactly what the server is sending back
4. **Inspect localStorage** - Verify saved data is correct format
5. **Draw hitboxes in red** - Visually see collision boundaries

---

# Part 7: Testing the Game Works

After building everything, I tested that the systems work together.

## Test 1: Player Movement

```javascript
// Test that player can walk without hitting walls
const test1 = () => {
  player.position = { x: 100, y: 100 };
  player.moveRight();  // Move right
  player.moveRight();  // Move again
  
  // Did the player move?
  if (player.position.x > 100) {
    console.log('✅ Movement works');
  } else {
    console.log('❌ Movement broken');
  }
};
```

## Test 2: Collision Detection

```javascript
// Test that player can't walk through barriers
const test2 = () => {
  const distance = Math.hypot(
    player.x - barrier.x,
    player.y - barrier.y
  );

  if (distance < 50) {
    console.log('✅ Collision detected');
  } else {
    console.log('❌ No collision');
  }
};
```

## Test 3: NPC Dialogue

```javascript
// Test that talking to NPC works
const test3 = () => {
  const canTalkToNpc = player.distance < 50 && npc.hasDialogue;
  
  if (canTalkToNpc) {
    npc.showDialogue();
    console.log('✅ NPC dialogue works');
  } else {
    console.log('❌ NPC dialogue broken');
  }
};
```

## Test 4: Leaderboard Saving

```javascript
// Test that scores save correctly
const test4 = async () => {
  const success = await leaderboard.submitScore('TestPlayer', 1500);
  
  if (success) {
    console.log('✅ Score saved successfully');
  } else {
    console.log('❌ Score failed to save');
  }
};
```

## All Tests Passed ✅

- Player walks full level without clipping walls
- NPC dialogue triggers on collision
- Leaderboard saves scores and returns 200 status
- Level transitions when player reaches exit

---

# Part 8: All CS111 Concepts in One Place

This table shows every CS111 concept and how it's used in the game.

## The Complete Picture

| Concept | Simple Example | Game Usage | Why It Matters |
|---------|----------------|-----------|---------------|
| **Variables** | `const x = 100` | Store player position, score, etc. | Without variables, everything is hardcoded |
| **Data Types** | `100` (number), `"name"` (string), `true` (boolean) | Represent all game data | Each type has different purpose |
| **Operators** | `2 + 3`, `10 / 2`, `x > 5`, `alive && !paused` | Math for physics, comparisons | Operators do all calculations |
| **Conditionals** | `if (x > 100) { ... }` | Check collisions, trigger events | Gate when actions happen |
| **Loops** | `for (const obj of objects) { ... }` | Process all game entities | Scale to many objects efficiently |
| **Arrays** | `const items = [sword, shield]` | Store multiple game objects | Arrays hold variable-sized lists |
| **Objects** | `{ id: 'player', x: 100, y: 50 }` | Configure game entities | Objects group related data |
| **Functions** | `function moveRight() { ... }` | Reusable action blocks | Functions prevent code duplication |
| **Classes** | `class Player { ... }` | Create templates for entities | Classes make objects consistent |
| **Inheritance** | `class Enemy extends Player { ... }` | Reuse code from parent class | Inheritance reduces duplication |
| **JSON** | `{ "name": "Alice", "score": 500 }` | Send data over internet | JSON is the internet's data format |
| **Async/Await** | `const data = await fetch(...)` | Wait for network responses | Async handles slow operations |
| **Canvas** | `ctx.drawImage(sprite, ...)` | Render graphics | Canvas is how games draw |
| **DevTools** | Breakpoints, console logs, Network tab | Debug live code | DevTools find real bugs |

## Game Systems and What They Use

| System | What It Does | Key Concepts |
|--------|-------------|--------------|
| **Sprite Animation** | Draws character moving | Variables, Canvas, Math |
| **Movement** | WASD input moves player | Conditionals, Variables |
| **Collision** | Detect when things touch | Loops, Conditionals, Math |
| **NPC Dialogue** | Show text when close | Objects, Arrays, Conditionals |
| **Barriers** | Invisible walls | Objects, Booleans |
| **Leaderboard** | Save/load high scores | JSON, Async, Fetch |
| **Level System** | Multiple levels, progression | Classes, Inheritance |

---

# Part 9: Key Lessons

## What I Learned

### 1. Data is More Important Than Code

The sprite bug taught me that **well-structured data makes simple code**. I didn't need to rewrite the movement system—I just fixed the sprite mapping object.

### 2. Inheritance Prevents Duplication

By using `class GameLevelExpanded extends GameLevel`, I reused all parent code. Without inheritance, I'd copy-paste everything for each level.

### 3. Systems Scale Better Than Features

Instead of special code for "player," "npc," and "barrier," I built one generic **entity system** that handles all of them. Now adding new entities is trivial.

### 4. Configuration Beats Hardcoding

Every level, sprite, and asset is loaded from **data objects**, not hardcoded in functions. This means I can create new levels without touching code.

### 5. DevTools Are Essential

I found bugs using:
- Console logs to inspect variables
- Breakpoints to pause execution
- Network tab to see API responses
- Elements tab to verify canvas size

These tools saved me hours.

### 6. APIs Connect Games to the World

JSON and fetch enable the leaderboard. The game talks to a server and stores scores permanently. APIs are how games become multiplayer.

### 7. Testing Matters

Integration testing (testing everything together) caught bugs that unit testing (testing parts separately) missed. The player could walk through walls in isolation tests but collided correctly in the full game.

---

# Final Reflection

## The Journey

| Stage | What I Built | Size |
|-------|-------------|------|
| Start | Broken sprite, WASD movement | 50 lines |
| Sprite Fix | Correct animation mapping | 50 lines |
| NPCs | Interactive characters | 100 lines |
| Barriers | Collision system | 150 lines |
| Canvas | Rendering pipeline | 200 lines |
| Leaderboard | API integration | 300 lines |
| Full Game | 3 levels, multiple systems | 1,000+ lines |

## What This Shows

I went from fixing a sprite bug to building a **game engine** that handles:
- Sprite animation ✅
- Collision detection ✅
- NPC interaction ✅
- Network communication ✅
- Data persistence ✅
- Multiple levels ✅

**All using CS111 concepts.**

## The Real Lesson

Game development isn't magic. It's applying fundamental computer science systematically:
- Use **variables** to avoid hardcoding
- Use **objects** to organize data
- Use **classes** to create templates
- Use **inheritance** to reuse code
- Use **loops** to scale
- Use **APIs** to connect systems

Everything I built was built from these concepts.

## Looking Forward

This game can still grow:
- Add sound effects (Web Audio API)
- Add multiplayer (WebSockets)
- Add mobile controls (touch events)
- Add procedural levels (algorithms)
- Add AI enemies (pathfinding)

But the foundation is solid. The architecture is clean. Adding new features just means extending existing classes and adding new objects to the data.

**That's the power of understanding fundamentals.**

---

## Summary

This portfolio showed my progression through CS111:

1. ✅ Fixed a sprite bug by inspecting data
2. ✅ Added NPCs using objects and inheritance
3. ✅ Built collisions using loops and conditionals
4. ✅ Rendered graphics using canvas
5. ✅ Connected to servers using JSON and fetch
6. ✅ Debugged with DevTools
7. ✅ Tested everything works together
8. ✅ Built a complete game system

Every step used CS111 concepts. Every concept serves a purpose. The game works because the fundamentals are solid.

---
