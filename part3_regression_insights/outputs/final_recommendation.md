# Final Business Recommendation

## Executive Summary

This analysis applied simple and multiple linear regression to 320 store-month observations across a retail chain. The final multiple regression model explains **83.2% of the variation in monthly sales** (R-squared = 0.832, Adjusted R-squared = 0.826). Based on the regression evidence, five key business insights and four actionable recommendations are presented below.

---

## 1. Which Factors Appear Most Strongly Associated with Monthly Sales?

| Rank | Variable | Coefficient | Statistical Significance | Business Impact |
|---|---|---|---|---|
| 1 | **Footfall** | +$34 per visitor | *** (p < 0.001) | The single largest numerical driver of sales |
| 2 | **Store Type (Airport)** | +$41,880 vs Residential | *** (p < 0.001) | Airport stores significantly outperform |
| 3 | **Store Type (Mall)** | +$29,086 vs Residential | *** (p < 0.001) | Mall stores are the second-highest format |
| 4 | **Inventory Availability** | +$3,002 per 1% improvement | *** (p < 0.001) | Stock availability has a meaningful and consistent effect |
| 5 | **Customer Rating** | +$13,627 per 1-star increase | ** (p = 0.005) | Rating becomes significant after controlling for other factors |
| 6 | **Marketing Spend** | +$1.20 per $1 spent | *** (p < 0.001) | Statistically significant, but return must be evaluated against cost |
| 7 | **Region (South & West)** | +$18,000–$19,000 vs East | ** (p < 0.01) | South and West regions outperform East and North |

---

## 2. Which Variables Should Leadership Focus On?

### Prioritise These:

**Footfall is the primary driver.** Leadership should investigate what drives footfall into stores — location accessibility, nearby anchors (transport hubs, offices, residential density), in-store events, and digital/physical marketing that converts awareness into store visits. Footfall alone explains 73.6% of monthly sales variation.

**Inventory availability matters consistently.** Each 1 percentage point improvement in stock availability is associated with approximately $3,002 more in monthly sales. This is a relatively controllable operational variable. Reducing stockouts and ensuring popular product lines are reliably available should be an operational priority.

**Store type and format are strong structural predictors.** Airport and Mall stores generate $29,000–$42,000 more per month than Residential stores of equivalent characteristics. In capital allocation decisions, investing in Airport and Mall locations is supported by this evidence.

**Customer rating is associated with higher sales** (after controlling for other factors). A 1-star improvement in average customer rating is associated with ~$13,600 more in monthly sales. Investments in service quality, staff training, and in-store experience may support both ratings and sales.

**South and West regions outperform East** by approximately $18,000 per month. Leadership should investigate whether these regions have structural advantages (demographics, competition, economic conditions) that can be replicated or leveraged.

---

## 3. Which Variables Should Not Be Over-Interpreted?

**Marketing Spend alone is a weak predictor (R-squared = 0.167 in simple regression).** While statistically significant, the return of $1.20 in sales per $1 of marketing spend does not imply that increasing marketing budgets universally drives growth. Marketing spend is likely correlated with store size and footfall levels. Leadership should not assume that additional spend will automatically generate proportional sales lifts without analysing marketing effectiveness by channel and store.

**Average Discount Percentage is not statistically significant** in the multiple regression model (p = 0.211). The evidence does not support the view that higher discounting meaningfully increases monthly sales, once other factors are controlled for. Discount strategies should be evaluated on other grounds (margin management, competitive positioning) rather than expected sales volume uplift.

**Region North does not differ significantly from Region East** (p = 0.38). North-East comparisons should not be used as a basis for resource reallocation decisions based on this model.

**Customer Rating in a simple model is not significant** (p = 0.638). Leadership should be cautious about interpreting customer satisfaction scores as a direct short-term revenue driver without controlling for the size and type of the store.

---

## 4. What Business Action Would You Recommend?

Based on regression evidence, leadership should prioritise the following actions:

### Action 1: Investigate footfall drivers at underperforming stores

The five stores with the largest negative residuals (including STR-1017, STR-1023, STR-1012) are generating significantly less sales than the model expects for stores with their footfall levels and characteristics. Leadership should audit whether footfall is being effectively converted into purchases (conversion rate, product availability, in-store layout) at these locations.

### Action 2: Prioritise inventory availability improvements

At an estimated $3,002 per percentage point per month per store, even modest improvements in inventory availability across the store network could represent significant revenue gains. Stores with inventory availability below 85% should be identified and targeted for supply chain improvement.

### Action 3: Evaluate capital allocation toward Airport and Mall formats

If new store openings or format conversions are planned, the evidence supports prioritising Airport and Mall formats, which structurally outperform Residential stores by $29,000–$42,000 per month on average, controlling for footfall and other variables.

### Action 4: Learn from stores with the largest positive residuals

Stores such as STR-1028 (Mall, East), STR-1073 (Residential, East), and STR-1019 (Residential, East) are significantly outperforming model expectations. Leadership should investigate the specific practices, management approaches, and local market conditions at these stores and consider whether learnings can be transferred to other locations.

---

## 5. What Risks and Limitations Should Leadership Keep in Mind?

### A. The model explains association, not causation

Regression demonstrates that variables are **correlated** with monthly sales. It does not prove that changing a variable will directly cause a change in sales. For example:

- Stores with high footfall may have higher sales *because they are better located*, not because footfall causes sales in isolation.
- Higher marketing spend may correlate with higher sales because larger, better-performing stores receive larger marketing budgets — not because the spend itself drove the result.

Before investing based on a regression coefficient, leadership should consider whether the relationship reflects a genuine causal mechanism or a confounding association.

### B. Omitted variables remain a concern

The model explains 83.2% of sales variation, but 16.8% remains unexplained. Important factors not captured in this dataset include:

- **Competitor strength and pricing** (only distance is measured, not quality or range)
- **Seasonality and external economic conditions** (the month variable was not used as a predictor)
- **Staff quality and management effectiveness** (only staff count is available)
- **Marketing channel mix** (TV, digital, in-store promotions are aggregated)
- **Local demographics** (population density, age profile, income levels)

### C. The model is built on cross-sectional data from a limited time window

With 80 stores observed across 4 months, the panel is relatively small. Relationships identified may not generalise perfectly to all future periods or new store locations.

### D. Residuals reveal that the model is not equally accurate for all stores

Some stores — particularly in the West region — show large negative residuals, meaning the model over-predicts their sales. Any decisions about these stores based on model predictions should account for this uncertainty.

---

## Conclusion

The regression analysis provides clear, evidence-based signals: **footfall, inventory availability, store type, and customer rating are the variables most strongly associated with monthly sales**. Leadership should investigate what drives footfall, ensure stock availability is high, prioritise Airport and Mall store formats in capital allocation, and learn from the outperforming stores. Marketing spend and discounting strategies should not be assumed to drive sales without further rigorous testing of their causal effectiveness. All findings should be treated as starting points for investigation, not deterministic rules.
