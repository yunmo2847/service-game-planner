---
name: Game-Publish
description: Use to publish a finished or near-finished web game GDD to a Notion page for at-a-glance viewing. Use for requests like "write this up in Notion", "put this GDD in Notion" ("노션에 정리해줘", "이 GDD 노션에 만들어줘"). Also suggest this as a save option right after Game-Plan wraps up.
---

# Game-Publish

Publishes web game plan content worked out via Game-Plan (and, if used, Game-DeepSearch, Game-BM, Game-Balance) as a page in a Notion database.

**Write the page content in the language the user is using with you (Korean by default).** These instructions are in English only for maintainability; it's not a cue to answer in English.

Follow the shared procedure in `../references/notion-publish-workflow.md`.

## Database

Name: **웹게임 기획 아카이브** (Web Game Plan Archive). Create it with this schema if it doesn't exist:

```
CREATE TABLE ("이름" TITLE, "상태" SELECT('아이디어':gray,'초안':yellow,'진행중':blue,'완료':green), "장르" SELECT('방치형':blue,'퍼즐':purple,'RPG':orange,'PvP/경쟁':red,'캐주얼':green,'기타':default), "BM 한줄요약" RICH_TEXT)
```

If the game doesn't fit an existing genre, use "기타" (other) — add a new option if needed.

## Page structure

Follow `../references/web-game.md`'s section order, re-expressed in Notion syntax:

- Sections 1-3 (overview, core loop, core mechanics) stay visible immediately on opening the page
- Section 9 (monetization) gets the fixed BM callout treatment
- The section-5 balancing table becomes a Notion table
- Sections that don't need to be seen every time — 7 (retention/live-ops), 10 (art & tone) — go in toggles

See `notion-publish-workflow.md` for the status-legend/color rules and the "don't shrink content" rule — both apply here without exception.

## Pass over the prose once before publishing

Once the page content is written, right before sending it to Notion, run it past the `../references/natural-writing.md` checklist once — no new call, no separate tool. Fix only the mechanically-repetitive or cliché sentences on the spot; leave the table/callout/toggle structure alone.

## After it's done

Give the user the created Notion page URL. If the content changes later, don't create a new page — update the same one.

If the GDD is genuinely finished (not just a draft), it's fine to mention the `marketer` agent as an option for turning it into a store listing/announcement post — but only offer it once, and only call it if the user actually asks.
