# Lessons — Learning Journal

Every new concept, library, and Python function is documented here as we encounter it.
Read this file anytime you forget what something means.

---

## Lesson 1: What Is a Machine Learning Project?

### What it is
A Machine Learning (ML) project is a software project where a computer **learns patterns from past data** to make predictions on new data — without being explicitly programmed with rules.

### Why it exists
Humans cannot write rules for every possible situation (e.g., "if team A has 80% win rate AND team B is tired AND it's raining → team A wins"). There are too many variables. ML lets the computer find those patterns automatically.

### Where it is used
- Netflix recommending movies
- Banks detecting fraud
- Doctors predicting disease risk
- **Our project:** Predicting World Cup match outcomes

### Simple analogy
Imagine you watched 500 football matches and took notes. Over time, you start noticing patterns: "Strong home teams usually win." ML does the same thing — but with thousands of matches and dozens of variables, much faster than a human.

### Real-world example
Amazon does not manually write "if user bought a tent, recommend sleeping bags." Their ML model learned that pattern from millions of purchase histories.

### Common beginner mistakes
- Jumping straight to "train a model" without understanding the data
- Treating ML like magic instead of a structured engineering process
- Memorizing library syntax without understanding the pipeline

---

## Lesson 2: The ML Pipeline (The Complete Journey)

### What it is
The **ML pipeline** is the ordered list of steps every ML project follows — from raw data to a working prediction.

### Why it exists
Without a pipeline, projects become chaotic. Every professional ML team follows the same structure.

### The 11 Steps (Our Roadmap)

```
1.  Load Dataset        → Bring data into Python
2.  Explore Dataset     → Understand what we have
3.  Clean Data          → Fix errors and inconsistencies
4.  Handle Missing Values → Fill in or remove empty cells
5.  Feature Engineering → Create useful input columns
6.  Train/Test Split    → Separate data for learning vs. testing
7.  Choose Model        → Pick the right algorithm
8.  Train               → Let the model learn patterns
9.  Evaluate            → Measure how good the model is
10. Save Model          → Store it for later use
11. Predict             → Use the model on new matches
```

### Simple analogy
Think of baking a cake:
1. Buy ingredients (Load data)
2. Check expiry dates (Explore)
3. Wash the fruit (Clean)
4. Replace missing eggs (Handle missing values)
5. Pre-mix dry ingredients (Feature engineering)
6. Set aside a slice to taste-test later (Train/test split)
7. Choose oven temperature (Choose model)
8. Bake (Train)
9. Taste and rate (Evaluate)
10. Store leftover batter recipe (Save model)
11. Bake another cake tomorrow (Predict)

### Common beginner mistakes
- Skipping exploration and cleaning ("the model will figure it out")
- Testing on the same data used for training (called **data leakage** — we will explain this when we reach that step)

---

## Lesson 3: Key Terms (First Introduction)

We will re-explain each term in depth when we actually use it. This is your glossary preview.

| Term | One-Line Meaning |
|------|-----------------|
| **Feature** | An input column the model uses to make a prediction (e.g., team ranking) |
| **Target** | The answer we want the model to predict (e.g., match result: win/draw/loss) |
| **Model** | The "brain" that learns patterns from features to predict the target |
| **Training** | Showing the model past data so it learns patterns |
| **Inference** | Using a trained model to predict new, unseen data |
| **Accuracy** | How often the model is correct (we will use better metrics too) |

> Terms like epoch, loss, precision, recall, normalization, etc. will be explained when we need them — not before.

---

## Lesson 4: Project Folder Structure (Why Each Folder Exists)

### What it is
A standardized layout so anyone on the team knows where to find things.

### Why it exists
In real companies, ML projects have multiple people working on them. A clear structure prevents chaos.

### Folder purposes

| Folder | Purpose |
|--------|---------|
| `data/raw/` | Original data. **Never edit this.** Like a photo negative — you always keep the original. |
| `data/processed/` | Cleaned, ready-to-use data. Safe to regenerate from raw. |
| `notebooks/` | Interactive exploration. Where we learn and experiment. |
| `src/` | Clean, reusable Python functions. Production code lives here. |
| `models/` | Saved trained models. Like saving a game — you can reload later. |

### Simple analogy
A kitchen: `raw/` is the grocery store delivery, `processed/` is pre-chopped ingredients, `notebooks/` is your recipe experiments, `src/` is the final recipe card, and `models/` is the finished dish in the fridge.

### Common beginner mistakes
- Putting everything in one file
- Modifying raw data directly (always keep originals)
- Not separating exploration (notebooks) from production code (`src/`)

