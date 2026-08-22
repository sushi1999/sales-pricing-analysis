# Superstore Sales & Pricing Analysis

Retailers use discounts to boost sales volume, but do those discounts actually make money, or do they just destroy profit margins?
This project looks at a fictional US Superstore's sales data to find out how discounts impact profit, and why a one-size-fits-all discount policy doesn't work.

## Overview

1. **What drives sales and profit** — by product category, sub-category, customer segment, and region.
2. **Whether discounting hurts profit** — via simple linear regression of Profit on Discount.
3. **Whether the discount penalty differs by product category** — via an ANCOVA model with a Discount × Category interaction.

## Dataset

- **Source:** [Superstore Sales dataset](https://www.kaggle.com/) (Kaggle) — a commonly used teaching dataset modeled on a fictional US-based superstore chain.
- **Size:** 9,994 order-line rows × 21 columns (raw), 20 columns after cleaning.
- **Granularity:** each row is a single product line item within a customer order (not a full order).
- **Key fields used:** `Sales`, `Profit`, `Discount`, `Quantity`, `Category`, `Sub-Category`, `Segment`, `Region`.

## Conclusion

Not all products handle discounts the same way. Using an ANCOVA model (Discount × Category), I found that Technology products get hit the hardest by discounts.
Because Technology products lose profit far faster than any other category under discounts, we should strictly cap Tech discounts to protect our bottom line.


## Limitations

- This is observational transactional data, not a designed experiment — discount levels were not randomly assigned, so results describe association, not causation.

## References

- Kaggle — Superstore Sales dataset
- [statsmodels documentation](https://www.statsmodels.org/)
- [seaborn documentation](https://seaborn.pydata.org/)
- [pandas documentation](https://pandas.pydata.org/)
- Kutner, M. H., Nachtsheim, C. J., Neter, J., & Li, W. *Applied Linear Statistical Models* (5th ed.). McGraw-Hill/Irwin.
