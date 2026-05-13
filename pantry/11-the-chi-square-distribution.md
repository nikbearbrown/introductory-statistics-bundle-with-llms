# Pantry: Chapter 11 — The Chi-Square Distribution

## Key terms and formulas

### Chi-square distribution ($\chi^2$)

A probability distribution that measures the sum of squared, standardized deviations. Used to test categorical data (counts in categories, not measurements). Always nonnegative. Always right-tailed.

**Notation:** $X^2 \sim \chi_{df}^2$ (read: X squared follows chi-square with $df$ degrees of freedom).

**Definition:** If $Z_1, Z_2, \ldots, Z_k$ are independent standard normal random variables, then $\chi^2 = Z_1^2 + Z_2^2 + \cdots + Z_k^2$ follows a chi-square distribution with $k$ degrees of freedom.

**Shape:** Right-skewed. As $df$ increases, approaches normal distribution.

**Mean:** $\mu = df$
**Standard deviation:** $\sigma = \sqrt{2 \cdot df}$

---

### Degrees of freedom (df)

The number of independent pieces of information available to estimate a parameter or test a hypothesis. In chi-square:

- **Goodness-of-fit:** $df = (\text{number of categories}) - 1$
- **Test of independence:** $df = (\text{rows} - 1) \times (\text{columns} - 1)$
- **Test of single variance:** $df = n - 1$

Intuition: Once you know the sum and the first $df$ values, the remaining value is determined.

---

### Observed count ($O$)

The actual frequency in each category, collected from data.

---

### Expected count ($E$)

The frequency you would expect in each category if the null hypothesis were true, calculated from theory or the null distribution.

In a **goodness-of-fit test:** $E = (\text{hypothesized proportion}) \times n$ for each category.

In a **test of independence:** $E = \frac{(\text{row total}) \times (\text{column total})}{\text{grand total}}$ for each cell.

**Critical assumption:** Each expected count must be at least 5 (or sometimes 3, but 5 is the conservative standard). If violated, combine categories.

---

### Chi-square test statistic

$$\chi^2 = \sum \frac{(O - E)^2}{E}$$

Measures total squared deviation between observed and expected, standardized by expected count.

- Large $\chi^2$ means observed deviates far from expected.
- Small $\chi^2$ means observed matches expected well.
- Always nonnegative.
- Always produces a right-tailed test (reject when $\chi^2$ is unusually large).

---

### Goodness-of-fit test

A chi-square test that asks: *Do observed counts fit a proposed distribution?*

**Null:** Data come from the proposed distribution (observed matches expected).
**Alternative:** Data do not fit the proposed distribution.
**Test statistic:** $\chi^2 = \sum \frac{(O - E)^2}{E}$
**Degrees of freedom:** $df = k - 1$ where $k$ is the number of categories.
**Always:** Right-tailed.

---

### Test of independence

A chi-square test that asks: *Are two categorical factors independent, or are they associated?*

Used with contingency tables (two-way tables with row and column counts).

**Null:** The two factors are independent (knowing one tells you nothing about the other).
**Alternative:** The factors are dependent (knowing one helps predict the other).
**Test statistic:** $\chi^2 = \sum \sum \frac{(O_{ij} - E_{ij})^2}{E_{ij}}$
**Degrees of freedom:** $df = (\text{rows} - 1) \times (\text{columns} - 1)$
**Expected frequency formula:** $E_{ij} = \frac{(\text{row total}_i) \times (\text{column total}_j)}{\text{grand total}}$
**Always:** Right-tailed.

**Critical caveat:** A significant test shows association, NOT causation. The variables are related, but which causes which—or whether they're both caused by something else—requires additional reasoning.

---

### Contingency table

A two-way table displaying counts for two categorical variables. Rows represent one variable, columns represent another. Cells contain the count of observations in each combination.

**Row totals:** Sum across the row (across all columns).
**Column totals:** Sum down the column (across all rows).
**Grand total:** Sum of all cells (or sum of all row totals, or sum of all column totals).

---

### Independence (statistical)

Two variables are **independent** if knowing the value of one tells you nothing about the probable value of the other. Mathematically: $P(A \text{ and } B) = P(A) \times P(B)$.

In a contingency table: the proportion in each column is the same for every row (and vice versa).

**Not the same as:** causation, no correlation, zero difference.

---

### Scale shift

A principle that allows combining results across multiple independent studies or tests:

