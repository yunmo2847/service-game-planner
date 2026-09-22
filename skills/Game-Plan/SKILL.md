---
name: Game-Plan
description: Use to design a browser web game (HTML5/WebGL) plan through Socratic questioning and turn it into a formal GDD. Use for requests like "plan out a web game", "nail down the core loop", "write the GDD" ("웹게임 기획해줘", "코어 루프 잡아줘", "GDD 만들어줘"). Also triggers without an explicit request whenever the conversation is fleshing out a new web game idea. For plain web service planning, use Web-Plan (if a game has shop/community elements, consult Web-Plan too).
---

# Game-Plan

Turns a fragmented web game idea into a structured plan (GDD). Doesn't just transcribe whatever the user says — asks questions that help the user clarify their own decisions.

**Write everything you produce for the user — questions, the GDD itself — in the language the user is using with you (Korean by default).** These instructions are in English only for maintainability; it's not a cue to answer in English.

## 1. Interview Socratically

Read `../references/socratic-method.md` and follow it. Ask 1-3 questions at a time, dig into the "why" behind the surface request at least once, and if the user gets stuck, stop asking and show a draft with assumptions labeled instead. If `socratic-method.md`/`web-game.md` were already read in this same conversation (e.g. this is a follow-up request to polish a single system), don't re-read them — work from what's still in context. Re-reading the same file on every follow-up is pure token waste.

**Settle the core loop first, and settle it solidly.** If the core loop is unclear, no amount of polish on the rest (progression, balance, content) will save the game. Always confirm "why would this loop want to be repeated?" before locking the core loop in.

**Also check BM (business model) direction early in the interview.** "Is this a free experiment, or does it need to make commercial revenue? If commercial, do you have a sense of ads/IAP/battle-pass?" — if it's commercial, the answer keeps shaping the core loop and progression design (where the payment trigger naturally sits) going forward.

## 2. Write it up as a plan (GDD)

Use `../references/web-game.md`'s section structure as the skeleton. For a small project, sections like retention/live-ops can be dropped — the template isn't a spec to satisfy.

Give the monetization section weight equal to the others if the project is commercial. Compare candidates among ads/IAP/battle-pass and record the reasoning. Suggest the Game-BM skill when deeper BM design is needed (pricing, free-to-pay gap, metric targets), and Game-Balance when the gap needs to become actual numbers (currency sources/sinks, growth curves).

Where real data is needed (reference games, genre trends, comparable games' BM), don't fill it in with a guess — suggest the Game-DeepSearch skill to the user.

A short brainstorm or a single-system polish is fine to leave in conversation. But once the content reaches formal-GDD quality, don't just leave it there — decide where it lives. The default is Notion. Ask whether to continue into the Game-Publish skill to write it up there (if the Notion MCP isn't connected, offer a markdown file instead).

## 3. Check before delivering (do this yourself — no subagent)

Before handing over the document, check it yourself against "could someone else start working from this immediately?" Confirm the core loop's fun factor rests on concrete mechanics, not just an abstract claim.

If this continues an in-progress plan, extend it without contradicting settings already locked in.

## 4. Deeper checks are opt-in only, one specialist at a time

Once the formal GDD is finished, don't automatically call a subagent — the fixed cost of spinning one up (tool-schema loading, etc.) isn't worth paying automatically for a short task, and it's definitely not worth paying multiple times in parallel. Two opt-in options exist; offer them as short one-liners and only call one when the user actually asks for it, **passing the draft as inline text in the prompt** (not a file path) so the subagent doesn't go hunting for other files to read:

- **`game-plan-reviewer`** — a document review across three lenses at once (core loop / implementation difficulty / BM). "If you want a more thorough look, I can run a cross-check review — it'll take a bit longer."
- **`game-tester`** — a different lens: not "is the document complete," but "how would this actually feel to play" (onboarding confusion, pacing spikes, exploitable loopholes). Offer this once the GDD is far enough along that a real system exists to playtest. "Want me to mentally playtest this and flag where a real player would get stuck or find an exploit?"

Neither is called automatically, and don't call both back-to-back unless the user asks for both — each is its own subagent cost. Both only report findings; they don't edit the draft, and only findings the user agrees are worth applying get folded back in.
