# Does Party Identity Displace Income as a Driver of Redistribution Preferences?
### Evidence from the ANES (1970–2024)

**Nathaniel Njaa | QSS 20 | Dartmouth College | Spring 2026**

---

## Overview

Rising income inequality in the US has not produced the surge in redistributive policy demand that the Meltzer-Richard model predicts. This project tests one explanation: party identity has increasingly displaced income as the primary driver of redistribution preferences. Using the ANES Cumulative Time Series (1970–2024, N=46,708), I examine whether the partisan gap in redistribution attitudes has grown over time while the income gradient has flattened, and whether this tracks rising inequality as measured by the Gini coefficient.

**Research question:** Has party identification increasingly displaced income as the primary predictor of redistribution preferences among American voters from 1970 to 2024?

---

## Data

**ANES Cumulative Time Series File, 1948–2024** — download free at https://electionstudies.org. The raw CSV (~156 MB) is not stored here due to file size (GitHub max of 100MB); set the path in `code/01_clean.ipynb`. Key variables: `VCF0830` (redistribution support, 7-pt), `VCF0114` (income quintile), `VCF0301` (party ID, 7-pt), `VCF0004` (year).

---

## Repository Structure

```
code/
  01_clean.ipynb      — load ANES, clean variables, save analysis-ready CSV
  02_analyze.ipynb    — descriptive stats, decade correlations, OLS regressions
  03_visualize.ipynb  — generate figures saved to output/
output/
  viz1_gini_overlay.png     — partisan gap over time with Gini overlay
  viz2_small_multiples.png  — redistribution by income x party, by decade
```

---

## Preliminary Findings

The income-redistribution correlation is nearly flat (r = -0.076). Contrary to Meltzer-Richard, richer and poorer Americans hold surprisingly similar views on redistribution, when you would expect income to be the dominant predictor. Instead, among low-income voters, the Democrat-Republican gap grew from ~0.9 points in the 1970s to ~2.45 by 2020. Low-income Democrats and low-income Republicans have pulled dramatically apart even as both groups experienced the same rise in inequality, consistent with Kelly & Enns (2010).

---

## Requirements

`pip install pandas numpy matplotlib scipy statsmodels`
