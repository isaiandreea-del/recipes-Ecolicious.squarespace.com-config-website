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

SQUARESPACE + PAYMENTS
  Open GHID-Squarespace.html (full step-by-step guide: link the app, custom subdomain, sell Premium,
  send the access link to buyers, test order).
  Quick unlock link for buyers:  https://YOURNAME.github.io/ecolicious/?code=YOUR-CODE

PICTURES
  Every recipe has a watercolor-style illustration (drawn, not photos), stored inside recipes.json (the "image" field).
  To use a real photo, upload it next to index.html and set that recipe's "image" line in recipes.json to its file name.

HOW PREMIUM WORKS
  Free:    ingredient picker, recipe search, courses, cuisine, allergen / vegan / vegetarian labels,
           step-by-step instructions + cook mode.
  Premium: full nutrition (kcal, protein, carbs, fat, fibre, vitamins) + "Masa mea" meal totals,
           substitutes for missing ingredients, saving favourites, diet suggestions,
           avoiding ingredients and allergens.
  Premium is unlocked with an access code and remembered in the visitor's browser.
  Note: this is a soft lock. Someone technical could read premium.json directly.

MENU, LANGUAGE AND PICTURES (new)
  - Top menu (Recipes / Subscription / Contact us / FAQ / Login) and the TikTok + Instagram icons are set in index.html:
    NAV_LINKS, TIKTOK_URL, INSTAGRAM_URL (near the top of the script). Paths like "/abonament" are added to SQUARESPACE_URL.
    Create Squarespace pages with those URL slugs, or paste full addresses instead.
  - Language button (Română / English): all texts are in index.html; English recipes are in en.json.
  - Watercolor pieces are stored in art.js. Recipe pictures are built from those pieces ("pic" field in recipes.json).
    36 recipes still use the earlier simple illustration ("image" field) until you add a matching watercolor piece.
