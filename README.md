# Healthcare Analytics for Doctor Visits

AICTE DIY Project — a data analytics case study on what drives doctor visits, built by **Chitranjan Vishwakarma** (BCA, Sri Ram Kishun P.G College, Gokul, Karsada, Varanasi).

## Project Overview

This project analyzes a healthcare survey dataset of **5,190 patients** to figure out what actually drives the number of doctor visits a person makes. The goal is to turn raw survey data into insights that a hospital, clinic, or health insurance company could use for staffing, premium design, or preventive-care planning.

The analysis follows the full data analytics workflow — clean the data, explore it visually, test whether observed differences are statistically significant, and then build predictive models to confirm what's really driving the outcome.

## Dataset

**File:** `Healthcare_Analytics_for_Doctor_Visits.csv`

Survey data recording doctor visits over a 2-week period, along with demographic and health information for each patient.

| Column | Description |
|---|---|
| `visits` | Number of doctor visits in the last 2 weeks |
| `gender` | male / female |
| `age` | Age, scaled (raw value × 100 = age in years) |
| `income` | Annual income, scaled (raw value × 10,000 = income in $) |
| `illness` | Number of illnesses in the last 2 weeks |
| `reduced` | Days of reduced activity due to illness/injury |
| `health` | General health questionnaire score (higher = worse) |
| `private` | Has private health insurance? |
| `freepoor` | Free government insurance due to low income? |
| `freerepat` | Free government insurance (veteran/senior/disability)? |
| `nchronic` | Chronic condition that does *not* limit activity |
| `lchronic` | Chronic condition that *does* limit activity |

## Files in This Project

| File | Description |
|---|---|
| `healthcare_analytics_doctor_visits.ipynb` | Main Jupyter notebook — full analysis, code, charts, and write-up |
| `Healthcare_Analytics_DIY_Project.pptx` | Filled AICTE submission slide deck (6 slides) |
| `Healthcare_Analytics_for_Doctor_Visits.csv` | Source dataset |
| `README.md` | This file |

## Methodology

1. **Data Cleaning** — rescaled `age` and `income` to real-world units, checked for missing values and duplicates, built an age-group bucket for grouped analysis.
2. **Exploratory Data Analysis** — distribution of visits, age, income, and health scores; visit patterns by gender, age group, insurance status, and chronic condition status; a correlation heatmap across numeric variables.
3. **Statistical Testing**
   - Independent t-test: are visit differences between genders statistically significant?
   - Chi-square test: is having a limiting chronic condition related to having private insurance?

## Key Findings

- **~80% of people had zero doctor visits** in the 2-week window — visits are rare and heavily right-skewed.
- **Illness severity metrics** (`illness`, `reduced` days, `health` score) are by far the strongest predictors of doctor visits — confirmed independently by both the Poisson regression and the Random Forest model.
- **Older patients visit more** — the 61–72 age group visits almost 3× as often as the 19–30 group.
- **Limiting chronic conditions nearly triple** average visits compared to no chronic condition.
- **Private insurance holders visit slightly more often**, consistent with insurance removing a cost barrier to care.
- **Gender has a small but statistically significant effect**, with women visiting marginally more than men.

## Tech Stack

- **Python** (pandas, NumPy) — data loading, cleaning, manipulation
- **Matplotlib & Seaborn** — visualizations
- **SciPy** — statistical hypothesis testing (t-test, chi-square)
- **Scikit-learn** — Random Forest regression, train/test split, evaluation metrics
- **VS Code** — end-to-end analysis environment

## How to Run

1. Install the dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scipy scikit-learn jupyter
   ```
2. Make sure `Healthcare_Analytics_for_Doctor_Visits.csv` is in the same folder as the notebook.
3. Launch and run all cells:
   ```bash
   jupyter notebook healthcare_analytics_doctor_visits.ipynb
   ```

## Recommendations

- Hospitals/clinics could use illness and health-score signals to **flag high-risk patients early** rather than waiting for a visit.
- Insurance companies could design **targeted plans for older patients and those with chronic conditions**, since these groups reliably drive up visit frequency.
- Public health campaigns could focus on the **~80% "zero visit" segment**, especially in lower-income brackets where free government insurance is available but may be underused.

---
*Dataset: Healthcare Analytics for Doctor Visits (Australian Health Survey data) — analyzed as part of the AICTE DIY Project.*
