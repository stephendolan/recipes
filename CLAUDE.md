# Recipes

Personal recipe collection using [Cooklang](https://cooklang.org/) markup language.

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

- **Folder name** = Category in app
- **File name** = Recipe title (e.g., `Chicken Stir Fry.cook`)
- **Images** in `images/` subfolder with matching name

## Cooklang Basics

Recipes use inline markup: `@ingredient{qty%unit}`, `#cookware{}`, `~{time%unit}`

For complete syntax reference, use the `cooklang-recipes` skill.

## CLI

```bash
brew install cooklang/tap/cook
cook server              # Browse at localhost:9080
cook shopping-list *.cook
cook doctor              # Validate syntax
```

## iOS Sync

Symlink to iCloud for Cooklang app:
```bash
ln -s ~/repos/recipes ~/Library/Mobile\ Documents/iCloud~org~cooklang~CooklangApp/Documents/recipes
```
