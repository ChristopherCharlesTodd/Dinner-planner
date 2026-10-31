# Meal Draw

A single-page app that draws a week of dinners or protein shakes at random, shows the recipe for each, and builds a shopping list with a Waitrose search link for every item.

It is one `index.html` file with no build step and no dependencies.

## Features

- **Two modes:** switch between Dinners and Protein shakes with the toggle at the top. Each mode keeps its own plan.
- **Random draw:** choose how many meals (2–7 dinners, 1–7 shakes), then draw a new set.
- **Swap:** replace any single meal you don't fancy.
- **Recipes:** expand any meal to see its ingredients and method.
- **Shopping list:** ingredients are combined across the plan and grouped by aisle. Tick items off as you shop, copy the list, or tap **Find** to search for the item on Waitrose.
- **Saved in your browser:** your plan and ticked items are remembered between visits, using `localStorage`.

## Running it

Open `index.html` in a browser, or use the **Live Server** extension in VS Code (right-click the file, then **Open with Live Server**).

## Adding or editing recipes

All the content is in the script at the bottom of `index.html`.

Dinners go in the `MEALS` list:

```js
["Recipe name",
  [["Ingredient", 400, "g", "M"], ["Another ingredient", 2, "", "P"]],
  ["First step.", "Second step."]
]
```

Shakes go in the `SHAKES` list, with an approximate protein figure in grams added at the end:

```js
["Shake name",
  [["Protein powder", 30, "g", "C"], ["Semi-skimmed milk", 250, "ml", "D"]],
  ["First step.", "Second step."],
  35
]
```

Each ingredient is `[name, quantity, unit, aisle]`. Use `"g"` or `"ml"` for the unit, or `""` for whole items.

Aisle codes:

| Code | Aisle |
|------|-------|
| `M` | Meat and fish |
| `P` | Fruit and veg |
| `D` | Dairy and eggs |
| `B` | Bakery |
| `C` | Cupboard |
| `F` | Frozen |

## Portion sizes

Dinner recipes are written for four adults. The `sc()` function scales them down for a smaller household (currently by a factor of 0.7). Change the `f` value in that function to suit your own household. Shakes are one serving each and are not scaled.

## Notes

- Protein figures for shakes are estimates, based on about 24g of protein per 30g scoop of powder. Check your own tub.
- Quantities in the shopping list are a guide, so check what you already have before shopping.
