# M05 — Coupon Acceptance Analysis

This folder contains the notebook `prompt.ipynb` and the dataset used to explore which factors influence whether a driver accepts a delivered coupon.

Summary of findings
- **Coupon type matters:** Certain coupons (e.g., Coffee House, low-cost restaurants) are accepted at higher rates than others. Coupon categories showed clear variance in acceptance.
- **Contextual factors are influential:** Time of day, passenger type (alone, partner, friend(s), kid(s)), and destination (No Urgent Place / Home / Work) all affect acceptance behavior.
- **Expiration & proximity:** Shorter expiration (`2h`) tends to increase immediate acceptance compared to `1d` in scenarios where the venue is nearby or on route to the destination.
- **Demographics show patterns:** Age groups and income brackets show differing acceptance tendencies; marital status also correlates with acceptance in ways worth testing further (for example, `Single` vs `Unmarried partner`).
- **Weather and travel plans:** Sunny vs. rainy/snowy and whether the driver has a destination that aligns with the venue direction also influence acceptance.

Notes on `Single` vs `Unmarried partner`
- **Meaning:** In the survey dataset `Single` denotes respondents without a partner, while `Unmarried partner` indicates respondents who are in a romantic/household partnership but not legally married. These are distinct groups and may behave differently (e.g., dining decisions can be influenced by a present partner).
- **Statistical check recommended:** Compare acceptance rates between these two groups (e.g., contingency table + Chi-square test) rather than assuming equivalence.

Where to find files
- Notebook: `prompt.ipynb`
- Data: `data/coupons.csv`

Reproducibility / how to run
1. Change directory to this folder:

```bash
cd "m05 Pratical Application I"
```

2. Start the Jupyter environment (project uses UV manager):

```bash
uv run jupyter lab
```

3. To execute the notebook non-interactively and save outputs:

```bash
uv run python -m nbconvert --to notebook --execute prompt.ipynb --output executed_prompt.ipynb
```

Suggested next steps
- Run targeted statistical tests for the strongest candidate factors (coupon type, passenger, time of day, expiration) to quantify effect sizes and significance.
- Build a simple classification model (logistic regression) to predict acceptance and analyze feature importance.
- Create a small section of the notebook to compare `Single` vs `Unmarried partner` acceptance rates and include confidence intervals / p-values.

If you want, I can: (a) run the statistical tests and add numeric results to this README, (b) commit these changes, or (c) add a brief visualization gallery with thumbnails and links to the figures in the notebook.

---
Generated from `prompt.ipynb` (EDA analysis) — see the notebook for plots, full code, and cell outputs.
