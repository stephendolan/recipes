---
description: "Write and edit Cooklang recipe files. Use when creating, editing, converting, or validating recipes. Covers ingredient markup, cookware, timers, metadata, modifiers, and recipe organization."
---

# Cooklang Recipe Writing

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
| `&` | Reference earlier quantity | `@&flour{100%g}` |

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

Keys: `title`, `servings`, `source`, `author`, `prep time`, `cook time`, `tags`, `cuisine`, `difficulty`, `diet`

### Steps

Blank lines separate steps. Each paragraph becomes a numbered step:

```
Preheat #oven{} to 375°F.

Mix @flour{2%cups} and @sugar{1%cup} in a #bowl{large}.

Bake for ~{25%minutes} until golden.
```

### Sections

For complex recipes with multiple parts:

```
= Sauce

Mix @soy sauce{3%tbsp} with @honey{1%tbsp}.

= Stir Fry

Cook @chicken{1%lb} in @oil{2%tbsp}.
```

### Notes

Personal tips with `>`:

```
> Don't overmix the batter
> Works best with room temperature butter
```

### Comments

```
-- Single line comment

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

## Quality Checklist

- [ ] All ingredients marked with `@`
- [ ] Multi-word ingredients have `{}`
- [ ] Quantities include units where applicable
- [ ] Cookware marked with `#`
- [ ] Timers added for cooking steps
- [ ] Metadata includes servings
- [ ] Steps separated by blank lines
- [ ] Source credited if adapted

## File Organization

- Filename becomes recipe title in apps
- Use Title Case: `Chocolate Chip Cookies.cook`
- Place in category folder: `Desserts/Chocolate Chip Cookies.cook`
- Images in `images/` subfolder with matching name

## Aisle Configuration

`config/aisle.conf` organizes shopping lists:

```
[produce]
garlic
onion|onions|yellow onion
bell pepper|peppers

[dairy]
butter|unsalted butter
eggs|egg|large eggs
```

Use `|` for synonyms that map to the same item.

## Resources

- [Cooklang Spec](https://cooklang.org/docs/spec/)
- [CLI Documentation](https://cooklang.org/cli/)
