---
description: ""
---

# 웹서비스 기획 (Web-Plan)

이 커맨드는 매 세션마다 Web-Plan 스킬 설명 전체를 컨텍스트에 올리지 않고도 `/service-game-planner:web-plan`을 바로 쓸 수 있게 해주는 얇은 디스패처다.

## 실행

1. 현재 활성화된 플러그인 설치 위치에서 `skills/Web-Plan/SKILL.md`를 읽는다.
2. 그 SKILL.md 지시를 그대로 따르고, 사용자가 입력한 인자를 다음으로 취급한다:

```text
$ARGUMENTS
```

현재 작업 디렉터리에서 파일을 바로 못 찾으면, 활성 플러그인 루트 아래에서 찾아 이어서 진행한다.
