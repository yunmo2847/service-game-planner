# Socratic Interview Technique (for planning interviews)

The Plan skills (Web-Plan, Game-Plan) don't just transcribe whatever the user asks for. They ask questions that lead the user to clarify their own decisions. The goal isn't interrogation — it's helping the user surface premises or contradictions they hadn't fully thought through themselves.

## Principles

**Ask before you answer.** When the user says "add a challenge feature," don't write it down immediately — ask why it's needed first. A single question like "Would the core value break without this, or is it just nice to have?" often sorts out priority on its own.

**Keep questions to 1-3 at a time.** "Socratic" doesn't mean firing off a barrage of questions. If answering feels like too much work, the user gives up on the process itself. One sharp question beats ten shallow ones.

**Dig into "why" at least once.** Confirming the real reason (why) behind the stated ask (what) is what lets you evaluate alternatives too. Example: "add a ranking system" → "Is the effect you want from ranking competitive drive, or social proof?" — the answer changes the design completely.

**When testing a premise, use a concrete scenario.** Instead of abstractly asking "is this really necessary?", attach a specific situation: "If there are only 100 users in the first week, does this ranking system still mean anything?" — concrete scenarios make it easier for the user to judge clearly.

**When the user gets stuck, stop asking and show a draft.** If they struggle to answer ("I don't know, just decide for me") or the conversation stalls, don't push for more answers. Present a draft with assumptions clearly labeled, and let them revise from there — it's much faster.

## Ask about BM (business model) early, and press on it

This skill set assumes, by default, that everyone building this eventually wants to make money from it. Early in the interview — right after concept/target are confirmed, before drafting the feature list — always ask once: "How does this make money? If monetization isn't the goal, what does 'success' mean for this project?"

The answer becomes the yardstick for feature priority later (which features connect directly to the monetization point). Don't bolt BM onto the end of the document as a formality — keep referring back to it throughout feature/system design.

## Example

**Bad (just transcribing):**
> User: Add a challenge feature.
> Claude: Sure, I'll add a challenge section. (goes straight to spec)

**Good (Socratic):**
> User: Add a challenge feature.
> Claude: Got it. Is this challenge meant to drive new-user retention, or to nudge payment (e.g. a paid-currency reward on clear)? The difficulty curve needs to be completely different depending on the goal.
