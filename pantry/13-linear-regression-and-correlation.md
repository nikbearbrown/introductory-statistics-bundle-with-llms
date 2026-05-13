# Pantry — Linear Regression and Correlation

Reference material, worked examples, and calculation details for Chapter 13.

---

## Correlation coefficient: Step-by-step calculation

**Example data:** Advertising spend and sales for 6 months.

| Month | Ad Spend (*x*, thousands) | Sales (*y*, thousands) |
|-------|--------------------------|----------------------|
| 1     | 10                       | 25                   |
| 2     | 15                       | 35                   |
| 3     | 12                       | 30                   |
| 4     | 18                       | 40                   |
| 5     | 20                       | 50                   |
| 6     | 25                       | 60                   |

**Step 1: Calculate means.**

$\bar{x} = \frac{10 + 15 + 12 + 18 + 20 + 25}{6} = \frac{100}{6} = 16.67$

$\bar{y} = \frac{25 + 35 + 30 + 40 + 50 + 60}{6} = \frac{240}{6} = 40$

**Step 2: Calculate deviations from mean.**

| Month | $x_{i} - \bar{x}$ | $y_{i} - \bar{y}$ |
|-------|-----------------|-----------------|
| 1     | −6.67           | −15             |
| 2     | −1.67           | −5              |
| 3     | −4.67           | −10             |
| 4     | 1.33            | 0               |
| 5     | 3.33            | 10              |
| 6     | 8.33            | 20              |

**Step 3: Calculate products of deviations.**

| Month | $(x_{i} - \bar{x})(y_{i} - \bar{y})$ |
|-------|--------------------------------------|
| 1     | (−6.67)(−15) = 100.05               |
| 2     | (−1.67)(−5) = 8.35                  |
| 3     | (−4.67)(−10) = 46.70                |
| 4     | (1.33)(0) = 0                       |
| 5     | (3.33)(10) = 33.30                  |
| 6     | (8.33)(20) = 166.60                 |

Sum = 355.00

**Step 4: Calculate squared deviations.**

| Month | $(x_{i} - \bar{x})^{2}$ | $(y_{i} - \bar{y})^{2}$ |
|-------|-------------------------|-------------------------|
| 1     | 44.49                   | 225                     |
| 2     | 2.79                    | 25                      |
| 3     | 21.81                   | 100                     |
| 4     | 1.77                    | 0                       |
| 5     | 11.09                   | 100                     |
| 6     | 69.39                   | 400                     |

$\sum (x_{i} - \bar{x})^{2} = 151.34$

$\sum (y_{i} - \bar{y})^{2} = 850$

**Step 5: Calculate correlation.**

$$r = \frac{355.00}{\sqrt{151.34 \times 850}} = \frac{355.00}{\sqrt{128,639}} = \frac{355.00}{358.66} = 0.990$$

A correlation of 0.99 indicates nearly perfect positive linear relationship between ad spend and sales.

---

## Regression line: Deriving slope and intercept

Using the same data as above:

$\bar{x} = 16.67$, $\bar{y} = 40$, $r = 0.990$

Calculate standard deviations:

$$s_{x} = \sqrt{\frac{\sum(x_{i} - \bar{x})^{2}}{n-1}} = \sqrt{\frac{151.34}{5}} = \sqrt{30.27} = 5.50$$

$$s_{y} = \sqrt{\frac{\sum(y_{i} - \bar{y})^{2}}{n-1}} = \sqrt{\frac{850}{5}} = \sqrt{170} = 13.04$$

**Calculate slope:**

$$b_{1} = r \left( \frac{s_{y}}{s_{x}} \right) = 0.990 \times \frac{13.04}{5.50} = 0.990 \times 2.37 = 2.35$$

For each thousand dollars of additional ad spend, sales are predicted to increase by 2.35 thousand dollars (or $2,350).

**Calculate intercept:**

