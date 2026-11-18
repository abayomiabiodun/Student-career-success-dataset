# Student Career Success Analysis — What Drives Placement & Salary?

An end-to-end exploratory data analysis and predictive modeling project investigating what academic, technical, and soft-skill factors most strongly influence student job placement and starting salary — and turning those findings into a practical, transparent **Placement Readiness Score** tool.

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen.svg)

---

##  Problem Statement

> What combination of academic, technical, and soft-skill factors most strongly predicts (a) whether a student gets placed in a job, and (b) how much they get paid — and can we build a practical, data-driven "Placement Readiness" scoring tool that students and career counselors can use to identify gaps and take action before graduation?

##  Dataset

- **File:** `student_career_success_dataset.csv`
- **Size:** 50,000 student records × 29 features
- **Fields include:** demographics, academic performance (CGPA, attendance, study hours), technical activity (programming skill, projects, certifications, hackathons, internships), soft skills (communication, teamwork, problem-solving), online presence (GitHub/LinkedIn), interview score, employability score, and outcomes (placement status, company tier, career field, starting salary).

##  Key Findings

| Question | Finding |
|---|---|
| Does GPA determine placement? | Only a modest effect — Placed students average CGPA 3.15 vs 2.96 for Not Placed; academic performance matters but isn't decisive. |
| What matters most? | **Resume quality, internships, and programming skill** dominate feature importance in the predictive model. |
| Do soft skills matter? | Yes — communication, teamwork, and problem-solving show a real, independent lift in placement rate. |
| What's the biggest bottleneck? | **Interview performance** — it's the tightest gate between candidates and top-tier company offers. |
| What drives salary (once placed)? | **Company tier**, more than individual skill scores — access to Tier-1 recruiting pipelines matters enormously. |
| Is the built-in Employability Score reliable? | Moderately — correlation of 0.47 with placement, validating it as a useful but incomplete signal. |

##  Data Cleaning

- Verified zero missing values and zero duplicate records
- Range/sanity checks on all numeric fields (percentages ≤ 100, CGPA ≤ 4.0, scores within bounds)
- Logical consistency checks (e.g., "Not Placed" students correctly show $0 starting salary)
- Standardized categorical text fields
- Engineered features: ordinal encodings (Academic Performance, English Proficiency, University Year, Company Tier), binary flags (GitHub/LinkedIn/Leadership), composite Soft Skill Index and Tech Activity Index

##  Exploratory Data Analysis

20+ visualizations covering:
- Placement rate by gender, major, university year, and placement mode
- Academic factor distributions (CGPA, attendance, study hours) split by outcome
- Technical activity comparisons (projects, certifications, hackathons, internships)
- Soft skill and English proficiency breakdowns
- Interview score as a placement/company-tier bottleneck
- Salary drivers by company tier and career field
- Full correlation ranking and heatmap across all numeric features
- Audit of the dataset's built-in Employability Score

##  Predictive Modeling

Two classifiers trained on **pre-outcome, non-leaking features only** (no company tier, interview score, or salary used as inputs):

| Model | ROC-AUC | Notes |
|---|---|---|
| Logistic Regression | 0.800 | Best overall discrimination |
| Random Forest (300 trees) | 0.796 | Best recall on at-risk ("Not Placed") students — 70% |

##  The Solution: Placement Readiness Score

A transparent, explainable 0–100 composite score built from the empirically strongest, student-actionable drivers (CGPA, programming skill, projects, certifications, internships, resume score, communication, teamwork, problem-solving, attendance, GitHub/LinkedIn presence), weighted by their measured importance.

- **ROC-AUC: 0.799** — nearly matching the black-box Random Forest, while remaining fully interpretable
- Identifies **9.2% of the student population** as early-stage "at-risk" (low readiness, Freshman/Sophomore year) — flaggable while there's still time to intervene
- Requires no new data collection — computable instantly from data institutions already track

##  Recommendations

**For Students:** prioritize landing at least one internship, build a visible GitHub portfolio, treat interview prep as its own subject, and don't neglect soft skills.

**For Universities:** use the Readiness Score to flag at-risk students early, invest in internship pipelines, run mandatory interview-readiness workshops, and track soft skills explicitly in curriculum.

**For Recruiters/Policy:** audit which majors/students get access to Tier-1 campus recruiting drives, since company tier — not marginal skill differences — is the dominant salary driver.

##  Tech Stack

- Python 3.10+
- pandas, numpy — data wrangling
- matplotlib, seaborn — visualization
- scikit-learn — modeling (Logistic Regression, Random Forest)
- Jupyter Notebook

##  Getting Started

### Installation
\`\`\`bash
git clone https://github.com/<your-username>/student-career-success-analysis.git
cd student-career-success-analysis
pip install -r requirements.txt
\`\`\`

### requirements.txt
\`\`\`
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
\`\`\`

### Usage
\`\`\`bash
jupyter notebook student_career_success_analysis.ipynb
\`\`\`
Run all cells top to bottom — the notebook is self-contained and fully reproducible.

##  Project Structure
\`\`\`
.
├── student_career_success_analysis.ipynb   # Full analysis notebook
├── student_career_success_dataset.csv       # Dataset (50,000 rows × 29 columns)
├── requirements.txt                          # Python dependencies
└── README.md                                 # This file
\`\`\`

##  Limitations

- Dataset is observational — correlations shown do **not** prove causation
- Readiness Score should be used as an advising/triage signal, not a high-stakes gatekeeping tool (precision on "Not Placed" predictions is ~44–64%, meaning false positives occur)
- Model performance and feature weights are dataset-specific and should be re-validated before deployment on a different student population

##  Author

Abayomi Abiodun | https://www.linkedin.com/in/abayomi-abiodun/ 

##  Project Request 

Built as an end-to-end data analysis & visualization portfolio project. Contributions, issues, and pull requests are welcome!
