# Plate Ledger

A daily nutrition tracker that runs as a single-page web app. Log meals, measure them against your own calorie and macro targets, track water, and watch a 14-day trend. No account, no server: everything is stored in your browser, and you can export a JSON backup at any time.

## Features

- **Log by meal.** Breakfast, lunch, dinner and snacks, with servings that multiply per-serving values.
- **Built-in food library.** About 40 common foods, including Indian staples (roti, dal, idli, poha, paneer, rajma, biryani), with approximate values per serving. Type any other food with its own numbers.
- **My foods.** Tick "Save to my foods" when adding something and it becomes a one-tap chip.
- **Today at a glance.** Calorie ring, protein / carbs / fat / fiber bars, and the share of calories from each macro.
- **Nutrition Facts panel.** The day's totals in a food-label layout. The % Daily Value column is measured against your targets, not a generic 2,000 kcal diet.
- **Water.** Tap 250 ml glasses.
- **14-day trend.** Calories per day against the target line, with hover details, click-to-jump, and a table view.
- **Targets.** Edit daily kcal, macro and water goals.
- **Backup.** Export and import a JSON file to move your log between devices.
- **Installable.** Ships with a web manifest and a service worker, so it installs as an app on phones and desktops and opens offline.
- **Light and dark themes** follow the system setting.

## Run it

It is static HTML. Any of these work:

```bash
# Python
python -m http.server 8080

# Node
npx serve .
```

Then open http://localhost:8080. Opening `index.html` directly from the file system also works, but the service worker (offline support) only registers over http(s).

## Deploy

Push to GitHub and enable **Settings → Pages → Deploy from branch → main / (root)**. The app will be served at `https://<user>.github.io/plate-ledger/`.

## Data

Everything is kept in `localStorage` under the key `plate-ledger-v1`:

```json
{
  "targets": { "calories": 2000, "protein": 120, "carbs": 220, "fat": 65, "fiber": 30, "water": 8 },
  "days": { "2026-10-07": { "date": "2026-10-07", "entries": [ ... ], "water": 6 } },
  "foods": [ { "id": "...", "name": "...", "serving": "...", "cal": 0, "p": 0, "c": 0, "f": 0, "fi": 0 } ]
}
```

Clearing site data clears the log, so export a backup now and then.

## Food values

Library values are approximate per listed serving and meant as a starting point. Edit the numbers before adding when you have a packet label or a more precise source.
