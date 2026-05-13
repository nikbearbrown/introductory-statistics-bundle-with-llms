# Pantry: Confidence Intervals

This file stores isolated concepts, definitions, formulas, and worked examples that can be re-used or remixed.

---

## Definitions and etymologies

**Confidence interval (CI):** A range of values, built from sample data, that estimates an unknown population parameter. The "confidence" refers to the long-run frequency at which such intervals (built the same way, repeatedly) contain the true parameter. Etymology: *confidence* from Latin *confidentia*, meaning trust or reliance; *interval* from Latin *intervallum*, the space between.

**Point estimate:** A single number computed from a sample to estimate a population parameter. Example: the sample mean $\bar{x}$ is a point estimate of $\mu$. A point estimate acknowledges no uncertainty; a confidence interval does.

**Margin of error (EBM, error bound for the mean):** The quantity $z^* \cdot SE$ (or $t_{df, \alpha/2} \cdot SE$ for t-intervals) that defines the radius of the interval around the point estimate. Larger sample sizes and lower confidence levels produce smaller margins of error.

**Standard error (SE):** The standard deviation of a sampling distribution. For sample means, $SE = \sigma/\sqrt{n}$ (or $s/\sqrt{n}$ when $\sigma$ is unknown). For sample proportions, $SE = \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$.

**Critical value ($z^*$ or $t_{df, \alpha/2}$):** The z-score or t-score that marks the boundary of the desired confidence region. Example: $z^* = 1.96$ for 95% confidence; $z^* = 2.576$ for 99% confidence.

**Confidence level:** The long-run proportion of confidence intervals (built by the same procedure, repeated many times) that contain the true population parameter. Common levels: 90%, 95%, 99%. Expressed as $(1 - \alpha) \times 100\%$.

**Degrees of freedom (df):** The number of independent pieces of information available to estimate a parameter. For sample standard deviation and t-intervals, $df = n - 1$ because one degree of freedom is "used up" in calculating the sample mean.

**Student's t-distribution:** A probability distribution, discovered by William Gossett in 1908 under the pen name "A Student," that has heavier tails than the standard normal and is used when (1) the population standard deviation is unknown, (2) the sample is small, and (3) the population is approximately normal. The shape depends on the degrees of freedom; at $df = \infty$, it becomes the normal distribution.

**Sample proportion ($\hat{p}$, "p-hat"):** The proportion of a sample that displays a particular characteristic. $\hat{p} = x/n$, where $x$ is the number of successes and $n$ is the sample size. It serves as a point estimate of the population proportion $p$.

---

## Key formulas

**Confidence interval for population mean, $\sigma$ known:**
$$\bar{x} \pm z^* \cdot \frac{\sigma}{\sqrt{n}}$$

**Confidence interval for population mean, $\sigma$ unknown (t-interval):**
$$\bar{x} \pm t_{df, \alpha/2} \cdot \frac{s}{\sqrt{n}}, \quad df = n - 1$$

**Confidence interval for population proportion:**
$$\hat{p} \pm z^* \sqrt{\frac{\hat{p}(1 - \hat{p})}{n}}$$
Condition for validity: $n\hat{p} \geq 5$ and $n(1-\hat{p}) \geq 5$.

**Sample size for estimating a population proportion:**
$$n = \frac{(z^*)^2 \cdot \hat{p}(1-\hat{p})}{e^2}$$
where $e$ is the desired margin of error.

**Sample size for estimating a population mean:**
$$n = \frac{(z^*)^2 \cdot \sigma^2}{e^2}$$
(If $\sigma$ is unknown, use a preliminary estimate or the most conservative value observed in a pilot study.)

---

## Critical z-values and t-values

**Common critical z-values:**
- 90% confidence: $z^* = 1.645$
- 95% confidence: $z^* = 1.96$
- 99% confidence: $z^* = 2.576$

**Selected t-values** (for two-tailed intervals):
- $df = 5$: $t_{0.025} = 2.571$ (95% CI), $t_{0.005} = 4.032$ (99% CI)
- $df = 10$: $t_{0.025} = 2.228$, $t_{0.005} = 3.169$
- $df = 20$: $t_{0.025} = 2.086$, $t_{0.005} = 2.845$
- $df = 30$: $t_{0.025} = 2.042$, $t_{0.005} = 2.750$
- $df = \infty$: $t_{0.025} = 1.96$, $t_{0.005} = 2.576$ (these match the z-values)

---

## Worked example: Complete walk-through

**Scenario:** A medical researcher measures the cholesterol levels of 16 patients randomized to a new diet program. The sample mean reduction is $\bar{x} = 18$ mg/dL with sample standard deviation $s = 12$ mg/dL. Build a 95% confidence interval for the true mean reduction.

**Solution:**

Step 1: Check conditions.
- Sample size $n = 16 < 30$, and the population SD is unknown, so use the t-distribution.
- Assume the population of cholesterol reductions is approximately normal (given by the study design).
- $df = n - 1 = 15$

Step 2: Find the critical value.
- For 95% confidence with $df = 15$: $\alpha = 0.05$, $\alpha/2 = 0.025$
- From a t-table: $t_{15, 0.025} = 2.131$

Step 3: Calculate the standard error.
$$SE = \frac{s}{\sqrt{n}} = \frac{12}{\sqrt{16}} = \frac{12}{4} = 3$$

Step 4: Calculate the margin of error.
$$EBM = t_{df, \alpha/2} \cdot SE = 2.131 \cdot 3 = 6.393 \approx 6.4$$

Step 5: Build the interval.
$$\text{CI} = \bar{x} \pm EBM = 18 \pm 6.4 = (11.6, 24.4)$$

