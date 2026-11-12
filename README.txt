ECOLICIOUS – recipe finder
==========================

FILES (keep this folder structure when you upload to GitHub):
  index.html          the website
  recipes.json        136 recipes (edit / add recipes here)
  premium.json        nutrition values + substitutes (Premium)
  ingredients.json    the ingredient list shown on the clipboard
  assets/             logo, chinchilla, wood texture, favicon
  fonts/              Quicksand font

3 SETTINGS TO FILL IN  (open index.html, find "SETĂRI" near the top of the <script>)
  SQUARESPACE_URL       your Squarespace site address. The logo and the "← Înapoi pe site" button link there.
  PREMIUM_PRODUCT_URL   the page of your Premium product in Squarespace (the "Cumpără Premium" button opens it).
  PREMIUM_CODES         access codes you give to people who paid, e.g. ["ECO-7F3K9", "ECO-Q82LM"].
                        Change the default PREMIUM2026 before you go live.

ADDING A PHOTO TO A RECIPE
  Put the image in a new folder "images/" and add this line to the recipe in recipes.json:
      "image": "images/my-photo.jpg",
  Recipes without a photo show an emoji on the sticky note.

HOW PREMIUM WORKS
  Free:    ingredient picker, recipe search, courses, cuisine, allergen / vegan / vegetarian labels,
           step-by-step instructions + cook mode.
  Premium: full nutrition (kcal, protein, carbs, fat, fibre, vitamins) + "Masa mea" meal totals,
           substitutes for missing ingredients, saving favourites, diet suggestions,
           avoiding ingredients and allergens.
  Premium is unlocked with an access code and remembered in the visitor's browser.
  Note: this is a soft lock. Someone technical could read premium.json directly.
