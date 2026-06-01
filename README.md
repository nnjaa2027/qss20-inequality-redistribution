# Does Party Identity Displace Income as a Driver of Redistribution Preferences?
### Evidence from the ANES (1970–2024)

**Nathaniel Njaa | QSS 20 | Dartmouth College | Spring 2026**

---

## Overview

Rising income inequality in the US has not produced the surge in redistributive demand that the Meltzer-Richard model predicts. This project tests two linked explanations: (1) income has become a weaker predictor of redistribution attitudes over time, and (2) redistribution attitudes have become more tightly bound to party identity rather than driving vote choice independently. Using the ANES Cumulative Time Series (1970–2024, N=46,708), I track how the partisan gap in redistribution preferences has grown while the income gradient has flattened, and test whether redistribution attitudes predict presidential vote choice differently across decades.

---

## Data

**Primary: ANES Cumulative Time Series File, 1948–2024**
Download free at [electionstudies.org](https://electionstudies.org). The raw CSV (~156 MB) is not stored in this repo due to file size. After downloading, update the `DATA_PATH` variable at the top of `code/01_clean.ipynb` to point to the file on your machine.

**Secondary: Census Bureau Historical Income Table H-4 (Gini coefficients)**
Stored at `data/gini_census.csv`. Source: [Census Bureau Historical Income Tables](https://www.census.gov/data/tables/time-series/demo/income-poverty/historical-income-households.html).

---

## Repository Structure

```
code/
  01_clean.ipynb
  02_analyze.ipynb
  03_visualize.ipynb
data/
  gini_census.csv
output/
  anes_clean.csv
  decade_coefs.csv
  viz1_gini_overlay.png
  viz2_aggregate_redist.png
  viz3_small_multiples.png
  viz4_coef_plot.png
```

---

## Scripts

### [01_clean.ipynb](code/01_clean.ipynb)
**Takes in:** Raw ANES CSV (path set by `DATA_PATH` variable)  
**Does:** Loads 10 key variables, coerces to numeric, recodes redistribution support (flipped so 7 = strongly pro), collapses party ID into Democrat/Independent/Republican, creates binary vote choice variable, filters to 1970+ and drops missing on core vars  
**Outputs:** `output/anes_clean.csv` (N=46,708, 12 columns)

### [02_analyze.ipynb](code/02_analyze.ipynb)
**Takes in:** `output/anes_clean.csv`  
**Does:** Sample characterization table; income-redistribution correlations by decade; partisan gap over time; weighted OLS predicting redistribution support (3 models); logistic regression predicting Republican vote choice (4 models); decade-by-decade logit coefficients  
**Outputs:** `output/decade_coefs.csv`

### [03_visualize.ipynb](code/03_visualize.ipynb)
**Takes in:** `output/anes_clean.csv`, `output/decade_coefs.csv`, `data/gini_census.csv`  
**Does:** Generates all four paper figures  
**Outputs:**
- `output/viz1_gini_overlay.png` — partisan gap among low-income voters over time with Gini overlay
- `output/viz2_aggregate_redist.png` — aggregate redistribution support over time with Gini overlay
- `output/viz3_small_multiples.png` — redistribution by income quintile × party across three decades
- `output/viz4_coef_plot.png` — logit coefficient on redistribution support predicting vote choice, by decade

---

## How to Run

Run notebooks in order:

```bash
jupyter nbconvert --to notebook --execute --inplace code/01_clean.ipynb
jupyter nbconvert --to notebook --execute --inplace code/02_analyze.ipynb
jupyter nbconvert --to notebook --execute --inplace code/03_visualize.ipynb
```

---

## Requirements

```
pip install pandas numpy matplotlib statsmodels
```
