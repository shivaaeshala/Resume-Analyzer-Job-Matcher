# Design: Expanded Skills List + Portfolio README

**Date:** 2026-04-14
**Project:** Resume Analyzer & Job Matcher

---

## Goals

1. Expand the hardcoded `SKILL_LIST` in `app.py` and make it file-driven (loaded from `skills.json`)
2. Replace the empty `README.md` with a polished, portfolio-focused README that includes screenshot placeholders

---

## 1. Skills List — Categorized JSON

### File: `skills.json` (new, project root)

A single JSON object where each key is a category and each value is an array of skill strings (all lowercase, matching the pattern used by `extract_skills()`).

**Categories:**

| Category | Example Skills |
|---|---|
| `programming_languages` | python, java, c++, r, scala, go, rust, typescript, kotlin, swift |
| `web_frameworks` | flask, django, fastapi, react, angular, vue, node.js, express, spring boot |
| `databases` | sql, mysql, postgresql, mongodb, redis, sqlite, cassandra, elasticsearch, firebase |
| `ml_ai` | machine learning, deep learning, nlp, computer vision, generative ai, llm |
| `ml_libraries` | scikit-learn, tensorflow, pytorch, keras, hugging face, xgboost, opencv |
| `data_tools` | pandas, numpy, matplotlib, seaborn, tableau, power bi, spark, hadoop, airflow |
| `devops_cloud` | docker, kubernetes, jenkins, git, github, github actions, ci/cd, aws, azure, gcp, terraform |
| `mobile` | android, ios, flutter, react native |
| `testing` | pytest, selenium, jest, unit testing |
| `soft_skills` | communication, problem solving, leadership, teamwork, agile, scrum |

### Change to `app.py`

Remove the hardcoded `SKILL_LIST` constant. Replace with:

```python
import json

with open("skills.json") as f:
    _skills_data = json.load(f)
SKILL_LIST = [skill for category in _skills_data.values() for skill in category]
```

All downstream functions (`extract_skills`, `improve_resume_suggestions`) use `SKILL_LIST` unchanged — no other modifications needed.

---

## 2. README

### File: `README.md` (full rewrite)

**Sections (in order):**

1. **Header** — Title + shields.io badges for Python version, Streamlit, spaCy, scikit-learn
2. **Overview** — 2–3 sentences: what the app does, who it's for, why it's useful
3. **Features** — Bullet list: PDF resume parsing, TF-IDF match scoring, skill gap detection, resume section feedback, improvement suggestions, dynamic skill list via JSON
4. **Tech Stack** — Markdown table: Tool | Purpose
5. **Project Structure** — Code-fenced file tree: `app.py`, `skills.json`, `requirements.txt`, `screenshots/`
6. **Screenshots** — 3 image embeds with descriptive captions and placeholder paths:
   - `screenshots/upload_screen.png`
   - `screenshots/score_result.png`
   - `screenshots/skills_feedback.png`
7. **Getting Started** — Prerequisites + step-by-step install + run command
8. **How It Works** — Short technical paragraph on TF-IDF similarity and regex skill extraction
9. **Future Improvements** — 4 ideas: DOCX support, AI-powered suggestions, job board API integration, visual skill gap chart

### File: `screenshots/.gitkeep` (new)

Empty file to commit the `screenshots/` directory so placeholder image paths are valid. User replaces with actual screenshots after running the app.

---

## Out of Scope

- No changes to the similarity algorithm or UI layout
- No new Streamlit components
- No license section
- Screenshots are placeholders only — user takes their own

---

## Implementation Order

1. Create `skills.json`
2. Update `app.py` to load from `skills.json`
3. Create `screenshots/.gitkeep`
4. Rewrite `README.md`
