# Computer Hardware Performance — Regression Model

A multiple linear regression project for IEE 380 (Probability and Statistics for Engineering Problem Solving) at ASU. I used Minitab to build a model that predicts a computer system's relative performance based on its hardware specs.

## The Dataset

I used the [Computer Hardware dataset](https://www.kaggle.com/datasets) from Kaggle — 209 systems from 30 vendors (IBM, Honeywell, Microdata, etc.). I pulled a random sample of 100 systems and used 6 hardware specs as predictors:

- **MYCT** – Machine cycle time (ns)
- **MMIN** – Minimum main memory (KB)
- **MMAX** – Maximum main memory (KB)
- **CACH** – Cache memory size (KB)
- **CHMIN** – Minimum channels
- **CHMAX** – Maximum channels

The goal: predict **PRP** (Published Relative Performance).

## What I Did

1. **Exploratory analysis** – summary stats, histograms, and a correlation matrix to see which specs actually moved the needle on performance.
2. **Initial model** – ran a regression with all 6 predictors. Two of them (MYCT and CHMAX) weren't statistically significant, so I dropped them.
3. **Final model** – narrowed it down to 4 predictors: MMIN, MMAX, CACH, and CHMIN.
4. **Checked assumptions** – linearity, independence (Durbin-Watson), homoscedasticity, and normality of residuals.

## Results

The final model:

```
PRP = -8.58 + 0.0127(MMIN) + 0.002868(MMAX) + 0.854(CACH) + 3.234(CHMIN)
```

- **R² = 90.59%** — the model explains about 91% of the variation in performance
- **Adjusted R² = 90.19%** — close to R², so the model isn't overfit
- All 4 predictors statistically significant (p < 0.001)
- No multicollinearity issues (all VIF scores under 5)

Out of everything, **cache size had the biggest impact** on performance — makes sense, since cache sits closest to the CPU and speeds up data access the most.

## Files

- `Individual_Project_IEE380.pdf` — full write-up with all the analysis, plots, and appendix
- `images/` — Minitab screenshots (histograms, regression output, diagnostic plots)

## Tools Used

Minitab Statistical Software
