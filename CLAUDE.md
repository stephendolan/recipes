# Recipes

Personal recipe collection using [Cooklang](https://cooklang.org/) markup language.

See README.md for project structure, CLI usage, and iOS sync setup.

## Cooklang Basics

Recipes use inline markup: `@ingredient{qty%unit}`, `#cookware{}`, `~{time%unit}`

For complete syntax reference, use the `cooklang-recipes` skill.

## Recipe Content Standards

### Required Metadata

- `servings`: number or yield description
- `prep time`: duration in minutes
- `cook time`: duration in minutes (use `0 minutes` for no-cook recipes)
- `tags`: comma-separated (include meal type, dietary info, speed)

### Optional Metadata

- `difficulty`: easy, medium, hard
- `cuisine`: cuisine name
- `source`: URL if adapted from another recipe
- `author`: name if original creation

### Modifier Usage

- `-@ingredient`: Use for pantry staples (salt, pepper, cooking oil, water)
- `?@ingredient`: Use for garnishes and truly optional additions
- `&` or `&(=N)`: Use for ingredient references within recipe

### Category Guidelines

| Category | Contains |
|----------|----------|
| **Basics** | Building blocks used in other recipes (stocks, doughs, spice blends) |
| **Sauces** | Finished sauces served as-is (vinaigrettes, pesto, gravy) |
| **Sides** | Accompaniments to main dishes |
| **Breakfast/Lunch/Dinner** | Primary meal categorization |
| **Desserts/Drinks** | Self-explanatory |
