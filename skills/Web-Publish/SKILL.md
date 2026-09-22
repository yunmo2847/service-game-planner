---
name: Web-Publish
description: Use to publish a finished or near-finished web service plan to a Notion page for at-a-glance viewing. Use for requests like "write this up in Notion", "put this plan in Notion" ("노션에 정리해줘", "이 기획서 노션에 만들어줘"). Also suggest this as a save option right after Web-Plan wraps up.
---

# Web-Publish

Publishes web service plan content worked out via Web-Plan (and, if used, Web-DeepSearch, Web-BM) as a page in a Notion database.

**Write the page content in the language the user is using with you (Korean by default).** These instructions are in English only for maintainability; it's not a cue to answer in English.

Follow the shared procedure in `../references/notion-publish-workflow.md`.

## Database

Name: **웹서비스 기획 아카이브** (Web Service Plan Archive). Create it with this schema if it doesn't exist:

```
CREATE TABLE ("이름" TITLE, "상태" SELECT('아이디어':gray,'초안':yellow,'진행중':blue,'완료':green), "카테고리" SELECT('SaaS':blue,'커머스':orange,'커뮤니티':purple,'크리에이터툴':pink,'관리자툴':gray,'기타':default), "BM 한줄요약" RICH_TEXT)
```

If the service doesn't fit an existing category, use "기타" (other) — add a new option if needed.

## Page structure

Follow `../references/web-service.md`'s section order, re-expressed in Notion syntax:

- Sections 1-3 (overview, target, core features) stay visible immediately on opening the page
- Section 8 (monetization/BM) gets the fixed BM callout treatment
- The section-3 priority table and section-6 feature spec (if present) become Notion tables
- Sections that don't need to be seen every time — 7 (non-functional requirements), 10 (competitors) — go in toggles

See `notion-publish-workflow.md` for the status-legend/color rules and the "don't shrink content" rule — both apply here without exception.

## Pass over the prose once before publishing

Once the page content is written, right before sending it to Notion, run it past the `../references/natural-writing.md` checklist once — no new call, no separate tool. Fix only the mechanically-repetitive or cliché sentences on the spot; leave the table/callout/toggle structure alone.

## After it's done

Give the user the created Notion page URL. If the content changes later, don't create a new page — update the same one.

If the plan is genuinely finished (not just a draft), it's fine to mention the `marketer` agent as an option for turning it into a pitch/landing copy/announcement post — but only offer it once, and only call it if the user actually asks.
