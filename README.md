# Interview Prep

A flashcard-style study app for data engineering interviews, covering Apache Spark, Kafka, Airflow, dbt, Databricks, AWS, Kubernetes, Terraform, system design, and behavioral questions.

Zero dependencies — no build step, no framework. Open `index.html` and study.

---

## Getting Started

### Option 1 — Open directly

```bash
open index.html
```

> **Note:** Browsers block `fetch()` on `file://` URLs. If questions fail to load, use a local server (Option 2).

### Option 2 — Local server (recommended)

```bash
npx serve .
# Open http://localhost:3000
```

---

## Question Schema

Each question file in `data/` is a JSON array. Every entry follows this schema:

```json
{
  "id": "spark-006",
  "question": "Your question here.",
  "answer": "Markdown answer. `inline code` and fenced blocks work.",
  "difficulty": "easy",
  "tags": ["tag1", "tag2"]
}
```

| Field | Type | Values |
|---|---|---|
| `id` | string | Unique identifier (e.g. `spark-006`) |
| `question` | string | The question text |
| `answer` | string | Markdown-formatted answer |
| `difficulty` | string | `easy`, `medium`, or `hard` |
| `tags` | array | Arbitrary topic tags |

---

## Adding Content

### Add a question

Edit the relevant file in `data/` and reload the page.

### Add a category

1. Create `data/{your-id}.json` containing a JSON array of questions (schema above).
2. Register it in `data/_categories.json`:
   ```json
   { "id": "your-id", "name": "Display Name", "icon": "🔥" }
   ```
3. Reload the page.

### Generate personal questions

See [personal-questions.md](personal-questions.md) for instructions on generating interview questions tailored to your background.

---

## Deploying to GitHub Pages

1. Push the repository to GitHub.
2. Navigate to **Settings → Pages**.
3. Set **Source** to `Deploy from a branch`, branch `master`, folder `/`.
4. The app is fully client-side — no server configuration required.

---

## Progress Tracking

Study progress is persisted in `localStorage` under the key `interview_prep`. To reset all progress, clear your browser's local storage for the site.
