# Superstore Sales & Pricing Analysis

Retailers use discounts to boost sales volume, but do those discounts actually make money, or do they just destroy profit margins?
This project looks at a fictional US Superstore's sales data to find out how discounts impact profit, and why a one-size-fits-all discount policy doesn't work.

## Overview

1. **Sales overviewt** — by product category, sub-category, customer segment, and region.
2. **Whether discounting hurts profit** — via simple linear regression of Profit on Discount.
3. **Whether the discount penalty differs by product category** — via an ANCOVA model with a Discount × Category interaction.

## Dataset

- **Source:** [Superstore Sales dataset](https://www.kaggle.com/) (Kaggle) — a commonly used teaching dataset modeled on a fictional US-based superstore chain.
- **Size:** 9,994 order-line rows × 21 columns (raw), 20 columns after cleaning.

## Conclusion

These findings suggest that discount strategies should differ by product category. Technology products appear to be much more sensitive to discounting, while Office Supplies are less affected. Therefore, managers should avoid offering large discounts on Technology products and instead consider category-specific pricing and promotional strategies.


## References

- Kaggle — Superstore Sales dataset
- [statsmodels documentation](https://www.statsmodels.org/)
- [seaborn documentation](https://seaborn.pydata.org/)
- [pandas documentation](https://pandas.pydata.org/)
- Kutner, M. H., Nachtsheim, C. J., Neter, J., & Li, W. *Applied Linear Statistical Models* (5th ed.). McGraw-Hill/Irwin.
