---
description: "Create a new Cooklang recipe file with proper structure and metadata"
argument-hint: "<category> <recipe-name>"
allowed-tools: Read, Write, Glob
---

Create a new Cooklang recipe at `<Category>/<Recipe Name>.cook`.

**Arguments:** $ARGUMENTS

If user provides recipe details, convert to Cooklang format. Otherwise create template with YAML frontmatter and placeholder steps.
