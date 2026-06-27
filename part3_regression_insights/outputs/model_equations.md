# Model Equations

## Dummy Variable Approach

Before running regression, categorical variables were converted into numeric dummy (indicator) variables. Each dummy variable takes the value **1** when a record belongs to a given category, and **0** otherwise.

To avoid the **dummy variable trap** (perfect multicollinearity), one category from each variable was dropped and treated as the **reference (baseline) category**. All coefficients on dummy variables represent the difference relative to that reference.

### Reference Categories

| Variable | Reference Category | Reason |
|---|---|---|
| `region` | **East** | East is the largest region and provides a stable baseline |
| `store_type` | **Residential** | Residential is the most common store type in the dataset |

### Dummy Variables Created

| Dummy Variable | Interpretation |
|---|---|
| `region_North` | 1 if store is in North region; 0 otherwise |
| `region_South` | 1 if store is in South region; 0 otherwise |
| `region_West` | 1 if store is in West region; 0 otherwise |
| `store_Airport` | 1 if store is an Airport store; 0 otherwise |
| `store_High Street` | 1 if store is a High Street store; 0 otherwise |
| `store_Mall` | 1 if store is a Mall store; 0 otherwise |

The East region and Residential store type are implicit baselines — their effect is captured in the model's intercept.

---

## Simple Regression Equations

### Model 1 – Footfall

**Equation:**

```
Monthly Sales = 446,410.58 + 35.68 × Footfall
```

| Term | Value | p-value | Meaning |
|---|---|---|---|
| Intercept | 446,410.58 | < 0.001 | Estimated baseline monthly sales when footfall is zero |
| Footfall coefficient | +35.68 | < 0.001 | Each additional visitor is associated with $35.68 more in monthly sales |
| R-squared | 0.7363 | — | 73.6% of monthly sales variation is explained by footfall alone |

**Business meaning:** Footfall is by far the strongest individual predictor of sales. Bringing more customers through the door — through location, accessibility, or promotional events — is the most powerful lever for increasing revenue.

---

### Model 2 – Marketing Spend

**Equation:**

```
Monthly Sales = 560,777.35 + 2.13 × Marketing Spend
```

| Term | Value | p-value | Meaning |
|---|---|---|---|
| Intercept | 560,777.35 | < 0.001 | Estimated baseline monthly sales when marketing spend is zero |
| Marketing Spend coefficient | +2.13 | < 0.001 | Each additional $1 in marketing spend is associated with $2.13 more in monthly sales |
| R-squared | 0.1672 | — | Marketing spend alone explains only 16.7% of sales variation |

**Business meaning:** Marketing spend is positively associated with sales, but its standalone explanatory power is weak. The $2.13 return per dollar of marketing is likely confounded by the fact that larger, higher-footfall stores also tend to spend more on marketing.

---

### Model 3 – Customer Rating

**Equation:**

```
Monthly Sales = 701,366.86 − 5,284.87 × Customer Rating
```

| Term | Value | p-value | Meaning |
|---|---|---|---|
| Intercept | 701,366.86 | < 0.001 | Estimated baseline |
| Customer Rating coefficient | −5,284.87 | 0.638 | Not statistically significant |
| R-squared | 0.0007 | — | Explains essentially none of the variation in monthly sales |

**Business meaning:** Customer rating does not predict monthly sales in a simple model. This does not mean ratings are unimportant — they may matter for customer retention, profitability, and long-term brand value — but a single month's sales figure is not meaningfully related to rating alone.

---

## Multiple Regression Equation

**Final Model Equation:**

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

### Coefficient Interpretation

| Variable | Coefficient | p-value | Significant? | Business Meaning |
|---|---|---|---|---|
| Intercept | 49,912.80 | 0.300 | No | Baseline sales for an East Residential store with all numeric variables at zero (theoretical; interpret with caution) |
| footfall | +34.00 | < 0.001 | ✅ Yes | Controlling for other factors, each additional visitor is associated with ~$34 more in monthly sales |
| marketing_spend | +1.20 | < 0.001 | ✅ Yes | Each additional $1 in marketing spend is associated with ~$1.20 more in monthly sales, after controlling for footfall and other factors |
| inventory_availability_pct | +3,001.99 | < 0.001 | ✅ Yes | Each 1 percentage point improvement in inventory availability is associated with ~$3,002 more in monthly sales |
| customer_rating | +13,627.39 | 0.005 | ✅ Yes | Each 1-star improvement in customer rating is associated with ~$13,627 more in monthly sales, after controlling for other variables |
| avg_discount_pct | −45,708.55 | 0.211 | ❌ No | Discounting does not significantly predict monthly sales after other factors are controlled for |
| region_North | +6,184.51 | 0.380 | ❌ No | North region stores do not differ significantly from East region stores in this model |
| region_South | +18,685.41 | 0.009 | ✅ Yes | South region stores earn approximately $18,685 more per month than comparable East region stores |
| region_West | +18,110.86 | 0.004 | ✅ Yes | West region stores earn approximately $18,111 more per month than comparable East region stores |
| store_Airport | +41,880.25 | < 0.001 | ✅ Yes | Airport stores earn approximately $41,880 more per month than comparable Residential stores |
| store_High Street | +18,092.55 | 0.003 | ✅ Yes | High Street stores earn approximately $18,093 more per month than comparable Residential stores |
| store_Mall | +29,086.17 | < 0.001 | ✅ Yes | Mall stores earn approximately $29,086 more per month than comparable Residential stores |

### Model Fit

| Metric | Value |
|---|---|
| R-squared | 0.8321 |
| Adjusted R-squared | 0.8255 |
| Number of observations | 320 |

---

## Final Model Selected

**Selected model: Multiple Regression (Model 4)**

### Reason for Selection

1. **Highest explanatory power:** R-squared of 0.8321 versus 0.7363 for the best simple model.
2. **Captures multiple real-world drivers:** footfall, marketing, inventory, customer experience, and store characteristics are all included.
3. **Identifies relative importance:** by controlling for all factors simultaneously, the model isolates each variable's contribution.
4. **Practical decision support:** leadership can use individual coefficients to evaluate the potential impact of specific actions (e.g., improving inventory availability, increasing marketing spend, or prioritising certain store types).

The model should be used for **identifying associations and guiding investigation**, not for making deterministic predictions or claiming causal relationships.
