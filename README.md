# Superstore Sales & Pricing Analysis

An exploratory and statistical analysis of a fictional US superstore's retail transactions, focused on identifying key drivers of sales and profit, and quantifying how discounting strategy affects profit across product categories.

## Overview

Retailers use discounts to drive volume, but every dollar discounted is a dollar not earned unless offset by higher sales volume. This project examines:

1. **What drives sales and profit** — by product category, sub-category, customer segment, and region.
2. **Whether discounting hurts profit** — via simple linear regression of Profit on Discount.
3. **Whether the discount penalty differs by product category** — via an ANCOVA model with a Discount × Category interaction.

## Dataset

- **Source:** [Superstore Sales dataset](https://www.kaggle.com/) (Kaggle) — a commonly used teaching dataset modeled on a fictional US-based superstore chain.
- **Size:** 9,994 order-line rows × 21 columns (raw), 20 columns after cleaning.
- **Granularity:** each row is a single product line item within a customer order (not a full order).
- **Key fields used:** `Sales`, `Profit`, `Discount`, `Quantity`, `Category`, `Sub-Category`, `Segment`, `Region`.

> The raw CSV (`Superstore.csv`) is not included in this repo — download it from Kaggle and place it in the project root to reproduce the analysis.

## Data Cleaning

- Dropped `Row ID` (arbitrary index, no analytical value).
- Converted `Order Date` and `Ship Date` from strings to proper datetime objects.
- Verified there are no missing values in any of the 20 remaining columns.

## Analysis

### 1. Descriptive / exploratory

- Total sales by Category and Sub-Category.
- Total sales and profit by Customer Segment (Consumer, Corporate, Home Office).
- Total sales and profit by Region (Central, East, South, West).
- Scatter plot of Profit vs. Discount to visually inspect the relationship.

### 2. Simple linear regression

```
Profit = β₀ + β₁(Discount) + ε
```

Tests whether discount rate alone predicts profit.

### 3. ANCOVA (Discount × Category)

```
Profit = μ + αᵢ(Category) + β(Discount) + (αβ)ᵢ(Discount × Category) + ε
```

Tests whether the discount-profit relationship differs across Furniture, Office Supplies, and Technology.

## Key Findings

| Model | R² | Key result |
|---|---|---|
| Profit ~ Discount | 0.048 | Each unit increase in discount → profit drops by ~249.05 (p < .001) |
| Profit ~ Discount × Category | 0.085 | Discount effect on profit varies significantly by category (p < .001) |

**Discount penalty per category (change in profit per unit of discount):**

| Category | Slope |
|---|---|
| Furniture (reference) | −362.53 |
| Office Supplies | −150.01 |
| Technology | −814.33 |

**Takeaway:** Technology is by far the most discount-sensitive category, while Office Supplies absorbs discounting with the least profit damage. A single storewide discount policy likely isn't optimal — category-specific discount ceilings would better protect margin, especially on Technology products.

## Tech Stack

- **Python** — pandas, seaborn, matplotlib, statsmodels

## Project Structure

```
.
├── Superstore.csv              # raw dataset (not included — download from Kaggle)
├── analysis.ipynb              # notebook: cleaning, EDA, regression, ANCOVA
├── Superstore_Analysis_Report.docx   # written report (Introduction, Data, Methods, References)
└── README.md
```

## Running the Analysis

```bash
pip install pandas matplotlib seaborn statsmodels
jupyter notebook analysis.ipynb
```

## Limitations

- This is observational transactional data, not a designed experiment — discount levels were not randomly assigned, so results describe association, not causation.
- Residuals in both models are heavy-tailed and non-normal (per Jarque-Bera test), so p-values should be interpreted with some caution; a robust or bootstrapped standard error approach would be a natural next step.

## References

- Kaggle — Superstore Sales dataset
- [statsmodels documentation](https://www.statsmodels.org/)
- [seaborn documentation](https://seaborn.pydata.org/)
- [pandas documentation](https://pandas.pydata.org/)
- Kutner, M. H., Nachtsheim, C. J., Neter, J., & Li, W. *Applied Linear Statistical Models* (5th ed.). McGraw-Hill/Irwin.
