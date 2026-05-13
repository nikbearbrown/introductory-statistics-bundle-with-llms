# Pantry: Chapter 12 — F-Distribution and One-Way ANOVA

Reference formulas, definitions, and computational details.

---

## Formulas

### F-Test for Equality of Two Variances

$$F = \frac{s_1^2}{s_2^2}$$

Degrees of freedom: $df_{\text{numerator}} = n_1 - 1$, $df_{\text{denominator}} = n_2 - 1$.

By convention, place the larger sample variance in the numerator.

Hypotheses:
- Two-tailed: $H_0: \sigma_1^2 = \sigma_2^2$ vs $H_a: \sigma_1^2 \neq \sigma_2^2$
- One-tailed (right): $H_0: \sigma_1^2 \leq \sigma_2^2$ vs $H_a: \sigma_1^2 > \sigma_2^2$
- One-tailed (left): $H_0: \sigma_1^2 \geq \sigma_2^2$ vs $H_a: \sigma_1^2 < \sigma_2^2$

### One-Way ANOVA

**Sum of Squares:**

$$SS_{\text{total}} = \sum_{i=1}^{n} (x_i - \bar{x}_{\text{grand}})^2$$

$$SS_{\text{between}} = \sum_{j=1}^{k} n_j (\bar{x}_j - \bar{x}_{\text{grand}})^2$$

$$SS_{\text{within}} = SS_{\text{total}} - SS_{\text{between}}$$

Alternatively:
$$SS_{\text{within}} = \sum_{j=1}^{k} \sum_{i \in \text{group } j} (x_i - \bar{x}_j)^2$$

**Mean Squares:**

$$MS_{\text{between}} = \frac{SS_{\text{between}}}{k - 1}$$

$$MS_{\text{within}} = \frac{SS_{\text{within}}}{n - k}$$

**F-Statistic:**

$$F = \frac{MS_{\text{between}}}{MS_{\text{within}}}$$

Degrees of freedom: $df_{\text{numerator}} = k - 1$, $df_{\text{denominator}} = n - k$.

**Hypotheses:**

$$H_0: \mu_1 = \mu_2 = \cdots = \mu_k$$

$$H_a: \text{At least two group means are not equal}$$

### Alternative Formula for Balanced Designs (Equal Sample Sizes)

When all groups have size $n_0$:

$$F = \frac{n_0 \cdot s_{\bar{x}}^2}{s_{\text{pooled}}^2}$$

where $s_{\bar{x}}^2$ is the variance of the group means and $s_{\text{pooled}}^2$ is the mean of the sample variances within each group.

---

## Computational Shortcut: Raw Sums for Hand Calculation

When computing by hand, the following formulas reduce rounding error:

Let $s_j = \sum_{i \in \text{group } j} x_i$ (sum of values in group $j$).

Let $\sum x = \sum_{i=1}^{n} x_i$ (sum of all values).

Let $\sum x^2 = \sum_{i=1}^{n} x_i^2$ (sum of all squared values).

$$SS_{\text{total}} = \sum x^2 - \frac{(\sum x)^2}{n}$$

$$SS_{\text{between}} = \sum_{j=1}^{k} \frac{(s_j)^2}{n_j} - \frac{(\sum x)^2}{n}$$

$$SS_{\text{within}} = SS_{\text{total}} - SS_{\text{between}}$$

---

## ANOVA Table Template

| Source | Sum of Squares | df | Mean Square | F | p-value |
|--------|----------------|----|-------------|----|----|
| Between (Factor) | $SS_B$ | $k-1$ | $MS_B$ | $F$ | $P(F_{{k-1},{n-k}} > F_{\text{obs}})$ |
| Within (Error) | $SS_W$ | $n-k$ | $MS_W$ | | |
| Total | $SS_T$ | $n-1$ | | | |

---

## Key Assumptions and Checks

### Assumptions for ANOVA

1. **Normality:** Each group is approximately normally distributed.
   - Check: Q-Q plot, Shapiro-Wilk test.
   - Robustness: ANOVA tolerates mild departures, especially with large, equal sample sizes.

2. **Homogeneity of Variance (Equal Variances):** All groups have equal population variance.
   - Check: Levene's test, Bartlett's test, side-by-side boxplots.
   - Robustness: ANOVA is fairly robust with balanced designs.
   - Alternative: If variances are unequal, use Welch's ANOVA.

3. **Independence:** Observations are independent within and between groups.
   - Check: Study design (e.g., random assignment, no repeated measures on same subjects).
   - Violation: Can severely bias results.

### Violations and Remedies

| Issue | Symptom | Remedy |
|-------|---------|--------|
| Non-normality (mild) | Histogram slightly skewed | Proceed with caution |
| Non-normality (severe) | Extreme skewness or outliers | Log or square-root transformation; Kruskal-Wallis test |
| Unequal variances (mild) | Variance ratios < 3:1 | Standard ANOVA often sufficient |
| Unequal variances (severe) | Variance ratios > 3:1 or Levene's test significant | Welch's ANOVA |
| Non-independence | Data clustered by unmeasured grouping | Mixed-effects model |

