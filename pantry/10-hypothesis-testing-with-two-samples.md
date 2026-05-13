# Pantry — Chapter 10

## Welch-Satterthwaite Degrees of Freedom

When sample sizes are unequal or small, the simple approximation $df = n_1 + n_2 - 2$ is inaccurate. Use the Welch-Satterthwaite formula instead:

$$df = \frac{\left(\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}\right)^2}{\frac{1}{n_1-1}\left(\frac{s_1^2}{n_1}\right)^2 + \frac{1}{n_2-1}\left(\frac{s_2^2}{n_2}\right)^2}$$

This formula accounts for the fact that when variances or sample sizes differ, the degrees of freedom should be adjusted downward from the simple $n_1 + n_2 - 2$. Most statistical software uses this formula automatically for the unpooled test (Welch's t-test).

## Levene's Test for Equal Variances

Before choosing between pooled and unpooled variance, some statisticians recommend testing whether the population variances are equal. Levene's test is a preliminary hypothesis test:

- $H_0: \sigma_1^2 = \sigma_2^2$ (variances are equal)
- $H_a: \sigma_1^2 \neq \sigma_2^2$ (variances differ)

If Levene's test fails to reject (large p-value), you have weak evidence that variances differ, and pooling is safe. If it rejects (small p-value), variances likely differ, and you should use the unpooled test.

Caveat: Levene's test itself has assumptions and can be sensitive to deviations from normality. Many modern statisticians prefer to use unpooled always, treating it as the safer default.

## Cohen's d for Paired Data

When comparing paired samples, Cohen's *d* uses the standard deviation of the *differences*, not the pooled standard deviation of the two groups:

$$d = \frac{\bar{d}}{s_d}$$

A Cohen's *d* for paired data of 0.2 is small, 0.5 is medium, 0.8 is large. This is comparable to the cutoffs for independent samples but computed differently because the paired design has only one sample of differences.

## Confidence Intervals for the Difference of Means

A $(1 - \alpha) \times 100\%$ confidence interval for the difference between two population means is:

$$(\bar{x}_1 - \bar{x}_2) \pm t_{\alpha/2, df} \cdot \text{SE}(\bar{x}_1 - \bar{x}_2)$$

where $t_{\alpha/2, df}$ is the critical value from the t-distribution with the appropriate degrees of freedom, and SE is computed using the unpooled formula.

**Example:** In the brake pad study, with $n_1 = 35, n_2 = 42, \bar{x}_1 = 49,200, \bar{x}_2 = 50,800, \text{SE} \approx 689$, and $df = 75$, the critical value $t_{0.025, 75} \approx 1.99$. The 95% CI is:

$$(49,200 - 50,800) \pm 1.99 \cdot 689 = -1,600 \pm 1,371 = (-2,971, -229)$$

Interpretation: We are 95% confident the true difference (Midwest mean minus West Coast mean) is between −2,971 and −229 miles. Since the interval does not contain zero, this is consistent with rejecting the null hypothesis at $\alpha = 0.05$.

## Confidence Intervals for the Difference of Proportions

A $(1 - \alpha) \times 100\%$ confidence interval for the difference between two population proportions is:

$$(\hat{p}_1 - \hat{p}_2) \pm z_{\alpha/2} \sqrt{\frac{\hat{p}_1(1-\hat{p}_1)}{n_1} + \frac{\hat{p}_2(1-\hat{p}_2)}{n_2}}$$

**Note:** This uses the *unpooled* standard error (each proportion estimated separately), not the pooled proportion from the hypothesis test. This is correct for confidence intervals but different from hypothesis testing.

**Example:** In the unemployment study, $\hat{p}_1 = 0.12, \hat{p}_2 = 0.10, n_1 = 400, n_2 = 450$, and $z_{0.025} = 1.96$. The 95% CI is:

$$(0.12 - 0.10) \pm 1.96 \sqrt{\frac{0.12 \cdot 0.88}{400} + \frac{0.10 \cdot 0.90}{450}}$$

$$= 0.02 \pm 1.96 \sqrt{0.000264 + 0.000200} = 0.02 \pm 1.96 \cdot 0.0215 = 0.02 \pm 0.042 = (-0.022, 0.062)$$

Interpretation: The 95% CI is (−2.2, 6.2) percentage points. Since the interval contains zero, we cannot conclude the two cities' unemployment rates differ at the 0.05 level—consistent with our earlier hypothesis test result.

## Power and Sample Size

The power of a two-sample test (probability of correctly rejecting a false null hypothesis) depends on:
1. Effect size (how different the populations truly are)
2. Sample sizes (larger samples give more power)
3. Significance level (lower $\alpha$ reduces power)
4. Whether the test is one-tailed or two-tailed (one-tailed has more power)

Rough power guidelines for two-sample t-tests with equal sample sizes:
- To detect a small effect ($d = 0.2$) with 80% power: ~400 subjects per group.
- To detect a medium effect ($d = 0.5$) with 80% power: ~64 subjects per group.
- To detect a large effect ($d = 0.8$) with 80% power: ~26 subjects per group.

Sample size calculators are available in R (`power.t.test`), online, or in statistical textbooks. Power analysis is crucial before conducting an expensive or time-consuming study.

## When the Equal Variance Assumption Fails: Practical Advice

If you suspect the population variances are unequal:
1. Use the unpooled (Welch) test. It's robust to violations of the equal variance assumption.
2. If sample sizes are very small ($n_1, n_2 < 10$), ensure the data are approximately normally distributed. Check a Q-Q plot.
3. Consider a log transformation if the data are right-skewed and heterogeneous in variance.
4. As a last resort, use a nonparametric test like the Mann-Whitney U test (rank-based, doesn't assume normality). This is beyond the scope of this chapter but is available in most statistical software.

## Paired vs. Independent: How to Decide

**Use paired when:**
- The same subject is measured twice (before/after).
- Subjects are matched on key characteristics before treatment assignment.
- Data come from matched pairs in the study design.

**Use independent when:**
- Two completely different groups are compared (no matching).
- You have no information linking individuals in one group to individuals in the other.

Pairing must be incorporated into the analysis. Don't pair in your data preparation if pairing wasn't in your study design—you'll introduce bias.

## Handling Missing Data in Paired Studies

If one subject drops out of a paired study, you lose both their before and after measurements (or both matched pairs). Unlike independent samples (where you can analyze the remaining subjects), paired data require complete pairs.

**Options:**
1. Use available-case analysis: delete the incomplete pair and analyze the rest. This reduces power but is unbiased if data are missing completely at random.
2. Imputation: estimate the missing value using the other group's mean or a regression prediction. This is more advanced and requires careful assumptions.
3. Sensitivity analysis: report results under both options to show how sensitive conclusions are to the missing data.

## Two-Proportion Test Conditions: What Goes Wrong

**Problem 1: Small expected frequencies.** If the number of successes or failures is less than 5 in any cell, the normal approximation is poor. Use Fisher's exact test (for 2×2 tables) or simulation.

**Problem 2: Extreme proportions.** If $\hat{p}_1 \approx 0$ or $\hat{p}_1 \approx 1$, the normal approximation fails. Use exact binomial methods.

**Problem 3: Dependent samples.** If the two samples are not independent (e.g., both contain some of the same people, or measurements are correlated), the formula is wrong. Use McNemar's test for paired proportions instead.

## Effect Size in Terms of "Number Needed to Treat" (NNT)

In clinical contexts, Cohen's *d* is sometimes converted to **Number Needed to Treat (NNT)**—the number of patients you must treat with the new drug to prevent one additional bad outcome compared to the control.

For a binary outcome (yes/no):
$$\text{NNT} = \frac{1}{p_{\text{treatment}} - p_{\text{control}}}$$

**Example:** If 30% of patients on the new drug recover, vs. 20% on placebo, then $\text{NNT} = 1/(0.30 - 0.20) = 10$. You must treat 10 patients to prevent one additional failure.

For continuous outcomes, NNT can be approximated from Cohen's *d*, but the interpretation is less direct. Always report effect size and p-value together.

