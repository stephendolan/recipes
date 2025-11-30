# Recipes

Personal recipe collection in [Cooklang](https://cooklang.org/) format.

## Quick Start

```bash
# Clone
git clone <repo-url> ~/repos/recipes

# Symlink for iOS app (macOS)
ln -s ~/repos/recipes ~/Library/Mobile\ Documents/iCloud~org~cooklang~CooklangApp/Documents/recipes

# Or use CLI
brew install cooklang/tap/cook
cook server  # Browse at localhost:9080
```

## Structure

```
recipes/
├── Breakfast/
├── Lunch/
├── Dinner/
├── Desserts/
├── Sides/
├── Sauces/
├── Drinks/
├── Basics/
└── config/
    └── aisle.conf
```

## Claude Code Commands

| Command | Purpose |
|---------|---------|
| `/new-recipe` | Create a new recipe file |
| `/import-recipe` | Import from URL to Cooklang |
| `/validate-recipes` | Check syntax and best practices |
| `/shopping-list` | Generate shopping list |

## Documentation

See [CLAUDE.md](CLAUDE.md) for project conventions and Cooklang basics.