$$b_{0} = \bar{y} - b_{1}\bar{x} = 40 - 2.35 \times 16.67 = 40 - 39.18 = 0.82$$

**Regression equation:**

$$\hat{y} = 0.82 + 2.35x$$

**Prediction:** If ad spend is $22,000 (*x* = 22):

$$\hat{y} = 0.82 + 2.35 \times 22 = 0.82 + 51.70 = 52.52$$

Predicted sales: $52,520.

---

## Residuals and $R^{2}$

Using the fitted equation $\hat{y} = 0.82 + 2.35x$:

| Month | Actual *y* | Predicted $\hat{y}$ | Residual $e_{i}$ |
|-------|-----------|------------------|----------------|
| 1     | 25        | 0.82 + 2.35(10) = 24.32 | 25 − 24.32 = 0.68 |
| 2     | 35        | 0.82 + 2.35(15) = 35.07 | 35 − 35.07 = −0.07 |
| 3     | 30        | 0.82 + 2.35(12) = 29.02 | 30 − 29.02 = 0.98 |
| 4     | 40        | 0.82 + 2.35(18) = 42.12 | 40 − 42.12 = −2.12 |
| 5     | 50        | 0.82 + 2.35(20) = 47.82 | 50 − 47.82 = 2.18 |
| 6     | 60        | 0.82 + 2.35(25) = 59.57 | 60 − 59.57 = 0.43 |

**Sum of squared residuals (SSE):**

$SSE = (0.68)^{2} + (−0.07)^{2} + (0.98)^{2} + (−2.12)^{2} + (2.18)^{2} + (0.43)^{2}$

$SSE = 0.46 + 0.01 + 0.96 + 4.49 + 4.75 + 0.18 = 10.85$

**Total sum of squares (SST):**

From earlier: $\sum (y_{i} - \bar{y})^{2} = 850$

**Coefficient of determination:**

$$R^{2} = 1 - \frac{SSE}{SST} = 1 - \frac{10.85}{850} = 1 - 0.0128 = 0.9872$$

Or: $R^{2} = r^{2} = (0.990)^{2} = 0.9801$ (slight rounding difference).

The regression line explains 98.72% of the variation in sales. Only 1.28% is unexplained residual error. This is an excellent fit.

---

## Regression with education and earnings data

**Scenario:** Cross-sectional data for 50 occupation categories.

Mean years of education: 14.5
SD of education: 2.8
Mean annual earnings: $52,000
SD of earnings: $18,000
Correlation: *r* = 0.78

**Calculate slope:**

$$b_{1} = 0.78 \times \frac{18,000}{2.8} = 0.78 \times 6,428.57 = 5,014.29$$

Each additional year of education is associated with approximately $5,014 more in annual earnings.

**Calculate intercept:**

$$b_{0} = 52,000 - 5,014.29 \times 14.5 = 52,000 - 72,707.2 = -20,707.20$$

The negative intercept is not meaningful here (you cannot have negative education), but it shows the line extrapolates poorly outside the observed range.

**Equation:**

$$\hat{\text{Earnings}} = -20,707 + 5,014 \times \text{Education}$$

**Prediction for 16 years of education:**

$\hat{\text{Earnings}} = -20,707 + 5,014 \times 16 = -20,707 + 80,224 = 59,517$

Predicted earnings: approximately $59,517.

**Calculate $R^{2}$:**

$R^{2} = (0.78)^{2} = 0.6084$

The model explains 60.84% of variation in earnings. This is a typical value for cross-sectional data. The remaining 39.16% reflects other factors: field of work, location, experience, ability, luck, measurement error.

---

## Testing whether a correlation is statistically significant

**Question:** Is a correlation of *r* = 0.32 based on *n* = 25 observations statistically significant at the 0.05 level?

**Method 1: Using the t-test**

The test statistic is:

