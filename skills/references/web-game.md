# Web Game Plan (GDD) Structure

Assumes a game running in a browser context (WebGL, HTML5, etc.). Keep web-specific constraints in mind throughout — session length, load time, input method (mostly mouse/touch). Add or drop sections to match project scale — a small single-player game can skip section 7 (retention).

## 1. Game Overview
- One-line concept (elevator pitch)
- Genre and reference games (1-2 existing games with a similar feel — what you're borrowing and what you're doing differently)
- Target player base
- (BM assumption) Note in one line here whether this is a free experiment or a commercial project, and if commercial, a rough sense of ads/IAP/battle-pass direction — flesh this out in section 9.

## 2. Core Gameplay Loop
Lay out the most basic action cycle the player repeats, as an arrow chain.
Example: Explore → Fight → Get rewards → Upgrade → Explore again

Explain in one or two sentences why this loop is fun — what keeps pulling the player back into it. If the core loop isn't clear, no amount of polish on the other systems will save the game — nail this section first, and nail it solidly.

## 3. Core Mechanics
The game's rules and controls. Define actual play actions concretely — movement, combat, puzzles, building, etc.
- List of actions the player can take
- Input method and result for each action
- Win/lose (or success/fail) conditions

## 4. Progression System
What the player gains over time, and how they grow.
- Growth axes (level, skill tree, gear, collection, etc.)
- What new choices or abilities unlock at each growth stage

## 5. Balancing
Lay out as a table:

| Item | Source | Sink | Baseline value / notes |
|---|---|---|---|
| (currency/resource name) | | | |

Settle the rule for how a number scales before settling the exact number (e.g. "XP required per level increases 1.15x over the previous level"). If there's a difficulty curve, briefly describe the felt difficulty in the early/mid/late game.

## 6. Content Structure
How stages/levels/maps are organized, roughly how many are needed at launch, and the cadence/method for expanding content afterward.

## 7. Retention & Live Ops
What brings players back tomorrow, and next week.
- Daily/weekly quests, login rewards
- Event cadence, season concept
- (Skip this section for small/single-player projects)

## 8. Web Platform Constraints
State the real constraints specific to a web game.
- Target session length (is the design built for short browser sessions?)
- Initial load time target, total asset size ceiling
- Tech stack (Phaser, Unity WebGL, PixiJS, Three.js, etc.) — if decided, name it and note how that choice constrains the core loop's implementation
- Mobile browser support (touch input, aspect ratio)

## 9. Monetization
Give this section weight equal to the others if the project is commercial — shorten or skip it for a free experiment. See `bm-game.md` for model types and genre fit. Use the Game-BM skill when this needs to go deeper (free-to-pay gap, payment trigger points, metrics), and Game-Balance to turn that gap into actual numbers.

- **Primary / secondary revenue source**: pick a combination of ads (interstitial/rewarded), IAP (time-skip/cosmetic/content), battle pass, etc.
- **Payment trigger points**: where in play they show up naturally
- **Free-to-play reach**: how much of the total content a non-paying player can comfortably reach

## 10. Art & Tone
One or two sentences on visual style and mood. Break detailed art direction (reference images, color palette) into a separate doc if needed.
