# Publishing a Plan to Notion (shared workflow)

Shared procedure for the Web-Publish and Game-Publish skills. This skill moves and structures plan content that's already been worked out (or nearly finished) in the conversation into a Notion page — it doesn't invent new content.

**If Web-Plan/Game-Plan ran earlier in this same conversation, don't re-read `web-service.md`/`web-game.md`** — what that skill already read is still in context. Only re-read them if this is a new conversation, or the user pasted in an already-finished plan.

## 0. Confirm the Notion MCP is connected

This skill needs the Notion MCP tools (`notion-search`, `notion-create-pages`, etc.) to work. Connection status varies per user, so check first whether those tools are actually usable:

- If the tool names already appear in the tool list (even in deferred state), they're usable — proceed.
- If not, try a tool search with a keyword like `notion` / `notion-search`.
- If still not found, the Notion MCP isn't connected. **Never silently fall back to another format** — tell the user explicitly: "Notion isn't connected, so I can't create the page there directly. Want to connect Notion, or should I save this as a markdown file instead?" If they choose markdown, build the file following the `web-service.md`/`web-game.md` structure.

Skipping this check and calling the Notion tools directly just produces an opaque tool error for a user who isn't connected, with no explanation of why — that's what step 0 exists to prevent.

## 1. Find or create the target database

**Check the local cache first** — this is what keeps repeat publishing fast (see the caching note at the end of this section). Only fall back to a live search if there's no usable cache entry.

If no cache hit: search for the database name (specified by each skill) with `notion-search` first — the user may have used this skill before. If it exists, confirm the schema with `notion-fetch` and reuse it. If this database was already found or created earlier in this same conversation (e.g. a page was just published a moment ago), reuse that result — don't search again.

If it doesn't exist, create it with the schema each skill specifies. **Don't set a parent** — this skill is used by many different users across their own separate Notion workspaces, so hardcoding a specific parent page would break for everyone else. Omitting parent creates it at the top level of the workspace as a private page, which is the safe default. The one exception: if the user already pointed at a specific location in conversation ("put it under the OO page"), use that as parent.

When a new database is created, use the data source ID from the response (the `<data-source>` tag) as the parent when creating pages in it.

**Cache it locally for next time — this is the main speed fix.** After a successful search-and-find or create, write the database name → `{database_id, data_source_id}` mapping to `.service-game-planner-notion-cache.json` in the current working directory (create the file if it doesn't exist; add to it rather than overwriting if it already has other entries). Before step 1 runs again — whether later in this conversation or in a future session, in the same working directory — read this file first. A cache hit skips straight to page creation, which is what actually cuts publish time: the `notion-search` + `notion-fetch` round trips are pure overhead once the database already exists and its schema hasn't changed. If a cached ID turns out to be stale (page creation fails because the database was deleted or moved), fall back to a live search and overwrite that entry in the cache.

## 2. Convert content into Notion markdown

The table below is the entire block syntax this skill actually uses. **If this covers what's needed, don't re-fetch the full spec doc** (`notion://docs/enhanced-markdown-spec`) — that doc is mostly audio/video/tabs/columns/synced-block content this skill never touches, and pulling it in full on every publish burns tokens for no reason. Only fall back to the full spec when something outside this table is genuinely needed (audio, embeds, inline database views, etc.).

| Block | Syntax |
|---|---|
| Heading | `# text`, `## text`, `### text` |
| Table | `<table header-row="true"><tr><td>cell</td></tr></table>` — cells hold plain text only, no nested blocks |
| Callout | `<callout icon="💰" color="yellow_bg">`\n`\ttext`\n`</callout>` — children are tab-indented |
| Toggle | `<details>`\n`<summary>title</summary>`\n`\tcontent`\n`</details>` |
| To-do | `- [ ] text` / `- [x] text` |
| Code block | ` ```language ... ``` ` |
| Bold/italic | `**text**` / `*text*` |

Indentation uses tabs, not spaces. Table cells can't contain block elements like headings or lists — text only.

**Don't put a `{color=...}` tag on headings or body text.** Color is reserved for the BM callout only (see the fixed style rules below) — this is what keeps every published page visually consistent instead of each publish picking colors ad hoc.

## 3. Fixed style rules — consistency in the content, not just the container

The page icon is free to pick per project — that part doesn't need standardizing, and forcing one fixed icon on every page isn't the point. What actually made past pages inconsistent with each other was the **content-level notation**: whether a page marks which statements are confirmed, which are assumptions, and which are still open — and if so, whether it does that the same way every time. These rules fix that:

- **Every page states a status legend once, in the opening callout, and uses it consistently for the rest of the page**: `✅` confirmed/decided, `🔶` assumption or draft proposal (not yet validated), `❓` open question (still needs a decision). Attach the relevant marker to specific claims, table rows, and list items throughout the page — not just in one section — so a reader can tell at a glance what's locked in versus still soft. This mirrors how Web-Plan/Game-Plan and Web-DeepSearch/Game-DeepSearch already distinguish confirmed facts from guesses; carrying that same distinction into the Notion page (instead of flattening everything to the same confident tone) is the actual point of this rule.
- **Don't add a `{color=...}` tag to headings just for visual variety.** A different color per section with no fixed meaning behind it (section 1 red, section 2 blue, section 3 purple, etc.) is decoration, not information, and it's exactly the kind of thing that makes one page look different from the next for no reason. If a heading's content is genuinely a warning or a decision point, say so in the text or use a callout — don't lean on rotating colors to do that work.
- **BM/monetization callout**: always `icon="💰"`, always `color="yellow_bg"` — this one callout is worth a fixed, memorable treatment since it's the section users care most about scanning for.
- **Priority tables, balancing tables**: rendered as real Notion tables (not toggled, not summarized into prose) — always visible on open.
- **Secondary sections** (non-functional requirements, competitor analysis, retention/live-ops, art & tone, etc. — anything not needed on every read): wrapped in a toggle, collapsed by default.

**A toggle/callout/table changes the container, not the amount of content.** Specific content from the original doc — acceptance criteria checklists in particular — gets moved over item by item, not compressed into "a summary callout of the key points." Putting something in a toggle doesn't mean shortening the text inside it — it's collapsed, but expanding it should show the same length as the source. If the Notion page has less content than the source markdown, something was moved over wrong.

## 4. Pass over the prose once before publishing

Once the page content is written, right before sending it to Notion, run it past the `natural-writing.md` checklist once. No new call, no separate tool — just look at what was just written and fix only the mechanically-repetitive or cliché parts on the spot. Leave the table/callout/toggle structure alone.

## 5. Report the result

Give the user the created Notion page URL. If the content changes later (e.g. "I reworked the balancing, update the Notion doc too"), don't create a new page — update the same one with `notion-update-page`.
