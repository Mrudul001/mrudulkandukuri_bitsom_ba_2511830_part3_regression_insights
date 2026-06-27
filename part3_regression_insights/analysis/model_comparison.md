# Model Comparison

## Overview

Four regression models were built and compared to understand what drives monthly sales across stores. The table below summarises key metrics.

---

## Comparison Table

| Model | Variables Used | R-squared | Significant Variables | Business Usefulness | Limitations |
|---|---|---|---|---|---|
| **Model 1 – Simple (Footfall)** | monthly_sales ~ footfall | **0.7363** | footfall (p < 0.001) | High. Footfall alone explains 73.6% of sales variation – the strongest single predictor found. | Ignores marketing, inventory, store type, and all other factors. Cannot guide actionable decisions beyond "get more footfall." |
| **Model 2 – Simple (Marketing Spend)** | monthly_sales ~ marketing_spend | 0.1672 | marketing_spend (p < 0.001) | Moderate. Marketing is statistically significant, but explains only 16.7% of sales variation on its own. | Prone to confounding. Stores that spend more on marketing may also be larger, better located, or have higher footfall for unrelated reasons. |
| **Model 3 – Simple (Customer Rating)** | monthly_sales ~ customer_rating | 0.0007 | None (p = 0.638) | Low. Customer rating has essentially no linear relationship with monthly sales when examined alone. | Does not account for store size or type. A high-rated small store will still have lower sales than a lower-rated large store. |
| **Model 4 – Multiple Regression** | monthly_sales ~ footfall + marketing_spend + inventory_availability_pct + customer_rating + avg_discount_pct + region dummies + store_type dummies | **0.8321** (Adj. R² = 0.826) | footfall, marketing_spend, inventory_availability_pct, customer_rating, region_South, region_West, store_Airport, store_High Street, store_Mall (all p < 0.05) | High. This is the best-performing model, explaining 83.2% of monthly sales variation and capturing both numerical and categorical drivers. | Does not capture time/seasonality, competitor strength, staff quality, or marketing channel mix. Association does not imply causation. |

---

## Model-by-Model Analysis

### Model 1 – Simple Regression: Footfall

- **Equation:** Monthly Sales = 446,410.58 + 35.68 × Footfall
- **R-squared:** 0.7363
- **Key finding:** Each additional visitor to a store is associated with approximately **$35.68** more in monthly sales. This is statistically robust (p < 0.001).
- **Business use:** Good for quick benchmarking and footfall-based sales forecasting. However, this model cannot explain what drives footfall itself.

---

### Model 2 – Simple Regression: Marketing Spend

- **Equation:** Monthly Sales = 560,777.35 + 2.13 × Marketing Spend
- **R-squared:** 0.1672
- **Key finding:** Each additional $1 of marketing spend is associated with approximately **$2.13** more in monthly sales (p < 0.001). While statistically significant, the R-squared is very low.
- **Business use:** Suggests some positive association, but marketing spend alone is a poor predictor. The return appears low but is likely confounded by store size.

---

### Model 3 – Simple Regression: Customer Rating

- **Equation:** Monthly Sales = 701,366.86 − 5,284.87 × Customer Rating
- **R-squared:** 0.0007
- **Key finding:** Customer rating is **not significantly associated** with monthly sales in a simple regression (p = 0.638). The R-squared is essentially zero.
- **Business use:** Should not be used as a standalone sales predictor. Customer rating may matter for long-term loyalty or profitability, but does not directly correlate with monthly revenue.

---

### Model 4 – Multiple Regression (Recommended Model)

- **R-squared:** 0.8321 | **Adjusted R-squared:** 0.8255
- **Key finding:** The combined model explains **83.2%** of monthly sales variation. Most predictors are statistically significant after controlling for others.
- **Significant variables:**
  - `footfall` (p < 0.001) – strongest driver
  - `marketing_spend` (p < 0.001)
  - `inventory_availability_pct` (p < 0.001) – each percentage point improvement is worth ~$3,002 in sales
  - `customer_rating` (p = 0.005) – becomes significant in the multiple model
  - `region_South` and `region_West` (p < 0.01) – both outperform the East reference region
  - `store_Airport`, `store_High Street`, `store_Mall` (all p < 0.01) – all outperform Residential stores
- **Weak/non-significant variables:**
  - `avg_discount_pct` (p = 0.21) – discounting does not significantly predict sales after other factors are controlled for
  - `region_North` (p = 0.38) – not significantly different from East

---

## Which Model to Use?

**Model 4 (Multiple Regression) is the recommended model** for business decision-making because:

1. It has the highest explanatory power (R² = 0.832).
2. It separates the individual contribution of each factor while controlling for others.
3. It allows leadership to compare the relative importance of footfall, marketing, inventory, and store/region characteristics.
4. It produces more reliable residuals for identifying outperforming and underperforming stores.

Model 1 (footfall only) is useful as a quick diagnostic tool for estimating sales from visitor counts alone.
