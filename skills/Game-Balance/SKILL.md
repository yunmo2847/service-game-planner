---
name: Game-Balance
description: Use to design web game numeric balancing — currency sources/sinks, growth curves, difficulty curves, free-to-pay gap. Use for requests like "design the balancing", "how should I set the XP curve" ("밸런싱 짜줘", "경험치 곡선 어떻게 잡아야돼"). Continues mid-Game-Plan/Game-BM whenever something needs to become actual numbers.
---

# Game-Balance

Turns the game's currency/growth systems into usable numbers and formulas. If the core loop and progression system (what the growth axis even is) aren't settled yet, point the user to Game-Plan first.

**Write the output in the language the user is using with you (Korean by default).** These instructions are in English only for maintainability; it's not a cue to answer in English.

## 1. Start with the currency/resource table

Reference the balancing section format in `../references/web-game.md` (skip re-reading if this conversation already went through Game-Plan and read it):

| Item | Source | Sink | Baseline value / notes |
|---|---|---|---|

Every currency needs at least one source and one sink — a currency that only accumulates with no sink, or only drains with no source, is a design flaw.

## 2. Settle the curve's logic first, then fill in numbers

The rule for how a number scales matters more than the exact final value. E.g. settle "XP required per level increases 1.15x over the previous level" as a rule first.

- **Linear growth**: predictable, simple. Fits early content, short-session games.
- **Exponential growth**: growth slows sharply later on. Fits games that need long-term retention or a spot to drive monetization.
- **Logarithmic growth (fast early, gentle later)**: good for fast early immersion.

Briefly describe felt difficulty in the early/mid/late game — being able to say "what does the player feel at this point" matters more than just filling in a table; that's what gives the numbers meaning.

## 3. Connect it to BM

If a monetization model is already settled (see Game-BM), concretely compare a non-paying player's progression speed against a paying player's on this curve — e.g. "non-paying: 14 days to level 20, paying: 5 days." If BM isn't settled yet, it's fine to either suggest Game-BM first or design the curve now and align it later — leave it to the user's judgment.

## 4. Validate

Once the numbers are filled in, check the extreme cases: does a new player get frustrated in the first session, does a top player burn through content too fast. Don't stop at the table — mention these two points explicitly.