- One goodness-of-fit test produces one $\chi^2$ with one $df$.
- Two independent tests produce $\chi^2_{\text{combined}} = \chi^2_1 + \chi^2_2$ with $df_{\text{combined}} = df_1 + df_2$.

This is how meta-analyses detect patterns that individual studies miss due to noise.

---

## Red flags and assumptions

1. **Each expected count must be at least 5** (minimum; 3 acceptable in some textbooks, but 5 is standard). If violated, combine categories until all expected counts ≥ 5. This is not optional.

2. **Chi-square is always right-tailed.** Reject the null when the test statistic is unusually *large*, never when it's unusually *small*. This is because the test statistic is a sum of squared deviations.

3. **Association ≠ causation.** A significant test of independence shows that two variables are related. It does not show which one causes the other, or whether both are caused by a third variable. Interpret with care.

4. **Verify independence of observations.** Each observation should be independent of the others. Violations (e.g., repeated measures, clustered data) invalidate the test.

5. **Choose the right null distribution.** In goodness-of-fit, the expected counts must flow from a reasonable hypothesis about the population distribution. If the null is wrong, high chi-square just means the world didn't match your wrong guess.

---

## Worked calculation checklist

**Goodness-of-fit:**
- [ ] State hypotheses in words.
- [ ] Verify each expected count ≥ 5. If not, combine categories.
- [ ] Build table: category, $O$, $E$, $O - E$, $(O - E)^2$, $\frac{(O - E)^2}{E}$.
- [ ] Sum the last column to get $\chi^2$.
- [ ] Calculate $df = k - 1$.
- [ ] Find critical value or p-value.
- [ ] Compare statistic to critical value (or p-value to $\alpha$).
- [ ] State conclusion in context.

**Test of independence:**
- [ ] State hypotheses in words.
- [ ] Verify each expected count ≥ 5. Calculate with row total × column total / grand total.
- [ ] Build table: each cell shows $O$, below it $E$.
- [ ] Calculate $\chi^2$ across all cells.
- [ ] Calculate $df = (\text{rows} - 1) \times (\text{columns} - 1)$.
- [ ] Find critical value or p-value.
- [ ] Compare statistic to critical value (or p-value to $\alpha$).
- [ ] State conclusion in context (avoid causal language).

---

## Compared to other tests

| Test | Data type | What it tests | Distribution |
|---|---|---|---|
| **Chi-square goodness-of-fit** | Counts in categories | Do data fit a proposed distribution? | Chi-square |
| **Chi-square independence** | Counts in 2×2+ table | Are two categorical variables related? | Chi-square |
| **t-test (one sample)** | Measurements | Does the mean differ from $\mu_0$? | Student's t |
| **z-test (one proportion)** | Binary counts | Does the proportion differ from $p_0$? | Standard normal |
| **Test of single variance** | Measurements | Does the variance differ from $\sigma_0^2$? | Chi-square |

---

## Etymology

**Chi** ($\chi$): A Greek letter, looks like the Latin "X". The chi-square distribution is named after the shape $\chi^2$ notation used in older statistics texts (the superscript 2 indicating squaring).

**Degrees of freedom**: A concept from mechanics (moving parts have "freedom" to move). In statistics, the number of values that can vary freely before the constraint (the sum, or the row/column totals) determines the rest.

**Independence**: From probability and everyday English. Two events are independent if one doesn't affect the other.

**Contingency**: "Depending on," from Latin *contingere*. A contingency table shows how counts are contingent on (related to) two categorical variables.

---

## Quick lookup: Critical values for common α levels

For a goodness-of-fit test with 4 categories ($df = 3$):
- $\alpha = 0.05$: critical value ≈ 7.815
- $\alpha = 0.01$: critical value ≈ 11.345

For a 2×2 test of independence ($df = 1$):
- $\alpha = 0.05$: critical value ≈ 3.841
- $\alpha = 0.01$: critical value ≈ 6.635

(Use a chi-square table or calculator for specific values.)

---

## Limits and caveats

1. **Small sample sizes and sparse tables:** Chi-square loses power when many cells have small expected counts. Combine categories, increase sample size, or use Fisher's exact test for 2×2 tables.

2. **Non-independent observations:** If observations are clustered or repeated, chi-square breaks down. Use methods designed for that structure (mixed models, generalized estimating equations).

3. **Misspecified null:** If your expected distribution is wildly wrong, chi-square just measures misfit to a bad model. Always check that your null hypothesis is sensible.

4. **Direction of association:** Chi-square tests for independence tell you whether association exists, not how strong it is or in which direction. Use Cramér's V or other measures of association for effect size.

---
