# Generate Your Personal Interview Questions

A prompt you run once in Claude or ChatGPT with your CV attached. The output drops directly into this app.

---

## How to use

1. Open [Claude](https://claude.ai) or ChatGPT
2. Upload your CV (PDF or paste the text)
3. Copy the prompt below and send it
4. Copy the JSON output into `data/personal.json`
5. Add `{ "id": "personal", "name": "My Experience", "icon": "🙋" }` to `data/_categories.json`
6. Refresh the app — your personal category appears in the sidebar

> **Tip:** Add `data/personal.json` to your `.gitignore` so your personal questions stay private if you fork this repo.

---

## The Prompt

```
I'm attaching my CV. Generate a JSON array of 20 personalized interview questions based on my specific experience — not generic ones.

Every question must reference something concrete from my background: a project, a technology choice, a metric, a team situation, or a career decision.

Output ONLY a valid JSON array — no explanation, no markdown fences. Start with [ and end with ].

Schema for each object:
{
  "id": "personal-001",
  "question": "Specific question referencing something from my CV.",
  "answer_guidance": "150-300 words of coaching on how to structure MY answer. Include: what a strong answer covers, a STAR structure suggestion, what interviewers penalize, and one key phrase I should include. Reference specific details from my CV.",
  "what_they_are_probing": "1-2 sentences: what is the interviewer actually assessing?",
  "difficulty": "easy" | "medium" | "hard",
  "tags": ["2-4 lowercase tags"]
}

Difficulty mix: exactly 4 easy, 12 medium, 4 hard.

Coverage — include at least one question on each of:
- Why I made key career transitions
- Each major project or role mentioned
- Technical decisions I made and the tradeoffs involved
- Metrics I claimed (probe how I measured them and what levers I used)
- A leadership or mentoring moment if I mention one
- Something that went wrong or I'd do differently (at least 2)
- The hardest technical problem I faced in a specific project
- A decision I made that someone could reasonably disagree with

Quality rules:
- Probe the numbers: "reduced costs by 25%" → ask exactly how that was measured and what changed
- Probe ownership: what did I decide vs what was decided above me?
- Probe failure: every real project has something that didn't go as planned
- Be specific to me: "tell me about your Spark experience" is rejected — "your CV mentions migrating 50+ pipelines, which was the hardest and why?" is correct
- The 4 hard questions must be genuinely uncomfortable: challenging a claim, asking about regret, or forcing a real tradeoff

Output ONLY the JSON array.
```

---

## Expected output format

```json
[
  {
    "id": "personal-001",
    "question": "Your CV mentions reducing pipeline runtime by 50% after migrating to Databricks — what specifically changed in the architecture that drove that reduction?",
    "answer_guidance": "**What a strong answer includes:**\n- The specific bottleneck before migration (e.g. scheduling overhead, sequential execution, resource contention)\n- The concrete architectural change (Medallion refactoring, Delta Live Tables, Photon enabled, cluster right-sizing)\n- How you measured the before/after (Airflow task duration logs, Databricks run metrics)\n- A number that grounds it: average runtime went from X min to Y min across the 50 pipelines\n\n**STAR structure:**\n- Situation: on-prem Airflow + MinIO with aging pipeline fleet\n- Task: migrate 50+ pipelines without breaking downstream consumers\n- Action: which specific changes you made to the architecture (be precise)\n- Result: 50% runtime reduction — and what that unlocked for the team\n\n**What interviewers penalize:**\n- Vague attribution ('Databricks is just faster')\n- Claiming the full result without owning specific decisions\n- Not knowing the before/after numbers\n\n**Key phrase:** 'The main lever was...' followed by one specific thing.",
    "what_they_are_probing": "Whether the candidate understands WHY the migration improved performance, or just executed it without understanding the mechanism.",
    "difficulty": "medium",
    "tags": ["databricks", "performance", "migration", "delta-lake"]
  }
]
```

---

## After you get the output

The JSON goes directly into `data/personal.json`. No editing needed unless you want to tweak a question. The `answer_guidance` field is coaching notes — it tells you how to build your answer from your own experience, not a script to memorize.

Practice the hard questions out loud. Those are the ones that decide the offer.