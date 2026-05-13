# Images and Figures — Chapter 13

Reference list of figures, charts, and diagrams embedded in or referenced by the chapter.

---

## Figure 1: Scatter plots and correlation strength

[FIGURE: Four scatter plots showing the same general upward trend, labeled with *r* = 1.0 (perfect alignment on line), *r* = 0.8 (tight cluster around line), *r* = 0.5 (moderate scatter around line), *r* = 0.2 (wide scatter, weak trend). Horizontal axis labeled "Variable X"; vertical axis labeled "Variable Y".]

**Caption:** Correlation coefficient *r* measures the strength and direction of linear relationship. As *r* decreases from 1 to 0, the data scatter more widely around the underlying trend. The slope of the cloud and the tightness of the cluster are both captured in the value of *r*.

---

## Figure 2: Positive, negative, and zero correlation

[FIGURE: Three side-by-side scatter plots. Left: points tilted upward left to right (*r* > 0, labeled "Positive correlation"). Middle: points tilted downward left to right (*r* < 0, labeled "Negative correlation"). Right: points in a circular blob with no clear tilt (*r* ≈ 0, labeled "No linear correlation"). Each labeled with axis: horizontal "Education Level" or "Study Hours"; vertical "Test Score" or "Exam Grade".]

**Caption:** The sign of *r* tells you the direction of association. Positive correlation means higher values of *x* tend to coincide with higher values of *y*. Negative correlation means higher values of *x* tend to coincide with lower values of *y*. Zero correlation means *x* and *y* move independently (at least in a linear sense).

---

## Figure 3: Regression line and least-squares fit

[FIGURE: Scatter plot of approximately 20 points with one straight line drawn through them. Several points are labeled with vertical line segments showing the distance from the point to the line (the residual). The line is labeled "*ŷ* = *b*₀ + *b*₁*x*". The residuals are labeled "positive residual" (point above line) and "negative residual" (point below line). Title: "The Least-Squares Regression Line".]

**Caption:** The regression line minimizes the sum of squared residuals (vertical distances from points to line). Points above the line have positive residuals; points below have negative residuals. The line always passes through the point (*x̄*, *ȳ*), the mean of both variables.

---

## Figure 4: Regression to the mean

[FIGURE: Two columns of bars. Left column: parent heights (fathers, mothers, average), shown as bars of different lengths. Right column: offspring heights (children) as bars. The offspring bars are shorter than extreme parent bars, moving back toward the population mean height (horizontal dashed line). Arrows from parent bars to offspring bars show the regression toward the center.]

**Caption:** Galton's insight: children of very tall parents are tall, but not as tall on average as their parents. Children of very short parents are short, but not as short on average as their parents. This is regression to the mean. The regression line quantifies exactly how much of the parent-child difference we expect to regress back toward the population average.

---

## Figure 5: Residual plots: Good vs. bad fit

[FIGURE: Two panels. Top left: scatter plot with a fitted line and points scattered around it. Top right: residual plot (fitted values on horizontal axis, residuals on vertical axis) showing points randomly scattered above and below zero with no pattern, labeled "Good fit—random residuals." 

Bottom left: scatter plot where the fitted line is straight but the points curve around it. Bottom right: residual plot showing residuals that curve (points below line at edges, above in middle), labeled "Poor fit—curved pattern suggests nonlinear relationship".]

**Caption:** A residual plot helps diagnose model fit. If residuals scatter randomly with no pattern, the linear model is appropriate. If residuals show a pattern (curved, fanning, clustering), the linear assumption is violated and a better model is needed.

---

## Figure 6: $R^{2}$ and explained variation

[FIGURE: Three scatter plots with fitted lines. Left: *R*² = 0.95 (points tightly clustered around line). Middle: *R*² = 0.50 (points scattered moderately around line). Right: *R*² = 0.20 (points widely scattered; line is barely visible as a trend). Labels show: "Total variation = (bar showing total range)", "Explained variation = (bar showing fit quality)", "Unexplained variation = residuals (shown in light gray)".]

**Caption:** The coefficient of determination *R*² measures the proportion of total variance in *y* that is explained by the linear relationship with *x*. Higher *R*² means the line fits tighter and predictions are more reliable. Even with *R*² = 0.50, half the variation is unexplained.