---

## Lesson 5: Jupyter Notebook

### What it is
An interactive document that mixes **explanations** (markdown cells) and **code** (code cells). You run one cell at a time and see results immediately.

### Why it exists
Perfect for learning and exploring data. You can see output step by step instead of running an entire script.

### Where it is used
- Data exploration (our first notebooks)
- Prototyping before writing production code
- Teaching and documentation

### Simple analogy
A lab notebook where you write the hypothesis (markdown), run the experiment (code), and record the result — all on the same page.

### Common beginner mistakes
- Running cells out of order (always run top to bottom on first pass)
- Forgetting to restart the kernel after big changes

---

---

## Lesson 6: What Is a Dataset?

### What it is
A **dataset** is a collection of information stored in rows and columns — like a spreadsheet. Each **row** is one example (one football match). Each **column** is one piece of information about that match (date, team names, scores).

### Why it exists
Machine Learning needs **examples to learn from**. No data = no learning. The quality of your predictions depends heavily on the quality of your dataset.

### Where it is used
Every ML project starts with a dataset. Ours will live in `data/raw/` and never be edited.

### Simple analogy
A dataset is like a **match history book**. Each page (row) records one game. The columns are: date, home team, away team, final score, tournament name.

### Real-world example
Netflix's dataset has millions of rows — one row per user-movie interaction. Our dataset will have thousands of rows — one row per international football match.

### Common beginner mistakes
- Choosing a dataset that does not match your problem (e.g., player stats when you need match results)
- Downloading and immediately deleting the original file
- Picking a format that is hard to open (avoid exotic formats as a beginner; use **CSV**)

---

## Lesson 7: CSV File Format

### What it is
**CSV** stands for **Comma-Separated Values**. It is a plain text file where each row is one line, and columns are separated by commas. It opens in Excel, Google Sheets, and Python (Pandas).

### Why it exists
It is the simplest, most universal data format. Almost every data platform can export CSV.

### Example (what the inside of a CSV looks like)
```
date,home_team,away_team,home_score,away_score,tournament
2022-11-20,Qatar,Ecuador,0,2,FIFA World Cup
2022-11-21,England,Iran,6,2,FIFA World Cup
```

### Simple analogy
A CSV is like a **plain text shopping list** — no fancy formatting, just values separated by commas. Any program can read it.

### Common beginner mistakes
- Saving as `.xlsx` (Excel) when CSV is simpler for Python
- Opening CSV in Excel, editing it, and accidentally breaking the format
- Putting the file in the wrong folder (always go in `data/raw/`)

---

## Lesson 8: Features vs Target (First Deep Explanation)

### Feature (Input)
A **feature** is any column the model **uses to make a prediction**. It is information you would know **before or during** the match.

Examples for our project:
- `home_team` — who is playing at home
- `away_team` — who is the opponent
- `tournament` — World Cup, friendly, etc.
- (Later we will create) `home_team_avg_goals` — average goals scored by home team

### Target (Output / Label)
The **target** is the column we want the model to **predict**. It is the **answer**.

For our project, the target is **match outcome for the home team**:
- `Win` — home team scored more
- `Draw` — same score
- `Loss` — home team scored less

We will **create** this target column from `home_score` and `away_score` — the raw scores are not the target themselves; the Win/Draw/Loss label is.

### Simple analogy
**Features** = clues on a quiz sheet (team names, rankings, past form).
**Target** = the answer you are trying to guess (who won?).

### Common beginner mistakes
- Using the target column as a feature (the model would "cheat" — it already knows the answer)
- Confusing features with the target
- Not having enough features (only team names may not be enough — we will engineer more later)

---

---

## Lesson 9: pip and requirements.txt

### What it is
**pip** is Python's package installer. It downloads libraries (like pandas) from the internet into your Python environment.

**requirements.txt** is a text file listing every library the project needs, with minimum version numbers.

### Why it exists
Without pip, you would manually download dozens of files. `requirements.txt` lets anyone set up the project with one command:

```bash
pip install -r requirements.txt
```

### Where it is used
Every professional Python/ML project has a `requirements.txt` (or similar file like `pyproject.toml`).

### Simple analogy
**requirements.txt** = a shopping list.
**pip** = the delivery service that brings everything on the list to your kitchen.

### Common beginner mistakes
- Installing libraries one by one without recording them
- Forgetting to run pip install before opening the notebook
- Using the wrong Python version (always use the same Python for pip and notebooks)

---

## Lesson 10: Pandas (pd)