---

## Degrees of Freedom Reference

| Situation | df |
|-----------|-----|
| Numerator (between-groups) | $k - 1$ |
| Denominator (within-groups) | $n - k$ |
| Total | $n - 1$ |
| Per group | $n_j - 1$ |

where $k$ = number of groups, $n$ = total sample size, $n_j$ = sample size in group $j$.

---

## Interpretation Guide

### Decision Rule

At significance level $\alpha$:
- Find critical value $F_{\alpha, k-1, n-k}$ from F-table or software.
- If observed $F > F_{\alpha}$, reject $H_0$.
- Equivalently, if p-value $< \alpha$, reject $H_0$.

### Describing Results

If $H_0$ is rejected:
- "There is sufficient evidence (at the $\alpha$ level) that at least one group mean differs."
- Follow with post-hoc pairwise comparisons (Tukey, Bonferroni, etc.) to identify which groups differ.

If $H_0$ is not rejected:
- "There is insufficient evidence (at the $\alpha$ level) that group means differ."

### The Omnibus Nature of the Test

ANOVA tests whether *any* group differs. It does not identify which groups differ.

If groups differ, you must follow up with:
- Tukey's HSD (Honestly Significant Difference)
- Bonferroni-corrected t-tests
- Scheffé test
- Dunnett's test (if comparing treatment groups to a control)

---

## F-Distribution Properties

- **Support:** $F \geq 0$ (always non-negative).
- **Shape:** Right-skewed; shape depends on degrees of freedom.
- **Mean:** $\mu = \frac{df_2}{df_2 - 2}$ for $df_2 > 2$.
- **Asymptotic behavior:** As $df_1$ and $df_2$ increase, F approaches a normal distribution (but retains right skew).
- **Relationship to chi-squared:** $F = \frac{\chi^2_1 / df_1}{\chi^2_2 / df_2}$.

---

## When to Use Each Test

| Test | Question | Condition |
|------|----------|-----------|
| F-test for two variances | Do two populations have equal variance? | Exploratory; not typically the main question |
| One-way ANOVA | Do three or more group means differ? | Groups are independent; continuous outcome |
| Kruskal-Wallis | Do three or more groups differ (non-parametric)? | Non-normal data; ordinal outcome |
| Welch's ANOVA | Do three or more group means differ (unequal variances)? | Variances are unequal |
| Repeated-measures ANOVA | Does the same group's mean change across conditions? | Same subjects measured multiple times |

---

## Example Calculation Worked Through

**Data:** Three teaching methods, 4 students each.

| Method A | Method B | Method C |
|----------|----------|----------|
| 80       | 82       | 88       |
| 85       | 79       | 92       |
| 78       | 81       | 85       |
| 82       | 80       | 90       |

**Step 1: Compute group statistics.**
- Method A: sum = 325, mean = 81.25
- Method B: sum = 322, mean = 80.5
- Method C: sum = 355, mean = 88.75
- Grand total = 1002, grand mean = 83.5

**Step 2: Compute sums of squares.**

$SS_{\text{total}} = (80 - 83.5)^2 + (85 - 83.5)^2 + \cdots + (90 - 83.5)^2 = 398.5$

$SS_{\text{between}} = 4(81.25 - 83.5)^2 + 4(80.5 - 83.5)^2 + 4(88.75 - 83.5)^2 = 4(5.0625) + 4(9) + 4(27.5625) = 148.25$

$SS_{\text{within}} = 398.5 - 148.25 = 250.25$

**Step 3: Compute mean squares and F.**

$MS_{\text{between}} = 148.25 / 2 = 74.125$

$MS_{\text{within}} = 250.25 / 9 = 27.806$

$F = 74.125 / 27.806 = 2.665$

**Step 4: Find p-value and decide.**

With $df = (2, 9)$ and $F = 2.665$, p-value $\approx 0.126$.

At $\alpha = 0.05$: Since $p\text{-value} > 0.05$, do not reject $H_0$.

**Conclusion:** There is insufficient evidence that the three teaching methods produce different mean scores.

---

## Symbols and Notation Quick Reference

| Symbol | Meaning |
|--------|---------|
| $k$ | Number of groups |
| $n$ | Total sample size |
| $n_j$ | Sample size in group $j$ |
| $x_i$ | Individual observation |
| $\bar{x}_j$ | Mean of group $j$ |
| $\bar{x}_{\text{grand}}$ | Grand mean (mean of all observations) |
| $s_j^2$ | Variance within group $j$ |
| $SS$ | Sum of squares |
| $df$ | Degrees of freedom |
| $MS$ | Mean square (variance estimate) |
| $F$ | F test statistic; also F distribution |
| $H_0$ | Null hypothesis |
| $H_a$ | Alternative hypothesis |
| $\alpha$ | Significance level |
| $\mu_j$ | Population mean of group $j$ |
| $\sigma_j^2$ | Population variance of group $j$ |
