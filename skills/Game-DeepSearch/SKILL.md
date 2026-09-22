---
name: Game-DeepSearch
description: Use to research real information needed for a web game plan (reference games, genre trends, comparable games' BM, tech stack) via actual web search, so the plan is grounded in evidence instead of guesses. Use for requests like "research trends in this genre", "what's the monetization structure like for these kinds of games" ("이 장르 게임들 트렌드 조사해줘", "이런 류 게임 과금 구조 어때"). Continues research mid-Game-Plan/Balance/BM whenever real data is needed.
---

# Game-DeepSearch

Replaces the "numbers written from a gut feeling" in a plan with actually-researched information. The goal is accuracy, not plausibility.

**Write the report in the language the user is using with you (Korean by default).** These instructions are in English only for maintainability; it's not a cue to answer in English.

## How to research

Actually search with WebSearch/WebFetch. Don't fake knowing a number you don't — if search can't find it, either label it explicitly as an "estimate" or ask the user if they know.

Narrow the scope to the request. Not a vague "research this whole genre" — focus on wherever the plan is actually stuck (no reference point, no feel for balance, don't know this genre's monetization structure, etc.).

**Search with a budget in mind, not one lookup per sub-question.** A handful of well-chosen searches (roughly 3-6 total) is usually enough to answer a scoped request like "how does this genre monetize" — batch related lookups instead of firing off a separate search for every single fact you want to confirm. Search more only when what you've found is genuinely thin or contradictory, not to triple-check numbers that already came back clean and consistent. Every extra round trip costs real time and tokens, and it isn't buying more accuracy once you already have a confident, sourced answer. If you notice you're past 6 searches, treat that as a signal to stop and write up what you have rather than a reason to keep going — a thinner-than-ideal answer that says what it's missing is better than an open-ended search spiral.

**Prefer the WebSearch snippet over a full WebFetch when the snippet already answers the question.** A search result snippet costs a fraction of what fetching and reading a whole page costs, and most monetization/comparison facts are right there in the snippet. Reach for WebFetch only when the snippet is ambiguous, cut off before the detail you need, or you specifically need to verify an exact figure/quote straight from the source — accuracy on the specific numbers you'll put in a table is worth the extra fetch; re-fetching a page you've already got a clear snippet from is not.

**For any number that's going into the table, reach for a primary source first.** A developer's own postmortem, an official patch note, or a platform's own revenue-estimate tool beats a secondary "top monetization tips" blog repeating a number it got from somewhere else. A secondary source is fine when that's all there is, but don't state it with the same confidence as a primary one; a quick parenthetical flag is enough.

**When two sources genuinely disagree, say so instead of picking one silently.** Industry data on genres is often inconsistent — one report says ads dominate a genre's revenue, another says IAP does, because they sampled different games. Don't average them or quietly go with whichever you saw first. Name both numbers, where each came from, and your best read on why they might differ if you can tell (different sub-genre, different sample, different year). A single confident-sounding number hides the fact that it was actually contested; showing the disagreement is more honest and more useful to someone making a BM decision on it.

Both of the two rules above are about **how you treat what your searches already turned up** — they're not a reason to search more. If the first good source you land on is already solid and nothing you've seen contradicts it, use it and move on; don't go looking for a second source just to be thorough. Reach for another source only when the first one is visibly secondary/thin, or when a later search independently surfaces a number that doesn't match one you already have — at that point, report the mismatch rather than quietly dropping one.

## How to organize results

- **Reference game research**: table of game name, core loop, and overlap/difference with this project. At least 2-3 entries.
- **Genre/trend research**: 3-5 key findings as bullets, with sources.
- **BM/performance research**: what BM similar games use, and any public performance metrics, summarized in a form that feeds directly into Game-BM work.
- **Tech stack research**: compare candidate engines/libraries (Phaser, PixiJS, Three.js, Unity WebGL, etc.) against this project's actual requirements (genre, performance, team's familiarity).

Don't let the research stand on its own — point out in one line which section of the in-progress plan (if any) it should feed into.

## Save it as a file, in this template

Separately from showing results in the conversation, save to a markdown file in the `research/` folder (create it if missing) in the current working directory. Filename format: `<topic-slug>-<YYYY-MM-DD>.md` — this makes it reusable later, either to look up again or to carry over into Game-Publish's Notion page.

This exact structure applies every time (it's what keeps the report scannable instead of a wall of prose, so it's given here directly rather than as a separate file to go fetch — there's no case where you'd skip it, so there's nothing to save by looking it up on demand):

```markdown
# <Research Topic>

**TL;DR:** One or two sentences with the actual answer/finding up front — not a preview of what the report will cover, the finding itself. If someone reads only this line, they should know what to do next.

## Findings

- Bulleted, one finding per line, source linked inline. Group with a subheading only if you have more than ~6 bullets in one topic.

## Comparison (if the research involved comparing games/BMs)

| Name | Key feature | Price/BM | How this project differs |
|---|---|---|---|

## What this changes in the plan

One line: which section of the plan this affects and what should change there. Skip this if the research was requested standalone, with no plan in progress.

## Sources

Numbered list of links used, in the order first cited above.
```

Keep the TL;DR honest — if the research came back thin or inconclusive, say that plainly rather than padding it into something that sounds more conclusive than it is.

**Before finishing, check whether this is actually decision-ready.** If someone read only the TL;DR and the comparison table, could they make the call they came here to make (a BM choice, a genre-fit judgment, "yes this gap design works for us")? If there's a real open question left over — not everything needs a forced answer, but a genuine fork you can see but didn't resolve — name it explicitly as a decision point in "What this changes in the plan" instead of leaving it implied somewhere in the findings.

Before saving, glance back at the prose you just wrote (not the tables) for the obvious AI-tell patterns — the same connector repeated sentence after sentence, empty filler lines ("이는 매우 중요합니다"-style), every sentence the same length. Fix on the spot if you see it; this is a quick self-check, not a reason to go fetch a separate checklist file — DeepSearch output is mostly tables and short bullets, so there's rarely much prose to catch here in the first place. (Game-Publish carries the fuller version of this check, since Notion pages carry much more prose.)

## Keep the chat reply short — the file already has the full detail

The file you just saved already contains the complete tables and findings. Don't reproduce them again in your conversational reply — that's writing the same content twice for no reader benefit. The chat reply should be: the TL;DR in your own words, at most one line pointing at what's most decision-relevant, and where you saved the file. Save the full table/bullet reproduction for if the user asks to see it inline.
