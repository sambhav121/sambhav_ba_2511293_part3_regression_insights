# Regression Analysis

## Test Selection

Monthly sales is a continuous outcome, so ordinary least squares regression was selected. The model estimates `monthly_sales` using marketing spend, footfall, discount, staffing, inventory availability, competitor distance, holiday flag, customer rating, region, and store type.

Rows with missing model inputs were excluded by listwise deletion. No imputation was used.

## Model Summary

| metric | value |
| --- | --- |
| Source rows | 320 |
| Rows used after listwise deletion | 306 |
| Rows excluded for missing model fields | 14 |
| Predictor count including dummies | 14 |
| R-squared | 0.8554 |
| Adjusted R-squared | 0.8485 |
| F-statistic | 122.9739 |
| F-test p-value | 0.0000 |
| Residual standard error | 40068.5946 |
| Dependent variable | monthly_sales |

## Coefficients

| term | coefficient | std_error | t_stat | p_value | significant_0_05 |
| --- | --- | --- | --- | --- | --- |
| footfall | 27.1107 | 2.3507 | 11.5332 | <0.001 | True |
| marketing_spend | 1.2258 | 0.1192 | 10.2870 | <0.001 | True |
| competitor_distance_km | -3,524.8379 | 546.4105 | -6.4509 | <0.001 | True |
| inventory_availability_pct | 2,785.9192 | 442.1322 | 6.3011 | <0.001 | True |
| store_type_Residential | -42,601.3483 | 8,796.5262 | -4.8430 | <0.001 | True |
| region_West | 28,392.3395 | 6,013.7032 | 4.7213 | <0.001 | True |
| region_South | 24,922.2941 | 6,822.8004 | 3.6528 | <0.001 | True |
| staff_count | 3,721.2197 | 1,188.4583 | 3.1311 | 0.0019 | True |
| customer_rating | 12,753.2669 | 4,460.4920 | 2.8592 | 0.0046 | True |
| store_type_High Street | -23,957.2860 | 8,668.9430 | -2.7636 | 0.0061 | True |
| holiday_flag | 14,036.1537 | 6,154.0658 | 2.2808 | 0.0233 | True |
| Intercept | 103,558.5271 | 45,964.0096 | 2.2530 | 0.0250 | True |
| region_North | 13,670.8901 | 6,774.0141 | 2.0181 | 0.0445 | True |
| store_type_Mall | -11,865.7312 | 8,983.4156 | -1.3208 | 0.1876 | False |
| avg_discount_pct | -30,937.3040 | 34,706.9558 | -0.8914 | 0.3735 | False |

## Multicollinearity Check

| term | vif |
| --- | --- |
| footfall | 6.43 |
| staff_count | 6.36 |
| store_type_High Street | 3.27 |
| store_type_Residential | 3.18 |
| store_type_Mall | 2.82 |
| region_West | 1.41 |
| region_North | 1.38 |
| region_South | 1.34 |
| marketing_spend | 1.07 |
| holiday_flag | 1.06 |
| avg_discount_pct | 1.06 |
| customer_rating | 1.06 |
| competitor_distance_km | 1.05 |
| inventory_availability_pct | 1.04 |

## Interpretation

- The model explains 84.85% of variation in monthly sales after adjusting for predictor count.
- Statistically significant predictors at alpha 0.05 are: footfall, marketing_spend, competitor_distance_km, inventory_availability_pct, store_type_Residential, region_West, region_South, staff_count, customer_rating, store_type_High Street, holiday_flag, region_North.
- Positive coefficients indicate higher predicted monthly sales holding other model variables constant; negative coefficients indicate lower predicted monthly sales.

## Recommendation

Use the significant operational drivers as priority levers, but treat the result as observational. The model supports association, not proof of causality.

## Limitation

The model uses 306 of 320 source rows because `competitor_distance_km` and `customer_rating` have missing values.
