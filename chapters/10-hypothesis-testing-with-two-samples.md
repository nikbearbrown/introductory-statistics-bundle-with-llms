# Chapter 10 — Hypothesis Testing with Two Samples

## Three title options

1. **Comparing Two Groups: When one sample isn't enough to answer the question**
2. **Does This Difference Matter? Testing whether two groups really are different**
3. **Two Means, Two Proportions: The machinery for comparing samples and deciding what's real**

---

## TL;DR

When you have two groups—a treatment and a control, two manufacturing lines, two cities—you need to know whether a difference you observe in their sample statistics reflects a real difference in the populations they come from or just sampling noise. We extend the one-sample hypothesis test machinery from Chapter 9 to this case. The key insight: the difference between two sample means (or two sample proportions) itself follows a distribution. We can standardize it, compare it to a critical value, and ask a precise question: *if these two populations were really identical, how surprising would this observed difference be?*

---

## Cold open: The moment the comparison begins

It is 2024. A pharmaceutical company is running a Phase III clinical trial for a new anxiety medication. Half the enrolled patients (160 people) receive the drug. Half (160 people) receive an inert placebo. Neither the patients nor the clinicians administering the study know which is which—a design called **blinding** that protects against expectation bias, where believing you're getting medicine can make you feel better whether you're actually getting medicine or not.

After eight weeks, the researchers measure anxiety symptom reduction using a validated questionnaire. The drug group shows a mean reduction of 12.4 points on the scale, with standard deviation 4.8. The placebo group shows a mean reduction of 10.1 points, with standard deviation 4.2.

Difference: 12.4 − 10.1 = 2.3 points.

The company's medical team looks at that 2.3-point gap and asks: *Is this a real effect, or did we just happen to recruit slightly more anxious people into the placebo group by chance?*

That question—and the mathematical machinery to answer it—is what this chapter teaches. We'll see how to test whether two groups are genuinely different, when the difference is large enough to matter, and what assumptions we need to make along the way. We'll test differences in means (the anxiety trial above) and differences in proportions (does one city have a higher unemployment rate than another?), and we'll work through paired data (before-and-after measurements on the same person, where the pairing itself reduces noise).

### Learning objectives

By the end of this chapter you will be able to:

- **Construct and interpret** hypothesis tests for the difference between two independent population means (using both pooled and unpooled variance).
- **Conduct** a paired (matched-pairs) t-test for dependent samples.
- **Test** whether two population proportions differ significantly.
- **Calculate** the standard error of a difference, understand why it combines the two sample variances, and interpret what it measures.
- **Recognize** when to use pooled vs. unpooled variance, when samples are paired vs. independent, and how sample size affects the choice of test.
- **Interpret** p-values, effect sizes (Cohen's *d*), and confidence intervals in the context of two-sample comparisons.

### Prerequisites

Chapter 9 (Hypothesis Testing with One Sample), Chapter 7 (The Central Limit Theorem), Chapter 2 (Descriptive Statistics). You should be fluent with the null and alternative hypotheses, test statistics, p-values, and the t-distribution from Chapter 9. You should understand the standard error and the central limit theorem.

### Why this chapter matters

Medicine, policy, and product development all work by comparison. Does this treatment work better than the alternative? Does this group earn more than that group? Does this manufacturing process produce fewer defects? The question is almost never about a single sample in isolation. It is about whether two things differ. This chapter gives you the framework to answer that question rigorously, with an honest assessment of when the difference is large enough to be convincing.

---

## Concept 1: Independent Samples and the Difference of Means

**Cold open: Two manufacturing plants, one question**

A company manufactures automotive brake pads at two plants: one in the Midwest, one on the West Coast. Both are supposed to produce pads that last an average of 50,000 miles. The quality team samples 35 pads from the Midwest plant and tests them to failure. Mean lifespan: 49,200 miles, standard deviation 3,100 miles. They sample 42 pads from the West Coast plant. Mean lifespan: 50,800 miles, standard deviation 2,900 miles.

The Midwest pads lasted 1,600 miles less, on average. Is the Midwest plant drifting out of specification? Or did the sample just happen to catch Midwest pads on an off day?

This is the structure of an **independent two-sample problem**. Two groups. No natural pairing between them (a specific pad from the Midwest is not paired with a specific pad from the West Coast). The question: do the populations they come from have the same mean?

### From one sample to two: The difference as a random variable

In Chapter 9, you tested whether a single sample mean came from a hypothesized population. The test statistic was:

$$t = \frac{\bar{x} - \mu_0}{\text{SE}(\bar{x})} = \frac{\bar{x} - \mu_0}{s/\sqrt{n}}$$

Now you have two sample means. The central limit theorem tells us each one is approximately normally distributed (or t-distributed, when we estimate the population standard deviation). But we want to test whether the two *populations* have the same mean. So we construct a new random variable: the difference between the two sample means.

$$\bar{x}_1 - \bar{x}_2$$

This difference itself has a distribution. The central limit theorem applies to it: if you drew many pairs of samples from the two populations and computed the difference each time, those differences would be normally distributed (or approximately so). The mean of that distribution is $\mu_1 - \mu_2$, the true difference between the population means. The standard deviation of that distribution is the **standard error of the difference**:

$$\text{SE}(\bar{x}_1 - \bar{x}_2) = \sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}$$

