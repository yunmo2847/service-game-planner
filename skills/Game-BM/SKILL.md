---
name: Game-BM
description: Use to design a web game's business model (BM) concretely — choice of revenue source, free-to-pay gap, payment trigger points, key metrics. Use for requests like "design a monetization model", "design the IAP" ("과금 모델 짜줘", "IAP 설계해줘"). Continues mid-Game-Plan/Game-Balance whenever monetization needs to go deeper.
---

# Game-BM

For when the game's core loop and progression system are already roughly settled, and the question is "so how does this actually make money" — turns that into a concrete design. If the core loop isn't settled yet, point the user to Game-Plan first — BM sits on top of gameplay, not the other way around.

**Write the output in the language the user is using with you (Korean by default).** These instructions are in English only for maintainability; it's not a cue to answer in English.

## 1. Confirm direction

- Is this a free experiment, or a commercial project (if not commercial, this skill may not even be needed — confirm)
- What BM do similar games use — if unknown, suggest Game-DeepSearch research

## 2. Compare and recommend models

Using the model table in `../references/bm-game.md` (skip re-reading if already read this conversation), recommend one primary revenue source and 1-2 secondary sources that fit this game's genre/core loop. Always call out genre fit explicitly — e.g. recommending power-selling IAP for a competitive/PvP game creates a fairness problem, and that needs to be said.

## 3. Design the free-to-pay gap

The core of free-to-play is this gap: non-paying players need to be able to progress enjoyably enough (too wide a gap → churn), and paying players need to progress fast/favorably enough (no gap → no reason to pay). Concretely define how much of the total content a non-paying player can comfortably reach. If this gap needs to become actual numbers (currency source/sink curves), suggest the Game-Balance skill to the user.

## 4. Place payment triggers in the gameplay

Define the moments a player naturally encounters the payment screen — state clearly whether it's a hard wall (stamina depletion, etc.) or a voluntary convenience purchase (skip tickets, etc.), and note that frequency matters since overdoing it drives churn.

## 5. Define metrics

Precise modeling isn't needed, but state at least a direction: target paying-user ratio, 1-2 core metrics to track (ARPU, ARPPU, etc.).

Format the result so it can drop straight into the monetization section of an existing GDD, if one exists.
