# Recipes

Personal recipe collection using [Cooklang](https://cooklang.org/) markup language.

## Cooklang Syntax

Cooklang uses inline markup within natural recipe instructions:

```
Crack the @eggs{3} into a blender, add the @flour{125%g},
@milk{250%ml} and @salt{1%pinch}, and blend until smooth.

Pour into a #frying pan{} and cook for ~{2%minutes} on each side.
```

### Markers

| Marker | Purpose | Example |
|--------|---------|---------|
| `@` | Ingredient | `@salt` or `@salt{1%tsp}` |
| `#` | Cookware | `#pot` or `#pot{large}` |
| `~` | Timer | `~{15%minutes}` |

### Ingredient Format

```
@ingredient{quantity%unit}
```

- `@butter` - just the ingredient
- `@butter{2%tbsp}` - with quantity and unit
- `@eggs{3}` - quantity without unit

### Metadata

Add metadata at the top of `.cook` files:

```
>> source: https://example.com/recipe
>> servings: 4
>> time: 30 minutes
>> tags: breakfast, quick
```

### Comments

```
-- This is a single line comment

[- This is a
   multi-line comment -]
```

### Steps

Blank lines separate steps. Each paragraph becomes a numbered step in the app.

## Directory Structure

```
recipes/
├── CLAUDE.md
├── README.md
├── config/
│   └── aisle.conf        # Shopping list aisle organization
├── Breakfast/
│   ├── Pancakes.cook
│   └── images/
│       └── Pancakes.jpg
├── Dinner/
│   ├── Pasta Carbonara.cook
│   └── images/
│       └── Pasta Carbonara.jpg
└── Desserts/
    └── Chocolate Cake.cook
```

### Key Points

- **Folders = Categories** in the app
- **File name = Recipe name** (without `.cook` extension)
- **Images**: Place in `images/` subfolder, matching the recipe filename
- Supports nested folders for sub-categories

## iOS App Sync

The Cooklang iOS app ("Cook") syncs via iCloud Drive:

```
~/Library/Mobile Documents/iCloud~org~cooklang~CooklangApp/Documents/
```

### Sync Strategy

Since recipes live in a Git repo, use a symlink or sync script:

```bash
# Option 1: Symlink the whole repo (macOS)
ln -s ~/repos/recipes ~/Library/Mobile\ Documents/iCloud~org~cooklang~CooklangApp/Documents/recipes

# Option 2: Rsync script
rsync -av --delete ~/repos/recipes/ ~/Library/Mobile\ Documents/iCloud~org~cooklang~CooklangApp/Documents/
```

## Aisle Configuration

Create `config/aisle.conf` to organize shopping lists by store section:

```
produce: garlic|lettuce|tomato|onion|pepper
dairy: milk|butter|cream|cheese|eggs
meat: chicken|beef|pork|bacon|sausage
pantry: flour|sugar|salt|oil|vinegar
spices: paprika|cumin|oregano|basil
frozen: ice cream|frozen
```

Each line: `aisle name: regex|patterns|separated|by|pipes`

## Editing Tools

- **VS Code**: Install "Cooklang" extension for syntax highlighting
- **Obsidian**: Use "Cooklang Editor" plugin
- **Vim/Neovim**: Community syntax files available

## Resources

- [Cooklang Spec](https://cooklang.org/docs/spec/)
- [iOS App](https://apps.apple.com/us/app/cooklangapp/id1598799259)
- [Example Recipes](https://github.com/cooklang/awesome-cooklang-recipes)
