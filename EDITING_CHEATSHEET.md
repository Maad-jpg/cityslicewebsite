# City Slice — Editing Cheatsheet

Everything customers see and everything the chatbot knows lives in **one file**: `data.json`.

You never need to touch `index.html` or `api/chat.js` for content changes.

## How to edit

1. Open your GitHub repo
2. Click `data.json`
3. Click the pencil (top right)
4. Make your change
5. Scroll down, click **Commit changes**
6. Vercel redeploys in about 60 seconds

## Where to find things in data.json

| I want to change... | Look for... |
|---|---|
| Store hours | `"hoursDisplay"` and `"hoursPromptText"` |
| Phone / email / socials | `"business"` section |
| Buildings that get free delivery | `"freeDeliveryBuildings"` |
| Payment methods | `"payment"` |
| A slice price | `"menu" → "slices"` |
| A whole pizza price | `"menu" → "whole"` |
| A combo | `"menu" → "combos"` |
| A drink | `"menu" → "drinks"` |
| A dessert | `"menu" → "desserts"` |
| Add-ons / toppings | `"addOns"` |
| Current promos | `"promotions"` |
| An FAQ answer | `"faqs"` |
| A deflection response | `"deflections"` |
| Agent names in chat | `"agents"` |

## Adding a new menu item

Find the section (say `slices`) and add a new entry with the same shape as the ones around it:

```json
{
  "tag": "New",
  "name": "Truffle Slice",
  "desc": "Black truffle, mozzarella, honey drizzle.",
  "priceDineIn": 395,
  "priceDelivery": 425
}
```

Put a comma at the end of the previous item. No comma after the last item in the list.

## Removing a menu item

Delete the whole `{ ... }` block for that item, plus the comma before or after it.

## The one thing that can break the site

JSON is unforgiving about **commas** and **quote marks**. If the site menu shows "Menu temporarily unavailable" after an edit, it means the JSON is malformed. Common culprits:

- Missing comma between two items
- Extra comma after the last item
- Missing quote mark
- Curly quotes (" ") instead of straight quotes (" ")

Fix: revert your commit on GitHub (Commits → previous commit → Revert), then try the edit again more carefully.

## What still lives in index.html

- Visual design and layout
- The chatbot's tone/personality rules (out-of-scope handling, sensitive topic rules)
- The greeting message

Come back to me if any of those need changing.
