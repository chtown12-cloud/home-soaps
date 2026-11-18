# Home & Soaps

A personal recipe book for handmade skincare, haircare, soap and body care.

**Live site: https://chtown12-cloud.github.io/home-soaps/**

The site holds 35 recipes in seven categories: Skincare, Hair Care, Body Care, Bath Time, Lip Care, Soaps and Deodorants.

## Using the site

- **Units.** Switch between Metric, Imperial and Percent. Imperial shows ounces by weight, but amounts under 10 g stay in grams, because ounce readings are too coarse for them. Percent shows each ingredient's share of the batch. The site remembers your choice.
- **Batch size.** Scale a recipe from ½× to 4×. The amounts and the yield change together.
- **Ticks.** Tick off ingredients and steps as you go. Your browser keeps the ticks until you press *Reset ticks*.
- **Printing.** The print button prints the current recipe, including its batch size and yield.
- **Links.** Each recipe has its own link in the form `#category/recipe`, for example https://chtown12-cloud.github.io/home-soaps/#soaps/coldprocess.

## How it's built

Everything lives in one file, `index.html`: the styles, the recipe data and the script that builds the page. There is no build step, so you can preview a change by opening `index.html` in a browser.

GitHub Pages (GitHub's free static hosting) publishes the `main` branch. So a change usually goes live within a few minutes of being merged into `main`.

## Adding or editing a recipe

Recipes live in the `recipes` object, inside the script at the end of `index.html`. This is the lip balm, shortened:

```js
lipbalm: {
    category: 'lipcare',                  // the tab it appears under (see CATEGORIES)
    tab: 'Lip Balm',                      // the label on its button
    name: 'Beeswax Lip Balm',
    subtitle: 'Moisturizing protection for soft lips',
    difficulty: 'Easy',
    time: '15 min',
    makes: { count: 10, unit: 'tube' },   // optional; the weight is calculated
    ingredients: [
        { group: 'Melt Together' },       // optional divider
        { name: 'Beeswax', g: 15, info: 'Creates protective barrier (use candelilla for vegan)' },
        { name: 'Peppermint Essential Oil', drops: 8, info: 'Cooling and refreshing' },
    ],
    method: ['Set up double boiler with simmering water.', '…'],
    notes: ['Work quickly as mixture solidifies fast', '…'],
    shelfLife: '6–12 months. Anhydrous wax and oil blend — stable as long as stored away from heat.'
},
```

Write each amount once, as `g` (grams), `drops`, `capsules` or `pinches`, or as `asNeeded: true`. Don't add imperial amounts: the site calculates the imperial and percent views, and the yield, from these numbers. That's why they always agree.

Three optional fields add notes and warnings:

- `safety` on a recipe is a list, shown in a warning box above the ingredients.
- `safety` on an ingredient is a sentence that stays visible on its card.
- `info` on an ingredient is a note. Notes longer than 80 characters fold away behind *Show details*.

The tabs are built from this data, so a new recipe appears in its category with no other change.

## A note on safety

These are home recipes, not lab-tested formulas. Read each recipe's safety notes before you start, especially for cold process soap, which uses lye, and for the water-based products, which depend on a preservative and a pH check.