**Interpretation:** We are 95% confident that the true mean cholesterol reduction from the diet program is between 11.6 and 24.4 mg/dL.

**Procedural meaning:** If this study were repeated 100 times with 100 new random samples of 16 patients each, approximately 95 of the resulting confidence intervals would contain the true population mean reduction.

---

## Common errors and how to avoid them

**Error 1: Confusing the confidence level with the probability that the parameter is in the interval.**
- Wrong: "There's a 95% chance the true mean is in this interval."
- Right: "95% of confidence intervals built this way contain the true mean."

**Error 2: Using z when you should use t.**
- Wrong: Using $z^* = 1.96$ with a sample of $n = 15$ when $\sigma$ is unknown.
- Right: Use $t_{14, 0.025} = 2.145$ (the sample SD is an estimate, and the t-distribution accounts for that extra uncertainty).

**Error 3: Forgetting to check the condition for normal approximation with proportions.**
- Wrong: Building a confidence interval for a proportion when $n\hat{p} = 3$ and $n(1-\hat{p}) = 2$.
- Right: Check that $n\hat{p} \geq 5$ and $n(1-\hat{p}) \geq 5$ before using the normal approximation.

**Error 4: Assuming the interval is always symmetric around the point estimate.**
- Nuance: For z- and t-intervals with means, and for proportions, yes, the interval is symmetric. But other methods (like the Wilson score interval for proportions) produce asymmetric intervals. Specify your method.

**Error 5: Calculating sample size without specifying what you're estimating.**
- Wrong: "How big should the sample be?" (Big for what? Mean? Proportion? How much precision do you need?)
- Right: "How big a sample do I need to estimate the true proportion within ±3%, at 95% confidence?" Then use the formula $n = \frac{(z^*)^2 \cdot \hat{p}(1-\hat{p})}{e^2}$.

---

## Relationship between confidence, precision, and sample size

**Concept: The three-way trade-off**

When you design a study, you can control two of these three; the third follows from the math:

1. **Confidence level** (how often the procedure works): Higher confidence (95% vs. 90%) → wider intervals, larger $z^*$.
2. **Margin of error** (interval width): Smaller margin of error → more precision, requires larger sample size.
3. **Sample size**: Larger sample → smaller standard error, narrower intervals, more precision.

**Example: Estimating a proportion at various levels**

Suppose you want to estimate the proportion of a population with a given trait. You've done a pilot and estimate $\hat{p} = 0.3$.

| Confidence | Margin of error | Required $n$ |
|---|---|---|
| 90% | ±5% | $n = \frac{(1.645)^2 \cdot 0.3 \cdot 0.7}{(0.05)^2} = 228$ |
| 95% | ±5% | $n = \frac{(1.96)^2 \cdot 0.3 \cdot 0.7}{(0.05)^2} = 323$ |
| 99% | ±5% | $n = \frac{(2.576)^2 \cdot 0.3 \cdot 0.7}{(0.05)^2} = 559$ |
| 95% | ±3% | $n = \frac{(1.96)^2 \cdot 0.3 \cdot 0.7}{(0.03)^2} = 897$ |

Observations:
- Higher confidence (99% vs. 95%) requires a larger sample for the same precision.
- Higher precision (±3% vs. ±5%) requires a much larger sample for the same confidence.
- Halving the margin of error (from ±5% to ±2.5%) would require 4 times the sample size.

---

## Why the sample size formula has $(z^*)^2$ but margin of error has $z^*$

The margin of error formula is: $EBM = z^* \cdot \frac{\sigma}{\sqrt{n}}$

If you want to halve the margin of error, you have two levers:
1. Increase $z^*$ (higher confidence, but that makes the margin *wider*, not narrower).
2. Increase $n$ (larger sample, smaller standard error).

Setting $e = \frac{z^* \sigma}{2\sqrt{n}}$ (half of the original margin) and solving for $n$:

$$e = \frac{z^* \sigma}{2\sqrt{n}}$$
$$2e\sqrt{n} = z^* \sigma$$
$$\sqrt{n} = \frac{z^* \sigma}{2e}$$
$$n = \frac{(z^* \sigma)^2}{4e^2}$$

If the original sample size was $n_0 = \frac{(z^* \sigma)^2}{e^2}$, then the new size $n = \frac{(z^* \sigma)^2}{4e^2} = 4 \cdot n_0$.

The $(z^*)^2$ term arises because you're squaring the critical value when you rearrange to solve for $n$.

---

## When the normal distribution is a good enough approximation

**For sample means:** The Central Limit Theorem guarantees that $\bar{x}$ is approximately normal for large $n$, even if the population is not normal. "Large" typically means $n \geq 30$. If the population itself is normal, the sample mean is exactly normal (not just approximately) for any $n$. This is why you can use the z-distribution with confidence for large samples and the t-distribution for any $n$ when $\sigma$ is unknown.

**For sample proportions:** The binomial distribution (which governs the count of successes) can be approximated by the normal distribution when $np \geq 5$ and $n(1-p) \geq 5$. The further $p$ is from 0.5, the larger $n$ needs to be. Example: if $p = 0.01$, you'd need $n \geq 500$ to have $np = 5$.

---

## The conceptual core

A confidence interval is an honest admission: "I have a single sample, from which I calculated a point estimate. The true parameter is unknown. But if I build this range in this way, and I repeat this procedure many times with many samples, the range will capture the true parameter a certain percentage of the time."

The percentage is the confidence level. The range is the interval. The width depends on your sample size and your desired confidence. You choose the confidence first. The math then tells you the width.

The key insight: once the interval is built, the parameter is either in it or it's not. Probability no longer applies. The 95% confidence refers to the procedure, not to the outcome.
