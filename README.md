# Gender-Based Violence in Nepal (2019–2026): Exploratory Data Analysis

An exploratory data analysis (EDA) project investigating patterns and trends in reported Gender-Based Violence (GBV) cases across Nepal, using monthly, station-level administrative data from 2019 to early 2026.

This is the first project in a broader series of Nepal-focused data analysis work.

---

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Research Questions](#research-questions)
- [Tech Stack](#tech-stack)
- [Repository Structure](#repository-structure)
- [Setup & Installation](#setup--installation)
- [Usage](#usage)
- [Key Findings](#key-findings)
- [Project Status](#project-status)
- [Data Caveats & Limitations](#data-caveats--limitations)
- [Future Work](#future-work)
- [Author](#author)

---

## Overview

Gender-Based Violence remains a significant social issue in Nepal, and administrative reporting data offers a valuable, if imperfect, window into its scale, patterns, and trends over time. This project explores a multi-year dataset of reported GBV cases to surface meaningful patterns across time, geography, crime category, victim demographics, and case resolution status.

The analysis is Python-first (pandas, numpy, matplotlib, seaborn), structured as a single well-documented Jupyter notebook that progresses section by section through a set of guiding questions, with findings written up in plain language alongside each chart.

## Dataset

**Source file:** `data/raw/GenderBasedVoilence2019-2026_Nepal.csv`

| Property | Detail |
|---|---|
| Rows | 42,337 |
| Time span | January 2019 – March 2026 (monthly granularity; 2026 is a partial year) |
| Geographic coverage | 7 provinces, 76 districts, 178 police stations |
| Crime categories | Domestic Violence, Cybercrime, Rape, Attempt to Rape, Physical Abuse, Sexual Harassment, Child Sexual Abuse, Human Trafficking, Child Marriage |
| Victim demographics | Woman, Girl-Child, Boy-Child |
| Case status | Under Investigation, Decided, Filed |
| Missing values | None |
| Duplicate rows | None (though see [Data Caveats](#data-caveats--limitations) re: row granularity) |

**Row granularity:** each row represents an *aggregated monthly count* — i.e., the number of cases reported in a given month, at a given police station, for a given crime category, victim demographic, and status — **not** one row per individual case.

## Research Questions

The project explores questions across five themes:

**Trends over time**
- How have total reported cases changed year over year?
- Are there seasonal/monthly reporting patterns?
- Did COVID-19 (2020) visibly disrupt reporting?
- Is Cybercrime's share of total cases growing?

**Geographic patterns**
- Which provinces/districts report the highest case volumes?
- Are certain crime categories concentrated in specific provinces?
- Which police stations are high/low volume outliers?

**Crime category breakdown**
- What's the relative share of each crime category, and how does that mix differ by province?
- How do Rape and Attempt to Rape trends compare?
- Is there a relationship between Child Marriage and Child Sexual Abuse?

**Victim demographics**
- How does victim demographic vary across crime categories?
- Are Boy-Child cases concentrated in particular categories?
- Has the demographic split shifted over time?

**Case status / justice pipeline**
- What fraction of cases are Decided vs. Under Investigation vs. Filed, and does this vary by category or region?
- Has resolution rate changed over time?

## Tech Stack

- **Language:** Python 3.11
- **Core libraries:** pandas, numpy
- **Visualization:** matplotlib, seaborn
- **Environment:** Python `venv`
- **Notebook interface:** Jupyter Notebook
- **Version control:** Git / GitHub

## Repository Structure

```
gbv-nepal-eda/
├── data/
│   ├── raw/                  # original, untouched dataset
│   └── processed/            # cleaned/derived data (if produced)
├── notebooks/
│   └── 01_gbv_nepal_eda.ipynb
├── outputs/
│   └── figures/               # exported chart images
├── README.md
├── requirements.txt
└── .gitignore
```

## Setup & Installation

```bash
# Clone the repository
git clone <your-repo-url>
cd gbv-nepal-eda

# Create and activate a virtual environment
python3 -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## Usage

```bash
# From the repo root, with venv activated
jupyter notebook
```

Open `notebooks/01_gbv_nepal_eda.ipynb` and run cells sequentially from the top. The notebook is organized into numbered sections, each with markdown context explaining what's being explored and why, followed by code and a written takeaway.

## Key Findings

*(Findings so far — updated as remaining sections are completed)*

**Trends over time**
- Total reported cases dropped sharply in 2020 (~17,000, down from ~23,300 in 2019), before climbing to a series high of ~27,800 by 2025.
- The 2020 decline was not limited to lockdown months (which began ~March 2020) — case counts were already lower in Jan–Mar 2020 and stayed depressed through 2020–2021, suggesting a broader, longer disruption rather than a short lockdown-only effect.
- Reporting is consistently lowest in winter (Jan/Feb/Dec) and highest in summer (Jul/Aug) across all years.
- Cybercrime's share of total cases nearly doubled, from ~9–12% (2021–2023) to ~19–19.5% (2024–2025), driven by a genuine rise in case counts.

**Geographic patterns**
- Bagmati (~52,000 cases) and Madhesh (~39,500) report far more cases than other provinces; Karnali and Gandaki are lowest (~8,500–9,500) — likely reflecting population size as much as incidence rate.
- Kathmandu district is a major outlier (~11,500 cases), well above the next-highest district (Bara, ~6,500). The lowest-case districts are almost all mountainous/rural.
- Cybercrime is Bagmati's most disproportionate category: it makes up 31.9% of Bagmati's own case mix (vs. 1.9–8.4% elsewhere), and Bagmati alone accounts for 81.1% of all Cybercrime cases reported nationally.
- Case volume per police station is right-skewed — most stations report 300–1,000 total cases, with a small number of high-volume outliers reporting 3,500+.

**Crime category breakdown**
- Domestic Violence accounts for the large majority of all cases (~111,000+), more than 5x the next largest category (Cybercrime, ~20,500).
- Madhesh holds the largest national share of Domestic Violence, Physical Abuse, and Human Trafficking cases; Koshi holds the largest share of Rape and Attempt to Rape cases.
- Rape and Attempt to Rape are diverging over time: Rape cases have grown gradually since 2019, while Attempt to Rape cases have declined since peaking in 2020 — the ratio between them nearly halved (~0.33 in 2020 to ~0.18 in 2025).
- Child Marriage and Child Sexual Abuse show a weak-to-moderate positive correlation across districts (r = 0.384), but very different trends over time: Child Sexual Abuse has grown nationally while Child Marriage has stayed flat.

*(Victim demographics and case status sections pending — see Project Status)*

## Project Status

| Section | Status |
|---|---|
| 0. Setup & Data Loading | ✅ Complete |
| 1. Data Overview & Quality Check | ✅ Complete |
| 2. Trends Over Time | ✅ Complete |
| 3. Geographic Patterns | ✅ Complete |
| 4. Crime Category Breakdown | ✅ Complete |
| 5. Victim Demographics | 🔲 Not started |
| 6. Case Status / Justice Pipeline | 🔲 Not started |
| 7. Outliers & Anomalies | 🔲 Not started |
| 8. Summary & Key Findings | 🔲 Not started |

## Data Caveats & Limitations

- **Row granularity:** rows are monthly aggregated counts, not individual case records. Some (Date, Station, Category, Demographic, Status) combinations repeat with different case counts, suggesting the data may be compiled from multiple sub-reports — treated as a known quirk rather than an error.
- **Zero-case rows** (~34% of rows) are kept throughout, since they appear to represent genuine "nothing reported this month" entries and don't affect sums.
- **2026 is a partial year** (Jan–Mar only) and is excluded from year-over-year comparisons.
- **No population data is included.** Raw case counts by province/district reflect volume, not necessarily per-capita incidence rate — higher counts may partly or fully reflect larger populations rather than higher rates of violence.
- **Correlation ≠ causation.** Where relationships are noted (e.g., seasonal patterns, category co-occurrence), the dataset can describe patterns but cannot explain underlying causes.
- **A small number of category-year combinations are fully absent** rather than zero (e.g., no Cybercrime rows exist for 2020), likely reflecting a tracking/reporting gap rather than a true absence of that crime type.

## Future Work

- Complete Sections 5–8 (demographics, case status, outliers, summary)
- Bring in external population data to compute per-capita case rates by province/district
- Investigate the Child Marriage/Child Sexual Abuse outlier district identified in Section 4
- Explore additional Nepal-related datasets as part of the broader project series

## Author

Rohan Piya — Dickinson College