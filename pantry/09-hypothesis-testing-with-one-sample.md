# Pantry: Chapter 9 — Hypothesis Testing with One Sample

## Formulas and key equations

### Test statistic for a single population mean (σ known)
$$Z = \frac{\bar{x} - \mu_0}{\sigma/\sqrt{n}}$$

### Test statistic for a single population mean (σ unknown, use t-distribution)
$$t = \frac{\bar{x} - \mu_0}{s/\sqrt{n}}$$
Degrees of freedom: $df = n - 1$

### Test statistic for a single population proportion
$$Z = \frac{p' - p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}}$$
where $p' = x/n$ (sample proportion) and $q_0 = 1 - p_0$.

### Conditions for hypothesis test for a proportion
- $np_0 > 5$
- $nq_0 > 5$ (where $q_0 = 1 - p_0$)

---

## Decision rules

### Critical value approach (two-tailed)
- If $|Z| > Z_{\alpha/2}$ or $|t| > t_{\alpha/2, df}$, reject $H_0$.
- If $|Z| \leq Z_{\alpha/2}$ or $|t| \leq t_{\alpha/2, df}$, fail to reject $H_0$.

### P-value approach
- If p-value < α, reject $H_0$.
- If p-value ≥ α, fail to reject $H_0$.

---

## Common critical values (two-tailed)

| α | Z_critical | Confidence level |
|---|-----------|------------------|
| 0.10 | 1.645 | 90% |
| 0.05 | 1.96 | 95% |
| 0.01 | 2.576 | 99% |

For one-tailed tests, use half the α value when looking up critical values.

---

## Hypothesis setup patterns

### Testing a mean: Two-tailed
$H_0: \mu = \mu_0$
$H_a: \mu \neq \mu_0$

### Testing a mean: Right-tailed
$H_0: \mu \leq \mu_0$
$H_a: \mu > \mu_0$

### Testing a mean: Left-tailed
$H_0: \mu \geq \mu_0$
$H_a: \mu < \mu_0$

### Testing a proportion: Two-tailed
$H_0: p = p_0$
$H_a: p \neq p_0$

### Testing a proportion: Right-tailed
$H_0: p \leq p_0$
$H_a: p > p_0$

### Testing a proportion: Left-tailed
$H_0: p \geq p_0$
$H_a: p < p_0$

---

## Type I and Type II errors

| Actual truth | Reject H₀ | Fail to reject H₀ |
|---|---|---|
| H₀ is true | Type I error (α) | Correct |
| H₀ is false | Correct | Type II error (β) |

Power of the test = $1 - \beta$

---

## Quick reference: Which test statistic?

| Scenario | Test statistic |
|----------|---|
| $n \geq 30$, σ known | Z |
| $n \geq 30$, σ unknown | Z or t (t is safer) |
| $n < 30$, σ known | Z |
| $n < 30$, σ unknown, normal population | t with df = n-1 |
| Testing proportion, $np > 5$ and $nq > 5$ | Z |

---

## Example worked computation

**Problem:** A sample of 25 students has a mean exam score of 75 with sample standard deviation 8. Test whether the mean score differs from 72 at α = 0.05.

**Step 1:** Set hypotheses.
$H_0: \mu = 72$
$H_a: \mu \neq 72$
(Two-tailed)

**Step 2:** Set α = 0.05.

**Step 3:** Choose test statistic and critical value.
$n = 25 < 30$, σ unknown → use t-distribution with $df = 24$.
For two-tailed test, α = 0.05, $df = 24$: $t_{critical} = \pm 2.064$.

**Step 4:** Calculate test statistic.
$$t = \frac{75 - 72}{8/\sqrt{25}} = \frac{3}{1.6} = 1.875$$

**Step 5:** Decision.
$|1.875| < 2.064$, so fail to reject $H_0$.
The data do not provide sufficient evidence at the 5% significance level to conclude the mean score differs from 72.

---

## Common errors to avoid

- **Confusing p-value with probability the null is true.** The p-value is P(data | H₀), not P(H₀ | data).
- **Accepting the null instead of failing to reject.** There's no proof the null is true; you simply don't have enough evidence against it.
- **Ignoring the direction of the test.** A one-tailed test puts all rejection probability in one tail; a two-tailed test splits it.
- **Using the wrong distribution.** With small samples and unknown σ, use t, not z.
- **Forgetting degrees of freedom.** For the t-test, $df = n - 1$.
- **Running multiple tests without adjusting α.** If you run 20 tests at α = 0.05, expect about 1 false positive by chance.

