---
description: "Write and edit Cooklang recipe files. Use when creating, editing, converting, or validating recipes. Covers ingredient markup, cookware, timers, metadata, modifiers, and recipe organization."
---

# Cooklang Recipe Writing

## Cook CLI

The `cook` command-line tool manages recipes. Key commands:

| Command | Purpose |
|---------|---------|
| `cook recipe "<path>"` | Parse and display a recipe |
| `cook recipe "<path>:2"` | Scale recipe by factor |
| `cook shopping-list <files>` | Generate shopping list |
| `cook doctor validate` | Check all recipes for errors |
| `cook doctor aisle` | Find ingredients missing from aisle.conf |
| `cook server` | Browse recipes in web interface |
| `cook search "<term>"` | Search recipes |

### Recipe Display

```bash
cook recipe "Dinner/Pasta.cook"           # display recipe
cook recipe "Dinner/Pasta.cook:2"         # double the quantities
cook recipe "Dinner/Pasta.cook" -f json   # output as JSON
cook recipe "Dinner/Pasta.cook" -f markdown  # output as Markdown
```

### Shopping Lists

```bash
cook shopping-list "Dinner/Pasta.cook"                    # single recipe
cook shopping-list "Dinner/Pasta.cook" "Dinner/Soup.cook" # multiple
cook shopping-list "Dinner/Pasta.cook:2"                  # scaled
cook shopping-list */*.cook                               # all recipes
```

### Validation

```bash
cook doctor validate   # syntax errors and warnings
cook doctor aisle      # missing aisle.conf entries
```

## Core Syntax

### Markers

| Marker | Purpose | Examples |
|--------|---------|----------|
| `@` | Ingredient | `@salt`, `@butter{2%tbsp}`, `@eggs{3}` |
| `#` | Cookware | `#pot`, `#frying pan{}`, `#bowl{large}` |
| `~` | Timer | `~{15%minutes}`, `~resting{30%minutes}` |

### Ingredient Format

```
@ingredient                    -- name only
@ingredient{quantity}          -- with quantity (no unit)
@ingredient{quantity%unit}     -- with quantity and unit
@multi-word ingredient{}       -- multi-word names need braces
```

Examples:
- `@butter` - name only
- `@eggs{3}` - quantity without unit
- `@flour{250%g}` - quantity with unit
- `@ground black pepper{}` - multi-word ingredient
- `@olive oil{2%tbsp}` - multi-word with quantity

### Preparations

Add prep instructions in parentheses:

```
@onion{1}(diced)
@garlic{3%cloves}(minced)
@chicken{500%g}(cut into cubes)
```

### Modifiers

| Modifier | Purpose | Example |
|----------|---------|---------|
| `-` | Hidden from shopping list | `-@salt{to taste}` |
| `?` | Optional ingredient | `?@nuts{1%cup}` |
| `&` | Reference earlier ingredient | `&flour` |

### Timer Formats

```
~{15%minutes}           -- exact time
~{2%minutes} to ~{3%minutes}  -- time range (preferred)
~{30%seconds}           -- short durations
~resting{10%minutes}    -- named timer
```

## Recipe Structure

### Metadata (YAML Frontmatter)

```yaml
---
servings: 4
source: https://example.com/recipe
prep time: 15 minutes
cook time: 30 minutes
tags: dinner, quick, vegetarian
cuisine: Italian
difficulty: easy
---
```

Required: `servings` (must be a number, not "4 servings")

Optional: `source`, `author`, `prep time`, `cook time`, `tags`, `cuisine`, `difficulty`

### Steps

Blank lines separate steps. Each paragraph becomes a numbered step:

```
Preheat #oven{} to 375°F.

Mix @flour{2%cups} and @sugar{1%cup} in a #bowl{large}.

Bake for ~{25%minutes} until golden.
```

### Sections

For complex recipes with multiple parts, use `=`:

```
= Sauce

Mix @soy sauce{3%tbsp} with @honey{1%tbsp}.

= Stir Fry

Cook @chicken{1%lb} in -@oil{2%tbsp}.
```

### Notes

Personal tips with `>`:

```
> Don't overmix the batter
> Works best with room temperature butter
```

### Comments

```
-- Single line comment (not shown in output)

[- Multi-line
   comment block -]
```

## Conversion Guidelines

| Original | Cooklang |
|----------|----------|
| 1 cup flour | `@flour{1%cup}` |
| 2 large eggs | `@eggs{2%large}` |
| salt to taste | `-@salt{to taste}` |
| 1/2 cup butter, softened | `@butter{1/2%cup}(softened)` |
| medium saucepan | `#saucepan{medium}` |
| cook for 20 minutes | `cook for ~{20%minutes}` |
| cook 2-3 minutes | `cook ~{2%minutes} to ~{3%minutes}` |

## Quality Checklist

- [ ] All ingredients marked with `@`
- [ ] Multi-word ingredients have `{}`
- [ ] Quantities include units where applicable
- [ ] Cookware marked with `#`
- [ ] Timers added for cooking steps
- [ ] Servings is a number (not "4 servings")
- [ ] Steps separated by blank lines
- [ ] Section headers use `=` not `>>`
- [ ] Pantry staples use `-@`
- [ ] Source credited if adapted

## File Organization

- Filename becomes recipe title in apps
- Use Title Case: `Chocolate Chip Cookies.cook`
- Place in category folder: `Desserts/Chocolate Chip Cookies.cook`
- Categories: Breakfast, Lunch, Dinner, Sides, Sauces, Desserts, Drinks, Basics

## Aisle Configuration

`config/aisle.conf` organizes shopping lists by store section:

```
[produce]
garlic|garlic clove|garlic cloves
onion|onions|yellow onion|red onion
bell pepper|peppers|green bell pepper|red bell pepper

[dairy]
butter|unsalted butter|salted butter
eggs|egg|large eggs|egg whites

[pantry]
flour|all-purpose flour|bread flour
```

Use `|` for synonyms that map to the same item.

Run `cook doctor aisle` after adding recipes to find missing entries.

## Resources

- [Cooklang Spec](https://cooklang.org/docs/spec/)
- [CLI Documentation](https://cooklang.org/cli/)
