# Recipes

Personal recipe collection using [Cooklang](https://cooklang.org/) markup language.

See README.md for project structure, CLI usage, and iOS sync setup.

## Cook CLI

The `cook` command-line tool manages recipes:

```bash
cook doctor validate          # check all recipes for errors
cook doctor aisle             # find missing aisle.conf entries
cook shopping-list <files>    # generate shopping list
cook recipe "<path>"          # display a recipe
cook recipe "<path>:2"        # scale recipe (double)
cook server                   # browse recipes in web UI
cook search "<term>"          # search recipes
```

Always run `cook doctor validate` after editing recipes.

## Cooklang Basics

Recipes use inline markup: `@ingredient{qty%unit}`, `#cookware{}`, `~{time%unit}`

For complete syntax reference, use the `cooklang-recipes` skill.

## Recipe Content Standards

### Required Metadata

- `servings`: number only (e.g., `4` not `4 servings`)
- `prep time`: duration in minutes
- `cook time`: duration in minutes (use `0 minutes` for no-cook recipes)
- `tags`: comma-separated (include meal type, dietary info, speed)

### Optional Metadata

- `difficulty`: easy, medium, hard
- `cuisine`: cuisine name
- `source`: URL if adapted from another recipe
- `author`: name if original creation

### Syntax Rules

- Section headers use `= Section Name` (not `>>`)
- Ingredients must have `{}` even when empty: `-@salt{}` not `-@salt`
- Time ranges: `~{2%minutes} to ~{3%minutes}` (not `~{2-3%minutes}`)

### Modifier Usage

- `-@ingredient{}`: Pantry staples (salt, pepper, cooking oil, water)
- `?@ingredient{}`: Garnishes and truly optional additions
- `&ingredient`: Reference earlier ingredient in recipe

### Category Guidelines

| Category | Contains |
|----------|----------|
| **Basics** | Building blocks used in other recipes (stocks, doughs, spice blends) |
| **Sauces** | Finished sauces served as-is (vinaigrettes, pesto, gravy) |
| **Sides** | Accompaniments to main dishes |
| **Breakfast/Lunch/Dinner** | Primary meal categorization |
| **Desserts/Drinks** | Self-explanatory |
