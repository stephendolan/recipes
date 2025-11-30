---
description: "Generate a shopping list from one or more recipes"
allowed-tools: Glob, Read, Grep, Bash
argument-hint: "[recipe-names or 'all']"
---

Generate consolidated shopping list from specified recipes (or all if no args).

**Arguments:** $ARGUMENTS

Extract `@ingredient{quantity%unit}` patterns, skip `-@hidden`, consolidate quantities. Organize by `config/aisle.conf` sections if present. Output as markdown checklist with optional ingredients grouped separately.
