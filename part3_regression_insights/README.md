# Part 3: Regression-Based Business Insights & Model Interpretation

## Business Problem Summary

A retail chain's leadership team wants to understand what factors drive monthly sales performance across stores. They are evaluating potential actions including increasing marketing spend, improving inventory availability, changing discounting strategy, reallocating staff, and prioritising certain store types or regions.

This analysis uses **regression modelling** to identify which factors are most strongly associated with monthly sales, compare different models, and provide data-supported business recommendations.

---

## Dataset Description

**File:** `data/business_regression_data.xlsx`  
**Records:** 320 observations (80 stores × 4 months)

| Column | Type | Description |
|---|---|---|
| store_id | Categorical | Unique store identifier |
| month | Date | Month of observation |
| region | Categorical | Store region: East, North, South, West |
| store_type | Categorical | Store format: Residential, High Street, Airport, Mall |
| marketing_spend | Numerical | Monthly marketing expenditure ($) |
| footfall | Numerical | Monthly visitor count |
| avg_discount_pct | Numerical | Average discount percentage applied |
| staff_count | Numerical | Number of staff in the store |
| inventory_availability_pct | Numerical | % of products available in stock |
| competitor_distance_km | Numerical | Distance to nearest competitor (km) — 6 missing values |
| holiday_flag | Binary | 1 if month included a public holiday |
| customer_rating | Numerical | Average customer satisfaction score — 8 missing values |
| monthly_sales | **Dependent variable** | Monthly sales revenue ($) |
| monthly_profit | Numerical | Monthly profit (not used as predictor) |

**Data Cleaning:** Missing values in `customer_rating` and `competitor_distance_km` were imputed with the column median.

---

## Dependent and Independent Variables

- **Dependent variable:** `monthly_sales`
- **Numerical independent variables used:** `footfall`, `marketing_spend`, `inventory_availability_pct`, `customer_rating`, `avg_discount_pct`
- **Categorical variables converted to dummies:** `region`, `store_type`
- **Variables not used in regression:** `store_id` (identifier), `month` (not encoded), `monthly_profit` (outcome variable, would cause data leakage), `holiday_flag` (not significant in initial testing), `staff_count`, `competitor_distance_km` (excluded from final model to reduce complexity)

---

## Regression Approach

1. **Simple Linear Regression (3 models):** Each model used monthly_sales as the dependent variable and one independent variable at a time (footfall, marketing_spend, customer_rating).
2. **Multiple Linear Regression (1 model):** Combined 5 numerical predictors plus dummy variables for region and store_type.
3. All models estimated using Ordinary Least Squares (OLS).
4. Model fit measured using R-squared and Adjusted R-squared.
5. Statistical significance assessed via t-statistics and p-values.

---

## Dummy Variable Approach

Categorical variables were encoded as binary dummy variables:

| Variable | Reference Category | Dummies Created |
|---|---|---|
| `region` | **East** | region_North, region_South, region_West |
| `store_type` | **Residential** | store_Airport, store_High Street, store_Mall |

The reference category is omitted from the model to avoid multicollinearity (dummy variable trap). All dummy variable coefficients represent the sales difference relative to the reference group.

---

## Model Comparison Summary

| Model | R-squared | Key Finding |
|---|---|---|
| Simple – Footfall | 0.7363 | Strongest single predictor; each visitor ≈ $35.68 more in sales |
| Simple – Marketing Spend | 0.1672 | Significant but weak alone; explains only 16.7% of variation |
| Simple – Customer Rating | 0.0007 | Not significant alone (p = 0.638) |
| **Multiple Regression** | **0.8321** | Best model; 11 predictors explain 83.2% of sales variation |

---

## Final Model Selected

**Multiple Regression Model** (R-squared = 0.8321, Adjusted R-squared = 0.8255)

**Equation:**
```
Monthly Sales = 49,912.80
             + 34.00  × Footfall
             +  1.20  × Marketing Spend
             + 3,001.99 × Inventory Availability (%)
             + 13,627.39 × Customer Rating
             − 45,708.55 × Avg Discount (%)
             + 6,184.51 × region_North
             + 18,685.41 × region_South
             + 18,110.86 × region_West
             + 41,880.25 × store_Airport
             + 18,092.55 × store_High Street
             + 29,086.17 × store_Mall
```

**Significant variables:** footfall, marketing_spend, inventory_availability_pct, customer_rating, region_South, region_West, store_Airport, store_High Street, store_Mall

**Non-significant:** avg_discount_pct, region_North

---

## Business Recommendation

1. **Focus on footfall** – it is the primary driver of monthly sales. Investigate what drives visitors to stores and how to improve conversion.
2. **Improve inventory availability** – each 1% improvement is worth ~$3,002 per month in sales.
3. **Prioritise Airport and Mall formats** when making new store investment decisions.
4. **Investigate underperforming stores** (especially in the West region), which show large negative residuals.
5. **Do not rely on discount percentage** to drive sales — it is not statistically significant in the full model.

---

## Assumptions and Limitations

- **Linearity:** The model assumes a linear relationship between each predictor and monthly sales.
- **No causation:** Regression identifies associations, not causal relationships. Coefficients should not be interpreted as "if we increase X, sales will change by Y."
- **Omitted variables:** Seasonality, competitor quality, demographics, and marketing channel effectiveness are not captured.
- **Missing values:** Imputed by median; results may differ with more sophisticated imputation.
- **Extrapolation risk:** Predictions outside the range of observed data are unreliable.

---

## Screenshots Included

| File | Description |
|---|---|
| `screenshots/simple_regression_output.png` | Scatter plot and regression table for footfall simple regression |
| `screenshots/multiple_regression_output.png` | Coefficient plot and full table for multiple regression model |
| `screenshots/residuals_preview.png` | Actual vs predicted, residual histogram, and top residuals table |
| `screenshots/model_comparison_preview.png` | R-squared bar chart and comparison table across all 4 models |

---

