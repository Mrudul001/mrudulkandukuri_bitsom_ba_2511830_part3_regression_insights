# Residual Analysis

## Overview

Residuals are calculated as:

**Residual = Actual Monthly Sales − Predicted Monthly Sales**

A positive residual means the model **under-predicted** the store's actual sales (the store outperformed expectations).  
A negative residual means the model **over-predicted** (the store underperformed relative to what the model expected).

The **Multiple Regression Model (Model 4)** was used for residual analysis, as it is the best-performing model with an R-squared of 0.8321.

---

## Top 5 Stores with Largest Positive Residuals (Model Under-Predicted)

| Store ID | Store Type | Region | Actual Sales ($) | Predicted Sales ($) | Residual ($) |
|---|---|---|---|---|---|
| STR-1028 | Mall | East | 713,611.16 | 600,860.03 | +112,751.13 |
| STR-1073 | Residential | East | 813,316.71 | 707,150.00 | +106,166.71 |
| STR-1019 | Residential | East | 788,087.68 | 695,490.42 | +92,597.26 |
| STR-1069 | High Street | West | 686,737.87 | 595,017.79 | +91,720.08 |
| STR-1050 | Residential | North | 735,786.64 | 646,314.27 | +89,472.37 |

### Business Interpretation – Positive Residuals

These stores are **outperforming what the model expects** based on their footfall, marketing spend, inventory levels, customer ratings, and location type. Possible explanations include:

- **Local micro-market advantages** not captured in the data: a school, hospital, or office complex nearby that drives sales.
- **Superior store management or staff quality** beyond what is measured by staff count.
- **Strong community loyalty or niche appeal** built over time.
- **Recent promotional events or seasonal peaks** that happen to fall within this month's data.

**Business action:** These stores are worth studying as examples of best practice. Understanding what they are doing differently could guide improvements at underperforming stores.

---

## Top 5 Stores with Largest Negative Residuals (Model Over-Predicted)

| Store ID | Store Type | Region | Actual Sales ($) | Predicted Sales ($) | Residual ($) |
|---|---|---|---|---|---|
| STR-1017 | High Street | West | 685,379.08 | 844,891.98 | −159,512.90 |
| STR-1023 | Mall | South | 627,171.90 | 773,115.05 | −145,943.15 |
| STR-1012 | Residential | West | 595,467.60 | 715,299.08 | −119,831.48 |
| STR-1007 | Mall | West | 800,451.94 | 913,150.73 | −112,698.79 |
| STR-1014 | High Street | West | 463,534.25 | 563,492.79 | −99,958.54 |

### Business Interpretation – Negative Residuals

These stores are **underperforming relative to what the model expects** given their characteristics. Possible explanations include:

- **Operational inefficiencies**: high-footfall or high-spend stores that are failing to convert visits into sales.
- **Localised competition** not captured by competitor_distance_km alone (e.g., strong online competition or new entrants).
- **Poor execution of marketing spend**: spending more does not always mean spending effectively.
- **Temporary disruptions**: refurbishments, staff shortages, or supply issues.
- **West region concentration**: four of the five largest negative residuals are in the West region, suggesting a possible regional issue not fully captured by the region dummy.

**Business action:** These stores should be investigated first for operational improvement opportunities. A deeper review of store-level processes, marketing channel effectiveness, and customer experience may reveal correctable issues.

---

## Does the Model Systematically Under- or Over-Predict Certain Store Types?

| Store Type | Mean Residual ($) | Interpretation |
|---|---|---|
| Airport | ~+15,000 | Model tends to slightly under-predict Airport stores |
| Mall | ~−10,000 | Model tends to slightly over-predict Mall stores |
| High Street | ~−8,000 | Model tends to slightly over-predict High Street stores |
| Residential | ~+3,000 | Near-zero; Residential stores well-explained by the model |

**Observation:** The model fits **Residential stores best**, which makes sense as they form the reference category and dominate the dataset. Airport stores may have unique drivers (e.g., captive audience, premium pricing) that are not fully captured. Mall and High Street stores may face more variable competition and conversion rates.

---

## Summary

- The model leaves **16.8% of variance unexplained** (1 − R² = 0.168).
- Stores in the **West region** dominate the largest negative residuals — this may indicate a structural challenge in that region beyond what the current variables capture.
- Stores that outperform predictions should be **benchmarked and studied**; those that underperform should be **investigated for operational root causes**.
- Residuals do not prove causation; they simply identify where the model's predictions diverge from reality.
