# Interview Prep

A flashcard-style study app for data engineering interviews. No build step, no framework — just open `index.html`.

## How to run

```
open index.html
```

> **Note:** Browsers block `fetch()` on `file://` URLs. If questions don't load, run a local server:
> ```
> npx serve .
> # then open http://localhost:3000
> ```

## How to add a question

Edit the relevant file in `data/` and reload the page.

```json
{
  "id": "spark-006",
  "question": "Your question here.",
  "answer": "Markdown answer. `inline code` and fenced blocks work.",
  "difficulty": "easy",
  "tags": ["tag1", "tag2"]
}
```

`difficulty` must be `easy`, `medium`, or `hard`.

## How to add a category

1. Create `data/{your-id}.json` with a questions array (see schema above).
2. Add an entry to `data/_categories.json`:
   ```json
   { "id": "your-id", "name": "Display Name", "icon": "🔥" }
   ```
3. Reload.

## How to deploy to GitHub Pages

1. Push the repo to GitHub.
2. Go to **Settings → Pages**.
3. Set **Source** to `Deploy from a branch`, branch `master`, root `/`.
4. GitHub Pages serves the static files — the app works as-is since everything is client-side.

## Progress storage

Progress is saved in `localStorage` under the key `interview_prep`. Clear browser storage to reset.
