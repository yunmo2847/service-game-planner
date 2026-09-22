---
name: Web-Plan
description: Use to design a web service/platform plan (SaaS, e-commerce, creator tools, etc.) through Socratic questioning and turn it into a formal PRD. Use for requests like "plan out a web service", "define the MVP scope", "prioritize the features" ("웹서비스 기획해줘", "MVP 범위 정해줘", "기능 우선순위 정리해줘"). Also triggers without an explicit request whenever the conversation is fleshing out a new web service idea. For the game itself, use Game-Plan (if a web game has shop/community elements, consult Web-Plan too).
---

# Web-Plan

Turns a fragmented web service idea into a structured plan. Doesn't just transcribe whatever the user says — asks questions that help the user clarify their own decisions.

**Write everything you produce for the user — questions, the plan document itself — in the language the user is using with you (Korean by default).** These instructions are in English only for maintainability; it's not a cue to answer in English.

## 1. Interview Socratically

Read `../references/socratic-method.md` and follow it. In short: ask 1-3 questions at a time, dig into the "why" behind the surface request at least once, and if the user gets stuck, stop asking and show a draft with assumptions labeled instead.

**Ask about BM (business model) early — no later than right after the target user is confirmed.** "How does this make money? If monetization isn't the goal, what counts as 'success' for this project?" — the answer becomes the standard for feature priority later. Don't treat BM as a formality tacked onto the end of the document.

Don't re-ask about anything already covered in conversation (concept, target, ideas, etc.). If `socratic-method.md`/`web-service.md` were already read in this same conversation (e.g. this is a follow-up request to polish a single section), don't re-read them — work from what's still in context. Re-reading the same file on every follow-up is pure token waste.

## 2. Write it up as a plan

Use `../references/web-service.md`'s section structure as the skeleton. Drop sections that don't fit the project, add ones that are needed — the template isn't a spec to satisfy.

Give the BM (monetization) section equal or greater weight than the others. Don't present just one candidate model — compare at least 2-3 and record the reasoning for the recommendation. Suggest the Web-BM skill when deeper BM design is needed (pricing, conversion funnel, metric targets).

Where real data is needed (competitors, market pricing, comparable cases), don't fill it in with a guess — suggest the Web-DeepSearch skill to the user.

A short brainstorm or a single-section polish is fine to leave in conversation. But once the content reaches formal-plan quality, don't just leave it there — decide where it lives. The default is Notion. Ask whether to continue into the Web-Publish skill to write it up there (if the Notion MCP isn't connected, offer a markdown file instead).

## 3. Check before delivering (do this yourself — no subagent)

Before handing over the document, check it yourself against "could someone else start working from this immediately?" Look for abstract claims ("user-friendly UI") that should be concrete criteria ("core feature reachable within 3 clicks"), and ask follow-up questions to fill in anything left vague.

**Be especially suspicious of the feature spec section.** If this is meant to be a formal plan but each feature only gets a sentence or two with no acceptance criteria (checklist), it's been summarized rather than actually filled in — don't stop at listing feature names; write down the actual bar a developer would use to call it "done." Skipping this check is how a document ends up looking polished on the surface but hollow underneath.

If this continues an in-progress plan, extend it without contradicting decisions already locked in.

## 4. A more thorough review is opt-in only, and goes through one reviewer

Once the formal plan is finished, don't automatically call a subagent. Spinning up even one subagent carries a fixed cost (tool-schema loading, etc.) — paying that fixed cost multiple times (several reviewers in parallel) for one short review task is wasteful. That's why the three lenses (UX, feature spec, BM) are consolidated into **one** `web-plan-reviewer`.

Offer it in one short line: "If you want a more thorough look, I can run a cross-check review — it'll take a bit longer." Only call `web-plan-reviewer` (via the Agent tool, **once**) if the user says yes. Pass the full draft as **inline text in the prompt**, not a file path — this keeps the reviewer from wandering off to find and read other files. The reviewer doesn't edit the draft, only returns findings; pull in only the ones actually worth applying.