### What it is
**Pandas** is a Python library for working with tabular data (rows and columns). Its main object is the **DataFrame** — a table in memory.

### Why it exists
Python alone cannot easily read CSV files or filter thousands of rows. Pandas makes data work as simple as Excel formulas.

### Where it is used
- Loading CSV/Excel files
- Filtering, sorting, grouping data
- Handling missing values
- Almost every ML project's data step

### Key functions we use in Notebook 01

| Function | What it does |
|----------|-------------|
| `pd.read_csv(path)` | Loads a CSV file into a DataFrame |
| `df.head()` | Shows first 5 rows |
| `df.shape` | Returns (number of rows, number of columns) |
| `df.columns` | Lists column names |
| `df.info()` | Summary of columns, types, missing values |
| `df.describe()` | Statistics for numeric columns |
| `df["column_name"]` | Selects one column |
| `df[mask]` | Filters rows where mask is True |

### Simple analogy
Pandas is **Excel inside Python** — but you can automate everything with code instead of clicking.

### Common beginner mistakes
- Calling the variable `data` instead of `df` (both work, but `df` is the industry standard)
- Not checking `df.shape` after loading (you might load an empty file silently)
- Modifying `data/raw/` files instead of working on copies

---

## Lesson 11: NumPy (np)

### What it is
**NumPy** provides fast math operations on large arrays of numbers.

### Why it exists
Pure Python loops are slow on big datasets. NumPy runs calculations in optimized C code under the hood.

### Where it is used
- Behind pandas (pandas uses NumPy internally)
- ML model training (scikit-learn uses NumPy arrays)
- We rarely import it directly at the start — but it must be installed

### Simple analogy
If pandas is the spreadsheet, NumPy is the **calculator engine** inside it.

