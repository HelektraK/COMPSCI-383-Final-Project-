# COMPSCI 383 Final Project  
**Evaluating Bias in Automated Hiring Decisions Using LLMs and Text Similarity**

## Project Overview

This project investigates whether automated hiring systems make decisions based solely on
demographic cues when candidate qualifications are held constant.

We study bias in two settings:
1. **Large Language Model (LLM)–based resume scoring**
2. **TF-IDF cosine similarity–based resume selection**

All resumes used in this study are *identical in qualifications* (skills, experience, education).
Only candidate **names** are varied to encode demographic signals such as gender and race.
Any differences in outcomes therefore reflect bias arising from name-based or structural cues,
rather than merit.

---

## Key Questions

- Do LLMs assign different hiring scores to candidates based only on names?
- Can “demographically blind” algorithms (e.g., TF-IDF similarity) still produce biased outcomes?
- How do selection rates differ across gender and race when qualifications are controlled?

---

## Methods

### Dataset
- **480 synthetic resumes**
- Identical content across all resumes
- Balanced demographics:
  - 50/50 Male/Female
  - 25% each Black, White, Asian, Hispanic
- Generated in-house to isolate demographic effects

### Method 1: LLM Batch Scoring
- Candidates scored 1–10 by an LLM acting as a hiring manager
- Only names provided to the model
- Deterministic settings (temperature = 0.0)
- Statistical evaluation using:
  - Two-sample t-tests (gender)
  - One-way ANOVA + pairwise tests (race)

### Method 2: TF-IDF Resume Selection
- Resumes converted to TF-IDF vectors
- Cosine similarity computed against a fixed job description
- Probabilistic selection based on similarity scores
- No demographic information provided to the algorithm

---

## Results (High Level)

- **LLM scoring** showed statistically significant differences in hiring scores by both gender
  and race, despite identical qualifications.
- **TF-IDF selection** produced unequal selection rates across demographic groups,
  demonstrating that bias can emerge even without explicit demographic features.
- These results highlight how both generative models and traditional NLP pipelines can
  reproduce or amplify bias.

Detailed results, figures, and statistical analyses are provided in the final paper.

---

## Project Paper

**Final Report (PDF):**  
[CS383 Final Project Paper](CS383%20Final%20Project.pdf)

> **Note:** GitHub may not render this PDF inline. Please download to view.

---

## Repository Contents

- `finalProject.ipynb` — Main analysis and experiments
- `milestone1.ipynb`, `milestone4:11.ipynb` — Intermediate project milestones
- `CS383 Final Project.pdf` — Final written report
- `.gitignore` — Excludes environment files and nonessential artifacts

Raw CSV data is not included where excluded by `.gitignore`.

---

## Course Context

- **Course:** COMPSCI 383 – Data Science for the Common Good  
- **Focus Areas:** AI fairness, bias evaluation, NLP, reproducibility

---

## Team Members

- **Helektra Katsoulakis** — Dataset construction, demographic balancing, LLM batch pipelines
- **Aadvik Mishra** — Prompt design, parsing logic, TF-IDF sampling pipeline
- **Akash Sahadevan** — Statistical testing (t-tests, ANOVA), bias analysis, interpretation

---

## Ethics Note

This project is designed to *expose and measure* bias in automated decision-making systems,
not to deploy such systems in practice. All resumes are synthetic, and no real candidate data
is used.
