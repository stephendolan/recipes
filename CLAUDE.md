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

- Section headers use `= Section Name` (not `#`, `##`, or `>>`)
- Ingredients must have `{}` even when empty: `-@salt{}` not `-@salt`
- Time ranges: `~{2%minutes} to ~{3%minutes}` (not `~{2-3%minutes}`)
- Comments use `-- text` (not markdown `Notes:` sections)

### Ingredient Format

The `%` separates quantity from unit. Preparation goes in a second `{}` block.

```
@ingredient{quantity%unit}{preparation}
```

Correct examples:
- `@black beans{1%lb}{dry, rinsed}` — quantity: 1, unit: lb, prep: dry, rinsed
- `@garlic{5%cloves}{smashed}` — quantity: 5, unit: cloves, prep: smashed
- `@fire-roasted tomatoes{14%oz}{diced}` — use hyphens for compound names
- `@broth{4%cups}` — no preparation needed
- `-@salt{}` — hidden pantry staple, no quantity
- `?@sour cream{1%dollop}` — optional, note the `?@` prefix

Common mistakes:
- `@garlic{5-6|cloves smashed}` — WRONG: `|` is not valid, use `%` for unit and `{}` for prep
- `@beans{1 lb}` — WRONG: missing `%` between quantity and unit
- `?sour cream{dollop}` — WRONG: missing `@` after `?`

### Modifier Usage

- `-@ingredient{}`: Pantry staples (salt, pepper, cooking oil, water)
- `?@ingredient{}`: Garnishes and truly optional additions (must include `@`)
- `&ingredient`: Reference earlier ingredient in recipe

### Category Guidelines

| Category | Contains |
|----------|----------|
| **Basics** | Building blocks used in other recipes (stocks, doughs, spice blends) |
| **Sauces** | Finished sauces served as-is (vinaigrettes, pesto, gravy) |
| **Sides** | Accompaniments to main dishes |
| **Breakfast/Lunch/Dinner** | Primary meal categorization |
| **Desserts/Drinks** | Self-explanatory |
