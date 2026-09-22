---
description: ""
---

# Web Service Notion Publish (Web-Publish)

This command is a thin dispatcher that lets `/service-game-planner:web-publish` work without loading the full Web-Publish skill description into context every session.

## Run

1. Read `skills/Web-Publish/SKILL.md` from the active plugin install location.
2. Follow that SKILL.md's instructions exactly, treating whatever the user typed as:

```text
$ARGUMENTS
```

If the file can't be found relative to the current working directory, look under the active plugin root instead and continue from there.
