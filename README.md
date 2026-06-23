# FIFA World Cup Match Predictor

## Project Goal

Build a **real Machine Learning project** from scratch that predicts the outcome of international football matches (win, draw, or loss for the home team).

You will learn the **complete ML pipeline** — not just how to call a library, but how professional teams actually build predictive systems.

---

## Current Progress

**Path A Phase 2 — Goalscorer Features** ✅ Complete

| Model | Accuracy | File |
|-------|----------|------|
| v1 (basic features) | ~52% | `models/match_predictor.joblib` |
| v2 (+ goalscorer form) | ~63% | `models/match_predictor_v2.joblib` |

| Milestone | Status |
|-----------|--------|
| 1 — Load & Explore Dataset | ✅ |
| 2 — Clean & Filter (Path A: 2021+) | ✅ |
| 3 — Feature Engineering | ✅ |
| 4 — Train & Evaluate First Model | ✅ |
| 5 — Goalscorer Features (Path A Phase 2) | ✅ |
| 6 — Retrain v2 Model | ✅ |

---

## What We Completed

| Step | Status |
|------|--------|
| Defined project goal | ✅ |
| Created folder structure | ✅ |
| Created README, LESSONS, TODO | ✅ |
| Downloaded `results.csv` to `data/raw/` | ✅ |
| Installed Python libraries | ✅ |
| Notebook 01 — Load & explore (49,477 matches) | ✅ |
| Notebook 02 — Clean & filter (5,711 matches, 2021+) | ✅ |
| Notebook 03 — Feature engineering (target + features) | ✅ |
| Notebook 04 — Train, evaluate, save, predict (~52% accuracy) | ✅ |
| Notebook 05 — Goalscorer features | ✅ |
| Notebook 06 — Retrain v2 (~63% accuracy) | ✅ |

---

## Why It Was Necessary

We followed the professional order: **understand data → clean → engineer features → split → train → evaluate → save → predict**.

Skipping any step would have meant training on dirty data, leaking scores into features, or not knowing if the model actually works.

---

## Folder Structure

```
worldcup_predictor/
│
├── README.md
├── LESSONS.md
├── TODO.md
├── requirements.txt
│
├── data/
│   ├── raw/
│   │   └── results.csv
│   └── processed/
│       ├── matches_2021_onwards.csv
│       └── matches_ready_for_model.csv
│
├── notebooks/
│   ├── 01_load_and_explore.ipynb
│   ├── 02_clean_and_filter.ipynb
│   ├── 03_feature_engineering.ipynb
│   └── 04_train_and_evaluate.ipynb
│
├── models/
│   └── match_predictor.joblib
│
└── src/                   ← future production code
```

---

## Technologies Used

| Technology | Role |
|------------|------|
| Python | Language |
| Jupyter | Interactive notebooks |
| Pandas | Data loading & cleaning |
| Scikit-learn | Train/test split, encoding, model, metrics |
| joblib | Save/load trained model |

---

## Next Objective

**Optional Phase 3:** Add formation / player stats when you find good datasets.

**Or:** Use v2 model to predict live matches with real rolling stats from recent games.
