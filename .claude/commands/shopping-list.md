---
description: "Generate a shopping list from one or more recipes"
allowed-tools: Bash, Glob
argument-hint: "[recipe-names or 'all']"
---

Generate shopping list using the cook CLI.

**Arguments:** $ARGUMENTS

## Usage

For specific recipes, find the .cook file paths and run:
```bash
cook shopping-list "Category/Recipe Name.cook" "Category/Other Recipe.cook"
```

For all recipes:
```bash
cook shopping-list *.cook */*.cook
```

Scaling: append `:N` to scale (e.g., `"Dinner/Pasta.cook:2"` for double).

The output organizes ingredients by aisle sections from `config/aisle.conf`.
