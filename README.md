# Landing Page A/B Experiment

A statistical analysis of an A/B experiment on 40,000 users, to decide **which landing page version to adopt** and how traffic source and user type relate to conversion.

**Tech stack:** Python · pandas · SciPy · statsmodels · seaborn · Matplotlib · Jupyter Notebook

---

## Overview

A company tested two versions of its landing page (**A** and **B**). Users were exposed to one of the two versions, and the experiment recorded whether each user converted and how much they spent.

The business question is simple: **which version should become the main page?** This project answers it with hypothesis tests on the two metrics that matter, conversion rate and spend, and then checks whether traffic source and user type change the picture.

## Objectives

1. Validate the quality and structure of the experiment data.
2. Compare the **average spend** of converted users between page A and page B.
3. Compare the **conversion rate** between page A and page B.
4. Assess whether **traffic source** and **user type** are associated with conversion.
5. Support the conclusions with clear visualizations and turn them into business recommendations.

## Data

| Item | Detail |
|---|---|
| File | `landing_experiment.csv` |
| Size | 40,000 users (one row per user), 9 columns, no missing values |
| Period | January 1 to January 28, 2026 (28 days) |
| Assignment | 19,982 users on page A and 20,018 on page B |

| Column | Description |
|---|---|
| `user_id` | Unique user identifier |
| `date` | Date the user was exposed to the page |
| `landing` | Page version shown (A or B) |
| `region`, `dispositivo` | Geographic region and device type |
| `traffic_source` | Channel through which the user arrived (Organic, Ads, Email, Referral) |
| `user_type` | New or returning user (`Nuevo` / `Recurrente`) |
| `converted` | Whether the user made a conversion |
| `gasto` | Amount spent (0 if the user did not convert) |

## Methodology

The notebook is organized in seven steps:

1. **Load and validate the data:** structure, data types, unique users, date range and expected categories.
2. **Compare average spend** between pages, among converted users.
3. **Compare conversion rate** between pages.
4. **Traffic source and conversion:** association test.
5. **User type and conversion:** association test.
6. **Visualize** the categorical results in absolute volume and in proportion.
7. **Executive insight** with business recommendations.

Every test states its null and alternative hypotheses and is evaluated at a 0.05 significance level.

| Question | Test | Why |
|---|---|---|
| Does average spend differ between pages? | Independent two-sample t-test, with Levene's test to check equal variances | Compares the means of two independent groups |
| Does conversion rate differ between pages? | Two-proportion z-test | Compares two rates measured on independent groups |
| Is traffic source or user type associated with conversion? | Chi-square test of independence | Tests the association between two categorical variables |

## Key findings

| Metric | Page A | Page B | Result |
|---|---|---|---|
| Conversion rate | 12.57% | 15.96% | +3.39 percentage points · z = -9.68 · p < 0.0001 |
| Average spend (converted users) | 61.09 | 68.75 | +12.5% · t = -9.48 · p < 0.0001 |

- **Page B outperforms page A on both key metrics.** It converts more users and each converted user spends more.
- **Traffic source has a real but marginal effect on conversion** (χ² = 8.66, p = 0.0341). Email (14.99%) and Ads (14.74%) convert slightly better than Referral (13.88%) and Organic (13.79%), a spread of only 1.2 percentage points. Organic still brings the most converted users (2,480) because it has the highest traffic volume.
- **User type does not influence conversion** (χ² = 0.51, p = 0.4736). New users convert at 14.36% and returning users at 14.09%.

## Business recommendations

- **Migrate to page B as the main version of the site.** It is the factor with the strongest and most actionable impact in the analysis, improving both the number of conversions and the value of each one.
- **Prioritize Email and Ads as acquisition channels,** while sustaining Organic for its dominant volume of traffic and conversions.
- **Do not differentiate campaigns by user type** (new vs. returning), since there is no evidence that it affects conversion. Personalization resources can go to variables with proven impact, such as the page version.
- **Deepen the traffic source analysis** with a larger sample or a longer period, since the association is significant but small.

## Repository contents

| File | Description |
|---|---|
| `landing_experiment_ab_test_EN.ipynb` | Full analysis notebook, with code, documentation and saved outputs (tables and charts) |
| `README.md` | Project description |

## Viewing and reproducing the analysis

The notebook is saved with its outputs, so tables and charts can be read directly on GitHub without running any code.

In the notebook, the data is read from `/datasets/landing_experiment.csv`. To re-run the analysis, place the file in a folder of your choice and update that path in the data loading cell. Required libraries: `pandas`, `scipy`, `statsmodels`, `seaborn` and `matplotlib`.

## Author

**Natalia Sepúlveda** — Data Analyst | Business Intelligence

[LinkedIn](https://www.linkedin.com/in/natalia-sepulveda-escobar) · [GitHub](https://github.com/nataliasepulveda-28)