This is the key formula. Study it. It says: the variance of a difference is the sum of the variances. If one group is very variable and the other is tight, the difference between them is more variable. If both are small samples, the difference is more variable.

The test statistic, using the t-distribution (because we estimate the standard deviations from the samples), is:

$$t = \frac{(\bar{x}_1 - \bar{x}_2) - \delta_0}{\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}}$$

where $\delta_0$ (delta-nought) is the hypothesized difference between the population means. Usually $\delta_0 = 0$: we're testing whether the two populations have the *same* mean. But $\delta_0$ can be nonzero if the question is whether one population's mean exceeds the other's by a specific amount (e.g., "Is the new machine at least 5% faster?").

The degrees of freedom for this test is approximately $n_1 + n_2 - 2$ when both sample sizes are large (30 or more). When sample sizes are smaller or unequal, a more complicated formula applies (the Welch-Satterthwaite equation—see the pantry for details).

### A worked example: Testing whether two manufacturing plants differ

Back to the brake pads. 

**Setup:** 
- Midwest (Group 1): $\bar{x}_1 = 49,200$ miles, $s_1 = 3,100$ miles, $n_1 = 35$
- West Coast (Group 2): $\bar{x}_2 = 50,800$ miles, $s_2 = 2,900$ miles, $n_2 = 42$
- Hypothesized difference: $\delta_0 = 0$ (we're testing whether they're equal)
- Significance level: $\alpha = 0.05$
- This is a two-tailed test: $H_0: \mu_1 = \mu_2$ vs. $H_a: \mu_1 \neq \mu_2$

**Step 1: Compute the standard error.**

$$\text{SE} = \sqrt{\frac{(3,100)^2}{35} + \frac{(2,900)^2}{42}} = \sqrt{\frac{9,610,000}{35} + \frac{8,410,000}{42}} = \sqrt{274,571 + 200,238} = \sqrt{474,809} \approx 689 \text{ miles}$$

**Step 2: Compute the test statistic.**

$$t = \frac{(49,200 - 50,800) - 0}{689} = \frac{-1,600}{689} \approx -2.32$$

**Step 3: Find the p-value.**

Degrees of freedom: $df = 35 + 42 - 2 = 75$. This is a two-tailed test. We look up $|t| = 2.32$ in the t-distribution with 75 degrees of freedom. The area in both tails at $t = 2.32$ is approximately 0.023.

**Step 4: Make a decision.**

Since $p = 0.023 < 0.05$, we reject $H_0$. The Midwest plant's brake pads do last significantly less long, on average, than the West Coast plant's pads. The difference of 1,600 miles is unlikely to be due to chance sampling.

### Trade-off: Unpooled vs. pooled variance

I showed you the **unpooled variance** test above, also called the **Aspin-Welch test**. It does not assume the two population standard deviations are equal. It's the safer choice when you don't know whether $\sigma_1 = \sigma_2$.

