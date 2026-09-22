---
description: ""
---

# Web Game BM Design (Game-BM)

This command is a thin dispatcher that lets `/service-game-planner:game-bm` work without loading the full Game-BM skill description into context every session.

## Run

1. Read `skills/Game-BM/SKILL.md` from the active plugin install location.
2. Follow that SKILL.md's instructions exactly, treating whatever the user typed as:

```text
$ARGUMENTS
```

If the file can't be found relative to the current working directory, look under the active plugin root instead and continue from there.
