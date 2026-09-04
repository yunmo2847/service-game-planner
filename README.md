# service-game-planner

웹서비스/웹게임 기획을 소크라테스식 질문으로 함께 설계하고, 실제 리서치와 수익모델(BM) 설계를 거쳐 노션에 한눈에 보이게 정리하는 [Claude Code](https://claude.com/claude-code) 플러그인입니다.

파편적인 아이디어("~한 서비스/게임을 만들고 싶어")를 그냥 받아적지 않고, 질문을 던져 스스로 결정을 명확히 하도록 돕습니다. 특히 수익모델(BM)을 문서 맨 끝에 형식적으로 붙이지 않고, 기능 우선순위를 정하는 기준으로 인터뷰 초반부터 다룹니다.

## 설치

Claude Code에서:

```
/plugin marketplace add yunmo2847/service-game-planner
/plugin install service-game-planner
```

## 포함된 스킬

| 스킬 | 하는 일 |
|---|---|
| `Web-Plan` / `Game-Plan` | 소크라테스식 질문으로 인터뷰 → 정식 PRD/GDD 정리 |
| `Web-DeepSearch` / `Game-DeepSearch` | 경쟁 서비스·레퍼런스·트렌드를 실제 웹 검색으로 조사, 결과를 `research/` 폴더에 저장 |
| `Web-BM` / `Game-BM` | 수익모델(BM)을 가격/전환/무과금 밸런스까지 깊게 설계 |
| `Game-Balance` | 재화 획득/소모, 성장 곡선 같은 게임 수치 밸런싱 |
| `Web-Publish` / `Game-Publish` | 완성된 기획을 노션(Notion) 페이지로 발행 — 표/콜아웃/토글로 한눈에 보이게 구조화 |

각 스킬은 대화 중 자연어로 자동 트리거되고("웹서비스 기획해줘" 등), 명시적으로 부르고 싶으면 `/service-game-planner:web-plan` 같은 슬래시 커맨드도 씁니다.

기획서 초안이 나온 뒤 더 꼼꼼한 교차검토가 필요하면(기본값은 아님, 비용이 들어가는 선택 사항) `web-plan-reviewer` / `game-plan-reviewer` 에이전트를 요청할 수 있습니다.

## 노션 연동

`Web-Publish`/`Game-Publish`는 Notion MCP가 연결되어 있어야 합니다. 연결이 안 되어 있으면 자동으로 마크다운 파일로 대체 제공합니다.

**주의**: 노션 무료 플랜은 블록(콘텐츠) 개수에 한도가 있습니다. 한도를 넘으면 새 페이지 발행이 막힐 수 있으니, 자주 쓸 계획이면 유료 플랜을 고려하거나 오래된 테스트 페이지를 주기적으로 정리하는 걸 권장합니다.

## 구조

```
.claude-plugin/
├── plugin.json       — 플러그인 매니페스트
└── marketplace.json  — 마켓플레이스 매니페스트 (이 저장소 자체가 마켓플레이스)
commands/    — 슬래시 커맨드 (skills/ 지시를 그대로 따르는 얇은 디스패처)
skills/      — 실제 스킬 로직 + 공유 참고자료(skills/references/)
agents/      — 옵트인 교차검토 에이전트
```

## 라이선스

MIT
