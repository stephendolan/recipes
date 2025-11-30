# Recipes

Personal recipe collection in [Cooklang](https://cooklang.org/) format.

## Quick Start

```bash
# Clone
git clone <repo-url> ~/repos/recipes
cd ~/repos/recipes

# Enable pre-commit hooks
git config core.hooksPath .githooks

# Install cook CLI
brew install cooklang/tap/cook  # macOS
# or download from https://github.com/cooklang/cookcli/releases

# Browse recipes
cook server  # localhost:9080
```

## iOS Sync (macOS)

```bash
ln -s ~/repos/recipes ~/Library/Mobile\ Documents/iCloud~org~cooklang~CooklangApp/Documents/recipes
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
├── config/
│   └── aisle.conf      # Shopping list organization
├── bin/
│   └── validate        # Recipe validation script
└── .githooks/
    └── pre-commit      # Validates recipes before commit
```

## Development

```bash
# Validate all recipes
./bin/validate

# Or use cook directly
cook doctor validate    # Check syntax
cook doctor aisle       # Check ingredient mappings
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
