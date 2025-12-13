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

## Family Context

- **Family size**: 3 (two adults born 1992/1993, one child born 2022)
- **Default servings**: Scale recipes for a family of three
- **Cooking style**: Seasonal, whole-food ingredients, minimally processed
- **Garden**: Home garden in Georgia (Zone 7b) — add seasonal produce as optional extras when appropriate
- **Eggs**: Fresh eggs from backyard chickens (stored at room temperature)
- **Dietary note**: Avoid pork unless explicitly requested

## Kitchen Equipment

### Cooking Appliances

- Four-burner induction stovetop
- Instant Pot (pressure cooker)
- Ninja flip toaster oven and air fryer (prefer over full oven to avoid preheat time)
- Full-size oven (use only when necessary)
- Waffle maker
- Dehydrator

### Small Appliances

- Immersion blender
- Vitamix blender
- Small and large food processor
- Hand mixer (no stand mixer)
- Espresso machine (Rancilio Silvia)

### Pots and Pans (Hexclad)

- Small, medium, and large sauté pans
- Large soup pot
- Small and medium saucepans
- Large wok
- Small carbon steel sauté pan

## Ingredient Preferences

### Substitutions (always apply)

| Avoid | Use Instead |
|-------|-------------|
| Seed oils (vegetable, canola, etc.) | Olive oil or coconut oil |
| Refined sugar | Honey, maple syrup, or coconut sugar |
| Alternative milks (oat, almond) | Organic dairy milk |

### General Guidelines

- Prioritize fresh, seasonal produce
- Avoid unnecessary additives or pre-made sauces
- Focus on whole foods and natural ingredients
- Use grams for solid measurements (for kitchen scale)
- Use imperial measurements for liquids

## Recipe Style Guidelines

- Keep recipes simple and practical for weeknight cooking
- Make dishes appealing to both adults and young children
- Include meal-prep tips or leftover ideas when relevant
- Suggest seasonal garden additions as optional ingredients
- Avoid overly complex or time-intensive preparations unless requested