---

## Figure 7: Extrapolation danger

[FIGURE: Two panels. Left: scatter plot showing data points clustering between *x* = 20 and *x* = 80, with a fitted line extending through and beyond them. Right: extended view of the same line extending far beyond the original data range (say, to *x* = 150), with a question mark at the end of the line. Label: "Extrapolation: unverified and unreliable".]

**Caption:** The regression line is fit to the data you observe. Predictions within that range (interpolation) are reliable. Predictions far outside the range (extrapolation) assume the linear relationship continues, which may not be true. The relationship may curve, plateau, or reverse in the unobserved region.

---

## Figure 8: Confounding and causation

[FIGURE: Conceptual diagram showing three variables. Two observed variables *X* and *Y* are shown with a double arrow between them (labeled "Correlation observed"). A third variable *C* (confounding variable) is shown above, with arrows pointing down to both *X* and *Y* (labeled "Causal effects"). Caption below reads: "Example: *X* = ice cream sales, *Y* = drowning deaths, *C* = warm weather. Ice cream and drowning are correlated, but neither causes the other—warm weather causes both.".]

**Caption:** Correlation between *x* and *y* can arise from a third variable *c* causing both. Regression quantifies the association between *x* and *y* but cannot distinguish whether *x* causes *y*, *y* causes *x*, or a confounding variable causes both. Causation requires experimental design or strong theory.

---

## Figure 9: Trade-off between fit and complexity

[FIGURE: Two lines on a single graph. Horizontal axis: "Model complexity (number of parameters)". Vertical axis: "R² (training data)" on the left, "Predictive accuracy (new data)" on the right. One line (labeled "Fit to training data") increases monotonically as complexity increases. Another line (labeled "Fit to new data") increases initially, peaks, then decreases as complexity increases (overfitting). Vertical dashed line marks the peak of the second line.]

**Caption:** Adding variables to a regression always increases *R*² on the training data, but it can decrease prediction accuracy on new data. This is overfitting. A simpler model with lower *R*² may predict new observations more accurately because it captures genuine patterns rather than fitting noise in the specific data you observed.

---

## Figure 10: The regression line in context

[FIGURE: Scatter plot of test score data (many points) with fitted regression line. Superimposed is a bell curve (normal distribution) at three x-values, centered on the regression line, showing the predicted distribution of *y* for each value of *x*. Shaded regions show the 95% confidence intervals around each predicted mean.]

**Caption:** The regression model assumes that at each value of *x*, the values of *y* are normally distributed around the fitted line with constant variance. This assumption allows us to construct confidence intervals and hypothesis tests. A residual plot will reveal if this assumption is severely violated.

---

## Data tables for worked examples

### Exam score data (10 students, for illustration)

| Student | Midterm | Final |
|---------|---------|-------|
| 1       | 65      | 60    |
| 2       | 70      | 75    |
| 3       | 75      | 80    |
| 4       | 80      | 82    |
| 5       | 85      | 87    |
| 6       | 72      | 70    |
| 7       | 88      | 91    |
| 8       | 68      | 72    |
| 9       | 92      | 95    |
| 10      | 78      | 81    |

Summary statistics:
- Mean midterm: 77.3
- Mean final: 79.3
- SD midterm: 8.9
- SD final: 10.2
- Correlation: *r* = 0.96

---

### Advertising and sales data (12 months)

| Month | Ad Spend ($K) | Sales ($K) |
|-------|---------------|-----------|
| Jan   | 8             | 22        |
| Feb   | 12            | 28        |
| Mar   | 10            | 26        |
| Apr   | 15            | 35        |
| May   | 18            | 40        |
| Jun   | 14            | 31        |
| Jul   | 20            | 45        |
| Aug   | 22            | 48        |
| Sep   | 16            | 36        |
| Oct   | 24            | 52        |
| Nov   | 18            | 42        |
| Dec   | 26            | 55        |

Summary statistics:
- Mean ad spend: 16.75
- Mean sales: 39.2
- SD ad spend: 6.3
- SD sales: 11.8
- Correlation: *r* = 0.98

---
