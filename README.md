# service-game-planner

A [Claude Code](https://claude.com/claude-code) plugin that designs web service/web game plans together through Socratic questioning, backs them with real research and business-model (BM) design, and organizes the result clearly in Notion.

It doesn't just transcribe a fragmented idea ("I want to build a service/game that does ~") — it asks questions so you clarify your own decisions. Business model (BM) in particular isn't bolted on as a formality at the end; it's raised early in the interview and used as the standard for prioritizing features.

The interview, the plan/GDD, the Notion pages, and every other output stay in whatever language you use with Claude (Korean by default for this project) — only the skill instructions themselves are written in English, for maintainability across a wider set of users.

## Install

In Claude Code:

```
/plugin marketplace add yunmo2847/service-game-planner
/plugin install service-game-planner
```

## Skills

| Skill | What it does |
|---|---|
| `Web-Plan` / `Game-Plan` | Socratic interview → formal PRD/GDD |
| `Web-DeepSearch` / `Game-DeepSearch` | Researches competitors, references, and trends via real web search, saved to `research/` |
| `Web-BM` / `Game-BM` | Designs the business model in depth — pricing, conversion, free-to-pay balance |
| `Game-Balance` | Numeric balancing — currency sources/sinks, growth curves |
| `Web-Publish` / `Game-Publish` | Publishes the finished plan to a Notion page — tables/callouts/toggles, and a consistent ✅/🔶/❓ (confirmed/assumption/open-question) status legend applied throughout instead of ad hoc emoji and heading colors |

Each skill triggers automatically from natural language in conversation ("plan a web service for me", "웹서비스 기획해줘"), or can be called explicitly with a slash command like `/service-game-planner:web-plan`.

## Agents (opt-in only)

These never run automatically — each is a deliberate, single, on-demand call, so the fixed cost of spinning up a subagent is only paid when it's actually useful:

| Agent | What it does |
|---|---|
| `web-plan-reviewer` / `game-plan-reviewer` | Cross-checks a finished draft across UX/feature-spec/BM (or core-loop/implementation/BM) lenses in one pass |
| `game-tester` | Mentally playtests a finished GDD — onboarding confusion, pacing spikes, exploitable balance loopholes |
| `marketer` | Turns a finished plan into a one-line pitch, landing/store copy, or a short announcement post |

Ask for these explicitly when you want them ("review this more carefully", "playtest this", "write me some marketing copy") — the skills mention them as options but never call them on their own.

## Connecting Notion

`Web-Publish`/`Game-Publish` need the Notion MCP connected. If it isn't, they fall back to a markdown file automatically and tell you so.

**Note**: Notion's free plan has a block (content) limit. Publishing a lot will eventually hit it — consider a paid plan for heavy use, or periodically clean up old test pages. To keep repeat publishing fast, the skills also cache each database's ID locally (`.service-game-planner-notion-cache.json` in your working directory) after the first search, so later publishes skip the repeat lookup.

## Structure

```
.claude-plugin/
├── plugin.json       — plugin manifest
└── marketplace.json  — marketplace manifest (this repo is its own marketplace)
commands/    — slash commands (thin dispatchers that just point at skills/)
skills/      — the actual skill logic + shared references (skills/references/)
agents/      — opt-in on-demand agents (reviewers, tester, marketer)
```

## License

MIT

---

## 한국어 안내

웹서비스/웹게임 기획을 소크라테스식 질문으로 함께 설계하고, 실제 리서치와 수익모델(BM) 설계를 거쳐 노션에 한눈에 보이게 정리하는 [Claude Code](https://claude.com/claude-code) 플러그인입니다.

파편적인 아이디어("~한 서비스/게임을 만들고 싶어")를 그냥 받아적지 않고, 질문을 던져 스스로 결정을 명확히 하도록 돕습니다. 특히 수익모델(BM)을 문서 맨 끝에 형식적으로 붙이지 않고, 기능 우선순위를 정하는 기준으로 인터뷰 초반부터 다룹니다.

인터뷰·기획서/GDD·노션 페이지 등 실제로 만들어지는 결과물은 전부 사용자가 쓰는 언어(이 프로젝트 기준 기본 한국어) 그대로 나갑니다 — 영어로 되어 있는 건 Claude에게 주는 스킬 지시문뿐이며, 더 다양한 사용자가 쓸 수 있도록 유지보수성을 위해 영어로 작성했습니다.

### 설치

```
/plugin marketplace add yunmo2847/service-game-planner
/plugin install service-game-planner
```

### 포함된 스킬

| 스킬 | 하는 일 |
|---|---|
| `Web-Plan` / `Game-Plan` | 소크라테스식 질문으로 인터뷰 → 정식 PRD/GDD 정리 |
| `Web-DeepSearch` / `Game-DeepSearch` | 경쟁 서비스·레퍼런스·트렌드를 실제 웹 검색으로 조사, 결과를 `research/` 폴더에 저장 |
| `Web-BM` / `Game-BM` | 수익모델(BM)을 가격/전환/무과금 밸런스까지 깊게 설계 |
| `Game-Balance` | 재화 획득/소모, 성장 곡선 같은 게임 수치 밸런싱 |
| `Web-Publish` / `Game-Publish` | 완성된 기획을 노션(Notion) 페이지로 발행 — 표/콜아웃/토글로 한눈에 보이게, 확정/가정/미정을 ✅/🔶/❓로 표기해 문서 전체에 일관되게 적용 (이모티콘·헤딩 색을 즉흥적으로 쓰지 않음) |

각 스킬은 대화 중 자연어로 자동 트리거되고("웹서비스 기획해줘" 등), 명시적으로 부르고 싶으면 `/service-game-planner:web-plan` 같은 슬래시 커맨드도 씁니다.

### 에이전트 (옵트인 전용)

자동으로는 절대 호출되지 않습니다 — 매번 사용자가 원할 때만 한 번씩 명시적으로 부르는 방식이라, 서브에이전트 고정비용은 실제로 필요할 때만 지불합니다:

| 에이전트 | 하는 일 |
|---|---|
| `web-plan-reviewer` / `game-plan-reviewer` | 완성된 초안을 UX/기능명세/BM(또는 코어루프/구현난이도/BM) 세 관점에서 한 번에 교차검토 |
| `game-tester` | 완성된 GDD를 머릿속으로 플레이해보며 온보딩 혼란, 페이싱 문제, 악용 가능한 밸런스 구멍을 짚음 |
| `marketer` | 완성된 기획을 한 줄 홍보 문구, 랜딩/스토어 카피, 짧은 홍보 게시물로 변환 |

"더 꼼꼼하게 검토해줘", "플레이테스트해줘", "마케팅 문구 뽑아줘"처럼 원할 때 직접 요청하세요 — 스킬이 옵션으로 제안은 하지만 스스로 부르지는 않습니다.

### 노션 연동

`Web-Publish`/`Game-Publish`는 Notion MCP가 연결되어 있어야 합니다. 연결이 안 되어 있으면 자동으로 마크다운 파일로 대체 제공합니다.

**주의**: 노션 무료 플랜은 블록(콘텐츠) 개수에 한도가 있습니다. 자주 쓸 계획이면 유료 플랜을 고려하거나 오래된 테스트 페이지를 주기적으로 정리하는 걸 권장합니다. 반복 발행 속도를 위해 스킬이 처음 검색한 데이터베이스 ID를 작업 폴더에 로컬로 캐싱해둡니다(`.service-game-planner-notion-cache.json`) — 이후 발행부터는 같은 검색을 반복하지 않습니다.

### 구조

```
.claude-plugin/
├── plugin.json       — 플러그인 매니페스트
└── marketplace.json  — 마켓플레이스 매니페스트 (이 저장소 자체가 마켓플레이스)
commands/    — 슬래시 커맨드 (skills/ 지시를 그대로 따르는 얇은 디스패처)
skills/      — 실제 스킬 로직 + 공유 참고자료(skills/references/)
agents/      — 옵트인 온디맨드 에이전트 (리뷰어, 테스터, 마케터)
```

### 라이선스

MIT
