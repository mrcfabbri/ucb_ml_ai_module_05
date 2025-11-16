# M05 — Coupon Acceptance Analysis

This folder contains the notebook `prompt.ipynb` and the dataset used to explore which factors influence whether a driver accepts a delivered coupon.

## Summary of Findings

### Overall Acceptance Patterns
- **Overall acceptance rate:** 56.84% of all coupons delivered were accepted
- **Dataset:** 12,684 observations after removing columns with >5% missing data (primarily the `car` column with 99.15% null values)

### Bar Coupons — Key Quantitative Results
- **Overall bar coupon acceptance:** 41.00% (significantly below the overall average)
- **Visit frequency drives acceptance:**
  - Infrequent visitors (≤3 times/month): 37.06% acceptance
  - Frequent visitors (>3 times/month): 76.88% acceptance
  - **Effect size:** 2.07x increase for frequent bar-goers
  
- **Age and frequency interaction:**
  - Drivers visiting bars >1/month AND age >25: 69.52% acceptance
  - Non-frequent visitors or age ≤25: 66.67% acceptance
  
- **Social context matters:**
  - Drivers visiting bars >1/month + no kids as passengers + non-farming/fishing/forestry occupation: **71.32% acceptance**
  - All others: 29.60% acceptance
  - **Effect size:** 2.41x difference
  
- **Complex behavioral segments:**
  - Group 1 (bars >1/month, no kids, not widowed): 71.32%
  - Group 2 (bars >1/month, age <30): 72.17%
  - Group 3 (cheap restaurants >4/month, income <$50K): 45.35%

**Key insight:** Social, frequent bar patrons (younger adults and mid-age, not widowed, typically without kids) are 2-3x more likely to accept bar coupons than infrequent visitors.

### Coffee House Coupons — Key Quantitative Results
- **Overall coffee house acceptance:** 49.92% (slightly below average)
- **Visit frequency is highly predictive:**
  - Never visit: 18.88% acceptance
  - Less than 1/month: 48.19% acceptance
  - 1-3 times/month: 64.78% acceptance
  - 4-8 times/month: 68.59% acceptance
  - Greater than 8/month: 65.79% acceptance
  - **Progressive increase:** Acceptance increases monotonically with visit frequency up to 4-8/month
  
- **Frequency comparison:**
  - Infrequent visitors (≤3 times/month): 44.94% acceptance
  - Frequent visitors (>3 times/month): 67.50% acceptance
  - **Effect size:** 1.50x increase for frequent coffee-house visitors

**Key insight:** Coffee house acceptance shows a clear dose-response relationship with visit frequency, with the biggest jump occurring between "never" (18.88%) and occasional visitors (48-65%).

### Contextual and Demographic Patterns
- **Passenger type influence:** Drivers without kids as passengers show significantly higher acceptance rates for both bar and coffee house coupons
- **Occupation effects:** Non-farming/fishing/forestry occupations correlate with higher bar coupon acceptance
- **Marital status:** Widowed individuals show lower acceptance rates (excluded from high-performing segments)
- **Age patterns:** Younger drivers (<30) visiting bars frequently show 72.17% acceptance
- **Income and restaurant habits:** Lower-income frequent cheap-restaurant visitors show moderate acceptance (45.35%), suggesting different behavioral patterns than bar/coffee house segments

### Hypotheses and Qualitative Insights

**Bar Coupon Hypothesis:**
Frequent bar-goers are the primary target for bar coupons, with acceptance rates more than doubling (76.88% vs 37.06%) compared to infrequent visitors. Social context is critical: drivers visiting bars regularly (>1/month) who are over 25, not widowed, and traveling without kids show the highest acceptance (71.32%). This suggests bar coupons work best for socially active adults in leisure contexts rather than family settings.

**Coffee House Hypothesis:**
Coffee house coupons appeal broadly to regular visitors, with acceptance increasing progressively from never-visitors (18.88%) to frequent patrons (68.59%). Unlike bars, the pattern is more gradual, suggesting coffee house habits are more flexible and habitual rather than strongly social. The moderate-to-high acceptance across multiple visit frequency tiers indicates coffee coupons can successfully target both occasional and frequent customers.
7
**Strategic Implications:**
1. **Segmentation matters:** Visit frequency is the strongest predictor for both coupon types
2. **Social context filtering:** Bar coupons should avoid delivery when kids are passengers
3. **Broader appeal for coffee:** Coffee house coupons show higher baseline acceptance and work across wider demographic segments
4. **Behavioral targeting:** Focus on existing customers (habit reinforcement) rather than customer acquisition for immediate ROI

### ### Data Quality Notes

**Notes on `Single` vs `Unmarried partner`**
- **Meaning:** In the survey dataset `Single` denotes respondents without a partner, while `Unmarried partner` indicates respondents who are in a romantic/household partnership but not legally married. These are distinct groups and may behave differently (e.g., dining decisions can be influenced by a present partner).
- **Statistical check recommended:** Compare acceptance rates between these two groups (e.g., contingency table + Chi-square test) rather than assuming equivalence.

**Missing Data Handling:**
- Removed `car` column (99.15% missing values)
- Retained columns with <5% missing values (Bar: 0.84%, CoffeeHouse: 1.71%, CarryAway: 1.19%, RestaurantLessThan20: 1.02%, Restaurant20To50: 1.49%)
- Final dataset: 12,684 observations across 25 variables

### Where to Find Files
- **Notebook:** `prompt.ipynb`
- **Data:** `data/coupons.csv`

### Reproducibility / How to Run
1. Change directory to this folder:

```bash
cd ucb_ml_ai_module_05
```

2. Start the Jupyter environment (project uses UV manager):

```bash
uv run jupyter lab
```

3. To execute the notebook non-interactively and save outputs:

```bash
uv run python -m nbconvert --to notebook --execute prompt.ipynb --output executed_prompt.ipynb
```

### Suggested Next Steps
- **Statistical validation:** Run targeted Chi-square tests and logistic regression to quantify effect sizes and p-values for key factors (visit frequency, passenger type, age groups)
- **Predictive modeling:** Build a logistic regression or random forest classifier to predict acceptance and analyze feature importance
- **Marital status analysis:** Create contingency tables comparing `Single` vs `Unmarried partner` vs `Married partner` acceptance rates with confidence intervals
- **Contextual variable exploration:** Analyze time of day, weather, expiration period, and destination effects on acceptance
- **Coupon type comparison:** Extend analysis to Restaurant(<$20), Restaurant($20-50), and Carry Away coupons to identify cross-category patterns
- **Interaction effects:** Test two-way interactions between visit frequency and demographic variables (age × frequency, income × frequency)

---
**Generated from `prompt.ipynb`** — See the notebook for visualizations, complete code, and detailed cell outputs.
