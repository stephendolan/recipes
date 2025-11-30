---
description: "Validate all Cooklang recipes for syntax errors and best practices"
allowed-tools: Glob, Read, Grep
---

Find all `.cook` files and validate:
- Syntax: proper `@ingredient{}`, `#cookware{}`, `~{timer}` format
- Metadata: YAML frontmatter with servings
- Best practices: steps separated, ingredients marked, timers included

Report issues by category with suggested fixes.