### Common beginner mistakes
- Thinking you must master NumPy before pandas (you don't — learn as you go)

---

## Lesson 12: import Statement (Python)

### What it is
```python
import pandas as pd
```
This line **loads a library** so you can use its functions. `as pd` gives it a short nickname.

### Why it exists
Libraries contain thousands of functions. `import` brings them into your notebook.

### Common beginner mistakes
- Forgetting to run the import cell first (you get `NameError: name 'pd' is not defined`)
- Typo in library name (`import panda` instead of `import pandas`)

---

## Lesson 13: pathlib.Path

### What it is
```python
from pathlib import Path
DATA_PATH = Path("..") / "data" / "raw" / "results.csv"
```
**Path** builds file paths using `/` instead of hard-coded backslashes. Works on Windows and Mac.

### Why it exists
Hard-coded paths like `"C:\\Users\\..."` break when someone else runs your code. Relative paths from the project root are portable.

### Simple analogy
Path is a **GPS for files** — you give directions relative to where you are, not absolute addresses.

---

---

## Lesson 14: Missing Values

### What it is
A **missing value** is an empty cell in your dataset — no score, no team name, no date. In pandas, missing cells show as `NaN` (Not a Number).

### Why it exists
Real-world data is messy. Websites go down, records get lost, humans forget to enter data. Every dataset has some gaps.

### Where it is used
The cleaning step (step 4 in our pipeline). You must decide: drop the row, fill with a default, or impute (estimate) the value.

### Simple analogy
A attendance sheet with blank names. You can't grade a student whose name is missing — you either find their name or skip that row.

### Real-world example
Our dataset has **44 matches** with missing scores. We drop them because we cannot know who won.

### Common beginner mistakes
- Ignoring missing values and training anyway (crashes or wrong results)
- Filling scores with 0 (teaches the model that "no score" means 0 goals — wrong!)
- Not checking *which* columns have missing values

---

## Lesson 15: Data Cleaning

### What it is
**Data cleaning** means fixing errors, removing bad rows, and keeping only the data relevant to your problem.

### Why it exists
Raw data is never ready for a model. Cleaning turns messy input into reliable input.

### Where it is used
After exploration, before feature engineering. We save cleaned data to `data/processed/`.

### Simple analogy
Washing vegetables before cooking. You remove dirt, cut off bad parts, keep only what you need.

### Real-world example
We had 9,868 "World Cup" matches but most were **qualifiers**, not the actual World Cup. Cleaning means filtering to exactly `FIFA World Cup` → 1,036 matches.

### Common beginner mistakes
- Editing the raw file (never do this)
- Using `.str.contains("World Cup")` when you need an exact match
- Not saving cleaned data to a new file

---

## Lesson 16: raw/ vs processed/

### What it is
| Folder | Purpose |
|--------|---------|
| `data/raw/` | Original download — **never modified** |
| `data/processed/` | Cleaned, filtered data — safe to regenerate from raw |

### Why it exists
If cleaning code has a bug, you can delete `processed/` and rerun. Raw data is always your backup.

### Simple analogy
**raw/** = original photo. **processed/** = edited version for Instagram. You always keep the original.

---

## Lesson 17: dropna() and to_csv()

### dropna(subset=["col1", "col2"])
Removes rows where listed columns have missing values.

### to_csv(path, index=False)
Saves a DataFrame to a CSV file. `index=False` avoids saving row numbers as a column.

### .copy()
Creates an independent copy of a DataFrame so changes don't accidentally affect the original.

---

---

## Lesson 18: What Is a Jupyter Notebook? (Deep Explanation)

### What it is
A **Jupyter Notebook** is a file ending in `.ipynb` that contains **cells** — small blocks you run one at a time.

Two cell types:
| Type | Contains | Purpose |
|------|----------|---------|
| **Markdown cell** | Text, headings, explanations | Teach / document what you are doing |
| **Code cell** | Python code | Run logic and see output below the cell |

### Why it exists
ML is experimental. You try something, see the result, adjust, try again. Notebooks let you do that without rerunning an entire script.

### Where it is used
- Learning and exploration (our project)
- Data science teams prototyping before production code

### Simple analogy
A **lab workbook**: each page section has instructions (markdown) and a space to run the experiment (code). You fill it in step by step.

### How to create one yourself (no AI needed)

**Method 1 — In Jupyter (recommended for beginners):**
1. Run `jupyter notebook` in terminal
2. Click **New → Python 3**
3. First cell: change type to **Markdown** (dropdown), write your explanation
4. Add new cell: write Python code
5. **File → Save As** → name it `02_clean_and_filter.ipynb`

**Method 2 — In VS Code / Cursor:**
1. Create new file: `something.ipynb`
2. Click **+ Code** or **+ Markdown** to add cells
3. Save

**Method 3 — Generative AI helps you write the content:**
You describe the step; AI gives markdown + code; you paste into cells and run.

### What is inside the `.ipynb` file?
It is JSON (structured text) storing each cell. You rarely edit the JSON by hand — you use Jupyter or Cursor.

### Common beginner mistakes
- Running cells out of order
- Putting all code in one giant cell (split into logical sections)
- No markdown explanations (future you will not remember why)

---

## Lesson 19: Using Generative AI to Build Notebooks

### What it is
**Generative AI** (ChatGPT, Claude, Cursor, etc.) generates text and code from your description. It does **not** automatically run files on your computer unless connected to tools (that would be "agentic" behavior).

### Why it exists
Speeds up writing boilerplate — imports, load CSV, filter logic — so you focus on understanding.

### Good prompt template for notebook sections

```
I am a beginner building an ML project.
Create ONE section for a Jupyter notebook.

Section goal: [e.g. filter matches from 2021 onwards]
Input file: data/raw/results.csv
Columns available: date, home_team, away_team, home_score, away_score, tournament

Give me:
1. A markdown cell (explanation for a beginner)
2. A Python code cell (with comments on every line)
3. Expected output
4. Common mistakes
```

### What YOU must always do after AI generates code
1. **Read** every line — do not blind copy-paste
2. **Run** one cell at a time
3. **Check** output matches expected
4. **Fix** paths (`data/raw/`) for your folder structure
5. **Ask** "why" if you do not understand a line

### Simple analogy
Generative AI is a **junior developer** who drafts code. You are the **senior** who reviews, tests, and approves.

### Common beginner mistakes
- Assuming AI knows what files are on your PC (tell it your columns and paths)
- Skipping straight to "train model" without cleaning data
- Trusting AI about data you do not have (it may invent columns like `coach` or `formation`)

---

## Lesson 20: Features We Want vs Features We Have

### What it is
Not every cool idea can be built with every dataset. The model can only learn from **columns that exist** in your data.

### Our current file: `results.csv` has ONLY:
`date`, `home_team`, `away_team`, `home_score`, `away_score`, `tournament`, `city`, `country`, `neutral`

### What you asked for (NOT in this file):
| Feature | In results.csv? |
|---------|-----------------|
| Coach | ❌ No |
| Formation (4-3-3) | ❌ No |
| Playstyle (attacking/defensive) | ❌ No |
| Man of the match | ❌ No |
| Substitutions | ❌ No |
| Goal scorer foot (left/right) | ❌ No |
| Goal distance (yards) | ❌ No |
| League player stats | ❌ No |

### Why it matters
Feeding a model means giving it columns of numbers/text. If the column does not exist, you must **find another dataset** or **collect** the data.

### Simple analogy
You want to bake a cake with chocolate, but your bag only has flour and eggs. You must **go shopping** for chocolate before you can use it.

### Real-world path to your vision
1. **Now:** Learn pipeline with `results.csv` (matches from 2021+, all tournaments)
2. **Next datasets to find:** `goalscorers.csv` (same Kaggle), then external sources (StatsBomb, FBref, API-Football) for advanced stats
3. **Later:** Merge multiple datasets on match date + teams

### Common beginner mistakes
- Thinking "more features in my head" = "more features in the CSV"
- Using only World Cup (~1,036 matches) when thousands of international matches exist
- Training before cleaning and defining target

---

---

## Lesson 21: Feature Engineering

### What it is
**Feature engineering** means creating or selecting input columns (features) that help the model make good predictions.

### Why it exists
Raw data is rarely ready for a model. You transform dates into year/month, flags into 0/1, and pick only relevant columns.

### Where it is used
Step 5 of the pipeline — after cleaning, before train/test split.

### Simple analogy
Before baking, you don't throw whole eggs in the cake mix — you crack them, separate yolk, measure. Feature engineering prepares ingredients for the model.

### Common beginner mistakes
- Using the target or final scores as features (data leakage)
- Keeping too many text columns without encoding
- Not saving a separate modeling-ready file

---

## Lesson 22: Data Leakage

### What it is
**Data leakage** = the model sees information during training that it would NOT have in real life before making a prediction.

### Why it exists (as a problem)
The model looks accurate in testing but fails in production because it was "cheating."

### Example in our project
Using `home_score` and `away_score` as features → the model already knows who won. Useless for real prediction.

### Simple analogy
A student takes a test with the answer key on the same page. High score, but they didn't learn anything.

### Common beginner mistakes
- Including post-match stats as pre-match features
- Computing team averages using future matches (temporal leakage)

---

## Lesson 23: Encoding (Preview)

### What it is
ML models need **numbers**. **Encoding** converts text like `"Brazil"` into numbers the model can use.

### Why it exists
You cannot multiply `"England"` by 0.5. Encoding turns categories into numeric form.

### Where we use it
Next notebook — before training with scikit-learn.

### Simple analogy
Every country gets a student ID number. The model uses IDs, not names.

---

---

## Lesson 24: Train/Test Split

### What it is
Splitting data into **training set** (learn) and **test set** (evaluate).

### Why it exists
Testing on training data hides overfitting — the model memorized instead of learned.

### Simple analogy
Practice with 80% of flashcards, quiz yourself on the other 20% you never studied.

### Common beginner mistakes
- Testing on the same rows used for training
- Shuffling time-series without thinking (we use random split for now)

---

## Lesson 25: Model

### What it is
A **model** is the learned "brain" that maps features → prediction.

We use **Random Forest** — many decision trees voting together.

### Why it exists
Humans cannot write rules for thousands of team/tournament combinations.

### Simple analogy
100 coaches each vote Win/Draw/Loss — majority wins.

---

## Lesson 26: Training vs Inference

| Term | Meaning |
|------|---------|
| **Training** | `.fit()` — model learns from past matches |
| **Inference** | `.predict()` — model guesses a new match |

### Simple analogy
Training = studying for exams. Inference = taking the real exam.

---

## Lesson 27: Accuracy, Precision, Recall

| Metric | Meaning |
|--------|---------|
| **Accuracy** | % of all predictions that were correct |
| **Precision** | When model says Win, how often correct? |
| **Recall** | Of all real Wins, how many did we find? |

Random baseline for 3 classes ≈ 33%. Our first model ~52% beats random — not perfect, normal for v1.

---

---

## Lesson 28: Merging Datasets

### What it is
**Merging** joins two tables on shared columns (keys), like `date` + `home_team`.

### Why it exists
Real projects combine multiple data sources into one modeling table.

### Simple analogy
Matching attendance sheets with test score sheets using student ID — same idea with match keys.

### Common beginner mistakes
- Wrong merge keys (duplicate rows)
- Using same-match goal counts as features (data leakage)

---

## Lesson 29: Rolling / Historical Features

### What it is
**Rolling features** = statistics from a team's **previous N matches** (e.g. avg goals last 5 games).

### Why it exists
Recent form predicts future results better than team name alone.

### `.shift(1)` rule
Always shift before rolling so the **current match** is not included — prevents leakage.

### Simple analogy
Your last 5 exam scores predict the next exam — not including today's score while still in the exam room.

---

*More lessons will be added as we progress through each milestone.*