But sometimes you have prior information suggesting the two population standard deviations are equal—or your data show very similar sample standard deviations, and assuming equality gives you more power (a better chance of detecting a real difference if one exists). In that case, you can use the **pooled variance** approach.

The pooled variance is a weighted average of the two sample variances:

$$s_p^2 = \frac{(n_1 - 1)s_1^2 + (n_2 - 1)s_2^2}{n_1 + n_2 - 2}$$

The test statistic becomes:

$$t = \frac{(\bar{x}_1 - \bar{x}_2) - \delta_0}}{s_p\sqrt{\frac{1}{n_1} + \frac{1}{n_2}}}$$

The degrees of freedom is exactly $n_1 + n_2 - 2$, with no complicated adjustment.

**When to use pooled:** If a preliminary test (Levene's test, beyond this course) or domain knowledge strongly suggests equal population variances, pooling gives slightly more power. But many statisticians recommend unpooled as the default—it's safer.

**When to use unpooled:** Almost always, unless you have good reason to assume equal variances. The unpooled approach pays a small price in power to avoid the cost of a false assumption.

### Common misconceptions

**"The larger sample size always wins."** Not necessarily. If the larger sample is also much more variable, the standard error can be larger. It's the ratio of variance to sample size in each group that matters.

**"If two sample means look different, the populations must be different."** No. Random sampling can produce differences in sample means even when the populations are identical. The hypothesis test quantifies how surprising the observed difference would be under that assumption.

**"Pooled variance is always better because it gives more power."** Only if the assumption of equal population variances is true. If it's false, pooling can give misleading results. The unpooled approach is more conservative and requires fewer assumptions.

---

## Concept 2: Paired (Matched-Pairs) Samples

**Cold open: Before and after—a single person's story, twice measured**

A physical therapist has 12 patients recovering from knee surgery. Before starting a new rehabilitation protocol, each patient performs a standard test: how far can you walk without pain? The result (in meters) is recorded. Then they follow the protocol for six weeks. They perform the same test again. Walk distance after: recorded.

The data looks like this (before, after):

| Patient | Before | After | Difference |
|---------|--------|-------|------------|
| 1       | 150    | 240   | +90        |
| 2       | 120    | 180   | +60        |
| 3       | 180    | 200   | +20        |
| 4       | 100    | 190   | +90        |
| 5       | 140    | 170   | +30        |
| 6       | 160    | 260   | +100       |

And so on for all 12 patients.

This is a **paired** or **matched-pairs** design. Each observation in the "before" group has a natural partner: the same person, measured after. The pairing means the two measurements are not independent—they come from the same subject.

### Why pairing reduces noise: The elegance of one-sample thinking applied to pairs

Here's the key insight: In a paired design, you don't compare two independent groups. Instead, you compute the difference for each pair, and test whether those differences are centered at zero.

For each patient, compute $d_i = \text{after} - \text{before}$. Now you have a single sample of differences: {+90, +60, +20, +90, +30, +100, ...}. Test whether the mean of these differences is zero.

$$t = \frac{\bar{d} - 0}{s_d / \sqrt{n}}$$

where $\bar{d}$ is the mean difference and $s_d$ is the standard deviation of the differences. This is a one-sample t-test applied to the differences. The degrees of freedom is $n - 1$, where $n$ is the number of *pairs*, not observations.

Why does pairing help? Because variability *between people* (some people are naturally stronger than others) gets subtracted out. You're looking at the change *within* each person, which is less noisy than comparing "strong people in the after group" to "weak people in the before group."

### A worked example: Did the rehabilitation protocol help?

Data from the 12 patients. Differences (after − before, in meters):

+90, +60, +20, +90, +30, +100, −10, +50, +80, +40, +70, +60

**Step 1: Compute the mean difference.**

$$\bar{d} = \frac{90 + 60 + 20 + 90 + 30 + 100 - 10 + 50 + 80 + 40 + 70 + 60}{12} = \frac{760}{12} \approx 63.3 \text{ meters}$$

**Step 2: Compute the standard deviation of the differences.**

Using the sample standard deviation formula on the 12 differences:

$$s_d \approx 38.2 \text{ meters}$$

**Step 3: Compute the standard error and test statistic.**

$$\text{SE}(\bar{d}) = \frac{s_d}{\sqrt{n}} = \frac{38.2}{\sqrt{12}} \approx 11.0 \text{ meters}$$

$$t = \frac{63.3}{11.0} \approx 5.75$$

**Step 4: Find the p-value.**

Degrees of freedom: $df = 12 - 1 = 11$. A t-statistic of 5.75 with 11 degrees of freedom corresponds to a p-value far below 0.001 (essentially, $p < 0.001$).

**Step 5: Make a decision.**

With $p < 0.001 < 0.05$, we reject the null hypothesis that $\mu_d = 0$. The rehabilitation protocol significantly increased walking distance. On average, patients improved by about 63 meters, and this improvement is far too large to be explained by sampling noise.

### When pairing is possible—and when it isn't

**Paired designs work when:**
- You measure the same person/object before and after treatment.
- You match subjects in pairs by some criterion (height, baseline health, age) to make them comparable, then randomly assign one to treatment and one to control.
- You use identical twins or sibling pairs, assigning different treatments to each member.
- You measure the same location at two points in time.

**Independent samples are necessary when:**
- The groups are fundamentally different (men vs. women, two different companies, two different manufacturing plants).
- Subjects cannot be paired (you don't have the same people measured twice, or natural matches).

The paired test is more powerful (better at detecting a real effect) when pairing is possible, because it reduces variability. But you *must* have pairs. If you don't, pairing damages your inference.

### Common misconceptions

**"Paired designs are always better."** Only when the pairing actually reduces noise. If the pairing is arbitrary, you waste information.

**"I can pretend my data are paired if I sort them."** No. Pairing must come from the study design (same person twice, or matched pairs created before you knew the outcomes). Sorting the data and matching arbitrarily introduces bias.

**"The differences have to be positive (improvement) for the test to work."** No. The test is symmetric. Negative differences (the after score is lower) are fine. The question is whether the mean difference is zero, not whether it's positive.

---

## Concept 3: Two Proportions

**Cold open: Two cities, one question about unemployment**

In May 2024, the unemployment rate in City A (a large Midwestern manufacturing hub) is estimated from a survey. Surveyors randomly contact 400 households. In 48 of them, someone is currently seeking work. Sample proportion: $\hat{p}_A = 48/400 = 0.12$ (12%).

City B (a tech hub on the coast) surveys 450 households. In 45, someone is seeking work. Sample proportion: $\hat{p}_B = 45/450 = 0.10$ (10%).

Difference: 12% − 10% = 2 percentage points.

The question: Is City A's unemployment truly higher, or did this survey just happen to catch slightly more unemployed people in City A by chance?

### The structure of the two-proportion test

Like the two-mean case, we construct a test statistic based on the difference of the two sample proportions. The central limit theorem tells us this difference follows an approximately normal distribution.

The test statistic is:

$$Z = \frac{(\hat{p}_1 - \hat{p}_2) - \delta_0}{\sqrt{p_c(1 - p_c)\left(\frac{1}{n_1} + \frac{1}{n_2}\right)}}$$

where $p_c$ is the **pooled proportion** (combining successes and failures from both samples):

$$p_c = \frac{x_1 + x_2}{n_1 + n_2}$$

$x_1$ and $x_2$ are the number of "successes" (unemployed people, defective items, recovered patients) in each group. $\delta_0$ is usually 0 (testing whether the two population proportions are equal).

Note: This is a *z*-test, not a *t*-test, because proportions are bounded between 0 and 1 and have a known relationship between mean and variance (for a binomial: $\sigma^2 = np(1-p)$).

### A worked example: Are the cities' unemployment rates different?

**Setup:**
- City A: $\hat{p}_1 = 48/400 = 0.12$, $n_1 = 400$
- City B: $\hat{p}_2 = 45/450 = 0.10$, $n_2 = 450$
- Hypothesized difference: $\delta_0 = 0$
- Significance level: $\alpha = 0.05$
- Two-tailed test: $H_0: p_1 = p_2$ vs. $H_a: p_1 \neq p_2$

**Step 1: Compute the pooled proportion.**

$$p_c = \frac{48 + 45}{400 + 450} = \frac{93}{850} \approx 0.1094$$

**Step 2: Compute the standard error.**

$$\text{SE} = \sqrt{0.1094 \cdot (1 - 0.1094) \cdot \left(\frac{1}{400} + \frac{1}{450}\right)} = \sqrt{0.1094 \cdot 0.8906 \cdot (0.0025 + 0.00222)}$$

$$= \sqrt{0.0974 \cdot 0.00472} = \sqrt{0.000460} \approx 0.0214$$

**Step 3: Compute the test statistic.**

$$Z = \frac{(0.12 - 0.10) - 0}{0.0214} = \frac{0.02}{0.0214} \approx 0.93$$

**Step 4: Find the p-value.**

A z-statistic of 0.93 in a two-tailed test corresponds to a p-value of approximately 0.35.

**Step 5: Make a decision.**

With $p = 0.35 > 0.05$, we fail to reject $H_0$. The data do not provide sufficient evidence that the two cities' unemployment rates differ. The observed 2-percentage-point difference can reasonably be explained by sampling variation.

### Conditions for the two-proportion test

The two-proportion z-test requires:

1. Both samples are random and independent.
2. The number of "successes" and "failures" in each sample is at least 5 (some sources say 10). This ensures the normal approximation is accurate.

If either condition is violated, use an exact binomial test or a simulation-based approach (beyond this course).

### Common misconceptions

**"A difference in sample proportions proves a difference in population proportions."** No. Sample proportions vary due to random sampling. The hypothesis test quantifies whether the observed difference is surprising under the null hypothesis.

**"I should use the unpooled version if the sample proportions are very different."** No. The pooled proportion is used for the test under $H_0$ (assuming the populations have the same proportion). Use the unpooled standard error only if you're constructing a confidence interval, where you estimate each population proportion separately.

**"Smaller sample sizes always give larger p-values."** Not necessarily. A smaller sample size increases the standard error, which can increase the p-value. But if the true effect is large, even a small sample can produce a small p-value.

---

## Integration: Three Tests, One Logic

The three tests in this chapter—independent means (unpooled and pooled), paired means, and two proportions—follow the same four-step logic from Chapter 9:

1. **State the hypotheses.** $H_0: \text{populations are equal}$ vs. $H_a: \text{populations differ}$ (or one-sided versions).
2. **Compute the test statistic.** Standardize the observed difference by dividing by its standard error.
3. **Find the p-value.** Look up the test statistic in the appropriate distribution (t for means, z for proportions).
4. **Make a decision.** Reject $H_0$ if $p < \alpha$; otherwise, fail to reject.

The choice of which test to use depends on three questions:

- *Are the samples independent or paired?* Paired data use one-sample logic on differences. Independent data use the two-sample machinery.
- *Are you testing means or proportions?* Means use t-tests (with estimated standard deviation). Proportions use z-tests (with known relationship between mean and variance).
- *Do you assume equal population variances (for means)?* Unpooled is safer. Pooled gives more power if the assumption holds.

### What p-values actually tell us (and don't tell us)

A p-value of 0.03 means: *If the null hypothesis were true (the two populations are identical), there would be a 3% chance of observing a difference this large or larger, purely by sampling variation.*

It does **not** mean: the alternative hypothesis is 97% likely, or the null hypothesis has a 3% chance of being true, or the effect is practically important.

A small p-value (below $\alpha$, usually 0.05) says the data are surprising under $H_0$. It suggests $H_0$ is unlikely. But it doesn't prove $H_0$ is false—only that the evidence is stronger than we set as our threshold.

### Effect size: Is the difference meaningful?

A statistically significant difference (small p-value) is not the same as a practically meaningful difference. A huge sample can produce a tiny p-value for a trivial effect.

**Cohen's *d*** measures effect size—the magnitude of the difference relative to the standard deviation:

$$d = \frac{\bar{x}_1 - \bar{x}_2}{s_p}$$

where $s_p$ is the pooled standard deviation.

Cohen's standards: $d = 0.2$ is small, $d = 0.5$ is medium, $d = 0.8$ is large.

In the brake pad example, let's compute $d$:

$$s_p = \sqrt{\frac{(35-1)(3,100)^2 + (42-1)(2,900)^2}{35 + 42 - 2}} \approx 3,000$$

$$d = \frac{49,200 - 50,800}{3,000} = \frac{-1,600}{3,000} \approx -0.53$$

A Cohen's $d$ of −0.53 is medium. The Midwest plant's shortfall is not huge, but it's large enough to matter for customer satisfaction and warranty costs.

---

## Exercises

### Warm-up exercises

**10.1.** A hospital tests a new blood pressure medication on 40 patients. The control group (standard medication) shows a mean systolic BP of 142 mmHg with $s = 18$. The new medication group shows 138 mmHg with $s = 16$. Is the new medication significantly better at the 0.05 level? (Assume independent samples, unpooled variance.)

**10.2.** Define the difference between independent samples and paired samples. Give an example of each.

**10.3.** In a two-proportion test, City X surveys 200 residents and finds 30 own electric vehicles. City Y surveys 250 residents and finds 35 own EVs. Compute the pooled proportion.

### Application exercises

**10.4.** A company compares two customer service training programs. Program A (25 employees) yields a mean satisfaction score of 78 with $s = 8.5$. Program B (28 employees) yields 82 with $s = 7.2$. Test at $\alpha = 0.05$ whether the programs differ. Compute the standard error, the test statistic, and the approximate p-value.

**10.5.** Ten athletes perform a vertical jump test before and after a new strength-training program. The differences (after − before, in inches) are: 2.1, 3.5, 1.2, 4.1, 0.8, 2.9, 3.3, 1.6, 2.4, 3.2. Test at $\alpha = 0.05$ whether the training program significantly improves vertical jump. (Compute $\bar{d}$ and $s_d$, then the test statistic.)

**10.6.** Two manufacturers of smartphone screens report defect rates. Manufacturer A inspects 500 screens and finds 15 defective. Manufacturer B inspects 600 screens and finds 12 defective. Test at $\alpha = 0.05$ whether the defect rates differ.

### Synthesis and challenge

**10.7.** Explain why the standard error of the difference of two means is $\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}$ and not just $\sqrt{\frac{s_1^2 + s_2^2}{2}}$. (Hint: think about what happens when one sample is much larger than the other.)

**10.8.** A study compares weight loss (in pounds) after 12 weeks on diet A (30 people, mean 12 lbs, $s = 4$) vs. diet B (35 people, mean 10 lbs, $s = 5$). 
- Compute the unpooled test statistic and approximate p-value.
- Compute Cohen's *d* using the pooled standard deviation.
- Interpret both results in plain language.

---

## Chapter summary

Two-sample hypothesis tests extend the machinery from Chapter 9 to answer comparative questions: Do these two groups differ? The test statistic is built by standardizing the observed difference (in means or proportions) by its standard error.

**Independent means**: Use the t-distribution with the unpooled standard error unless you have strong prior reason to assume equal population variances. Unpooled is the safer default.

**Paired means**: Compute differences for each pair, then apply the one-sample t-test to the differences. This reduces noise from between-subject variability.

**Two proportions**: Use the z-distribution with the pooled proportion in the standard error formula.

In all cases, the p-value answers the same question: *If the null hypothesis (populations are equal) were true, how surprising would this observed difference be?* A small p-value suggests the null hypothesis is unlikely. But always pair the p-value with an effect size (Cohen's *d* for means) to know whether the difference is not just statistically significant, but practically meaningful.

---

## Connections forward

Chapter 11 generalizes the two-sample t-test to many groups (ANOVA), which tests whether three or more population means are equal. Chapter 12 extends the chi-square test to two-way tables, comparing proportions across multiple categories. Regression (Chapter 13) tests whether a predictor's coefficient is nonzero, using a two-sample test on the coefficient itself.

---

## What would change my mind

If a chapter on Bayesian two-sample inference were added (treating both the null and alternative hypotheses as probability distributions, updating based on data), I would need to revisit how the p-value and effect size relate to posterior probability and credible intervals.

## Still puzzling

I don't fully understand why many textbooks present the pooled-variance test first as "the standard method," when the unpooled (Welch) approach is more robust and doesn't require an assumption about equal population variances. The historical answer involves power: when variances truly are equal, pooling is slightly more powerful. But in practice, when we don't know the variances, this seems a small gain for a fragile assumption.

---

## Tags

two-sample hypothesis testing, independent samples, paired samples, t-test, z-test, standard error, effect size, Cohen's d, pooled variance, clinical trials, comparative inference

---

## LLM Exercise — Chapter 10: Hypothesis Testing with Two Samples (Analyze One Dataset Project)

**Project:** Analyze One Real Dataset.
**What you're building this chapter:** a two-sample comparison test.
**Tool:** **Claude Code** + **Claude Project**.

---

**The Prompt:**

```
Chapter 10 of my Analyze-One-Dataset project. Chapter 10 covered:
two independent samples (compare two distinct groups) → two-sample
t-test for means, two-proportion z-test for proportions; two paired
samples (same subjects measured twice, or matched pairs) → paired
t-test; the pooled vs. unpooled variance choice (Welch's t-test is
the safer default — doesn't assume equal variances); assumption
checking (independence within and between samples; approximate
normality OR large n).

Write the brief's "Two-Sample Comparison" section in 500-800 words.

1. **Identify a meaningful comparison.** Two groups in your data
   where the comparison answers a real question. Examples:
   - Two demographic groups (male/female; control/treatment).
   - Two time periods (pre/post intervention; weekday/weekend).
   - Two categories of a categorical variable, on some
     quantitative outcome.

2. **State the hypotheses.**
   - H₀: μ₁ = μ₂ (or p₁ = p₂) — no difference between groups.
   - H_a: μ₁ ≠ μ₂ (two-sided default, unless theory dictates
     direction).

3. **Choose the test.**
   - Independent two-sample t-test (Welch's preferred): two
     distinct groups.
   - Paired t-test: same subjects measured twice.
   - Two-proportion z-test: comparing proportions.

4. **Check assumptions.**
   - Independence: were the two samples drawn independently?
   - Normality OR large n: if both groups have n > 30, CLT covers
     us.

5. **Run the test.**
   - For independent t-test: `scipy.stats.ttest_ind(group1,
     group2, equal_var=False)` for Welch's.
   - For paired t-test: `scipy.stats.ttest_rel(before, after)`.
   - For two-proportion z-test: build it from formulas or use
     `statsmodels.stats.proportion.proportions_ztest`.

6. **Compute the effect size.** A significant test result with a
   tiny effect size is statistically detectable but practically
   meaningless.
   - For means: Cohen's d = (x̄₁ − x̄₂) / pooled SD.
   - For proportions: difference in proportions; risk ratio;
     odds ratio.

7. **Interpret.** Both the p-value AND the effect size matter.
   The p-value says "the difference exists"; the effect size says
   "by how much."

End with: based on this comparison, does your big question (from
Ch 1) become clearer? What does the comparison say about your
dataset's central story?
```

---

**What this produces:** A 500-800 word section with a complete two-sample test + effect size + interpretation. The effect-size discipline is what distinguishes useful inference from p-value-hunting.

**How to adapt this prompt:**

- *For your own project:* The choice of comparison shapes the story. Pick one that's defensible AND interesting.
- *For ChatGPT / Gemini:* Works as written.
- *For Claude Code:* The right tool. Effect size doesn't have a one-liner — compute it explicitly.
- *For a Claude Project:* Append.

**Connection to previous chapters:** Ch 8's CI logic generalizes — the two-sample test is equivalent to a CI for the difference of means.

**Preview of next chapter:** Chapter 11 covers chi-square tests for categorical relationships. You'll formally test independence between two categorical variables in your dataset (extending Ch 3's contingency-table work).


---

## 🕰️ AI Wayback Machine

**Frank Wilcoxon** was chemist whose rank-based two-sample test (1945) became one of the most-used nonparametric techniques in modern statistics.

**Run this:**

```
Who is Frank Wilcoxon, and how does their work connect to two-sample tests we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Frank Wilcoxon"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Frank Wilcoxon's framework to a small dataset you actually have.
- Add a constraint: "Answer including criticisms or limits of Frank Wilcoxon's framework."

What changes? What gets better? What gets worse?