$$t = \frac{r\sqrt{n-2}}{\sqrt{1-r^{2}}} = \frac{0.32\sqrt{25-2}}{\sqrt{1-0.32^{2}}} = \frac{0.32\sqrt{23}}{\sqrt{0.8976}} = \frac{0.32 \times 4.796}{0.9475} = \frac{1.535}{0.9475} = 1.620$$

Degrees of freedom: *df* = *n* − 2 = 23.

Critical value at *α* = 0.05, two-tailed: *t*<sub>crit</sub> ≈ 2.069.

Since 1.620 < 2.069, we fail to reject the null hypothesis. The correlation is not statistically significant at the 0.05 level. We cannot conclude that there is a real linear relationship in the population.

**Method 2: Using the 2/√n rule**

For a quick approximation, a correlation is statistically significant at the ≈ 0.05 level if:

$$|r| \geq \frac{2}{\sqrt{n}}$$

For *n* = 25:

$$\frac{2}{\sqrt{25}} = \frac{2}{5} = 0.40$$

Since |*r*| = 0.32 < 0.40, the correlation is not significant.

For *n* = 100:

$$\frac{2}{\sqrt{100}} = \frac{2}{10} = 0.20$$

A correlation of 0.32 would be significant with 100 observations but not with 25.

---

## Interpreting regression coefficients with different units

**Scenario 1: Predicting salary from age**

Equation: $\hat{\text{Salary}} = 30,000 + 2,500 \times \text{Age}$

Interpretation: Each additional year of age is associated with $2,500 more in annual salary. If someone is 10 years older, we predict they earn $25,000 more.

**Scenario 2: Predicting height (cm) from weight (kg)**

Equation: $\hat{\text{Height}} = 120 + 0.85 \times \text{Weight}$

Interpretation: Each additional kilogram of weight is associated with 0.85 cm more in height.

**Scenario 3: Predicting test score from hours studied**

Equation: $\hat{\text{Score}} = 45 + 8 \times \text{Hours}$

Interpretation: Each additional hour of study is associated with 8 additional points on the test. Five hours of study corresponds to a 40-point increase in predicted score.

---

## Common pitfalls and how to avoid them

**Pitfall 1: Confusing $r$ and $b$ (correlation and slope)**

*r* = correlation. It is unitless and ranges from −1 to 1.

*b* = slope. It has units (dollars per year, points per hour, etc.) and can be any value.

A correlation of 0.5 can correspond to a slope of 2 or 200, depending on the ratio of standard deviations of the two variables.

**Pitfall 2: Interpreting $R^{2}$ as a percentage correctly**

$R^{2}$ = 0.64 means 64% of variation is explained, not "64% of the variation is explained by X and Y." The explanation comes from X alone (in simple regression).

$R^{2}$ = 0.64 also does NOT mean "64% of the predictions are correct." It is a measure of explained variance, not prediction accuracy.

**Pitfall 3: Assuming linearity without checking**

Always plot the scatter. If the relationship is curved, a linear regression will fit poorly. The $R^{2}$ and residual plot will show this.

**Pitfall 4: Extrapolating beyond the data range**

The regression line is fit to the data you observe. Predicting far beyond that range is unreliable. The relationship might curve, level off, or reverse.

**Pitfall 5: Causation from association**

Correlation does not imply causation. Association with a confounding third variable can make *x* and *y* move together without either causing the other.

---

## Quick reference formulas

Slope: $b_{1} = r \times \frac{s_{y}}{s_{x}}$

Intercept: $b_{0} = \bar{y} - b_{1} \bar{x}$

Fitted value: $\hat{y}_{i} = b_{0} + b_{1} x_{i}$

Residual: $e_{i} = y_{i} - \hat{y}_{i}$

Sum of squared errors: $SSE = \sum e_{i}^{2}$

Total sum of squares: $SST = \sum (y_{i} - \bar{y})^{2}$

Coefficient of determination: $R^{2} = \frac{SST - SSE}{SST} = 1 - \frac{SSE}{SST}$

For simple regression: $R^{2} = r^{2}$

---
