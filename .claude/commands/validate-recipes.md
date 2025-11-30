---
description: "Validate all Cooklang recipes for syntax errors and best practices"
allowed-tools: Bash
---

Run the cook CLI validation commands:

```bash
cook doctor validate
cook doctor aisle
```

Report any warnings or errors found. For validation issues, show the file and line. For aisle issues, suggest additions to `config/aisle.conf`.
