---
description: "Import a recipe from a URL and convert to Cooklang format"
allowed-tools: WebFetch, Read, Write, Glob
argument-hint: "<url> [category]"
---

Import recipe from URL and convert to Cooklang format.

**Arguments:** $ARGUMENTS

Extract recipe metadata and ingredients, convert to Cooklang syntax with YAML frontmatter. Mark ingredients (`@`), cookware (`#`), timers (`~`), and preparations. Save to `<Category>/<Recipe Title>.cook`.
