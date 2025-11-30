---
description: "Import a recipe from a URL and convert to Cooklang format"
allowed-tools: WebFetch, Read, Write, Glob, Bash
argument-hint: "<url> [category]"
---

Import recipe from URL and convert to Cooklang format.

**Arguments:** $ARGUMENTS

## Process

1. Fetch the recipe URL and extract:
   - Title, servings, prep time, cook time
   - Ingredients with quantities
   - Instructions

2. Convert to Cooklang syntax:
   - YAML frontmatter with metadata
   - Mark ingredients (`@`), cookware (`#`), timers (`~`)
   - Use `-@` for pantry staples, `?@` for optional
   - Add preparations in parentheses

3. Save to `<Category>/<Recipe Title>.cook`

4. Validate with `cook recipe "<path>"` to check syntax

5. Run `cook doctor aisle` to check for missing ingredients in aisle.conf

## Alternative

The cook CLI has a built-in import (requires OPENAI_API_KEY):
```bash
cook import "<url>"
```
