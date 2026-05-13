# Bookmap — Chapter 10: Hypothesis Testing with Two Samples

## Source analysis

This chapter consolidates seven OpenStax modules covering independent and paired two-sample tests for means and proportions. The source material is pedagogically sound but abstract in opening and example selection. The rewrite anchors each concept in a concrete, grounded scenario (pharmaceutical trial, manufacturing quality, rehabilitation outcomes, unemployment surveys) before building the machinery.

---

## Concept 1: Independent Samples and the Difference of Means

**Source module:** m55671 (Aspin-Welch t-test for unknown, unequal population standard deviations)

**What the source teaches:** The test statistic for comparing two independent means when population SDs are unknown and possibly unequal. Central limit theorem ensures the difference of means is normally distributed. Degrees of freedom calculation via Welch-Satterthwaite. The pooled version (m64421) is also covered.

**How the rewrite operates:** Opens with a cold scene—two manufacturing plants with different quality outcomes. Unpacks what "independent samples" means (no natural pairing). Teaches the standard error of a difference from first principles: why variances add, not average. Walks through the brake pad example step by step (SE calculation, test statistic, p-value lookup, decision). Names the trade-off between unpooled (safer, fewer assumptions) and pooled (more power if equal variance assumption holds). Emphasizes unpooled as the default in modern practice.

**Key shift in voice:** The source presents the test statistic formula first, then example. The rewrite asks the question first ("Is the Midwest plant drifting?"), then derives why we need the machinery we're about to build.

---

## Concept 2: Paired (Matched-Pairs) Samples

**Source module:** m55674 (Hypothesis testing for matched or paired samples)

**What the source teaches:** Paired samples reduce noise from between-subject variability. Differences are calculated. A one-sample t-test is applied to the differences (not a two-sample test). The source includes two examples: employee training (before/after performance) and hypnotism for pain reduction.

**How the rewrite operates:** Opens mid-scene with a physical therapist and 12 patients, each measured before and after. Names the elegance of paired design: between-person variability is subtracted out. Teaches why $\text{SE}(\bar{d}) = s_d / \sqrt{n}$ is smaller than the independent-samples SE would be. Walks through the worked example in detail. Clarifies when pairing is possible vs. when it damages inference (arbitrary pairing is worse than independence). Names the common mistake: thinking data must show improvement (positive differences) for the test to work.

**Key shift in voice:** The source presents paired tests as a variant of two-sample testing. The rewrite treats it as a return to one-sample logic applied to a difference, making the connection to Chapter 9 explicit.

---

## Concept 3: Two Proportions

**Source module:** m55672 (Hypothesis testing for two population proportions)

**What the source teaches:** The test statistic for comparing proportions from two independent samples. Uses the pooled proportion in the standard error. Conditions: both samples random and independent, at least 5 successes and 5 failures in each group. Includes a bank default-rate example.

**How the rewrite operates:** Opens with unemployment surveys in two cities (a current, relatable question). Builds the test statistic from the idea that differences in proportions also follow a normal distribution. Explains why proportions use z-tests (bounded between 0 and 1, known relationship between mean and variance) rather than t-tests. Clarifies the distinction: pooled proportion for hypothesis testing (assuming $H_0$ is true), unpooled for confidence intervals. Walks through the cities example, showing why a 2-percentage-point difference is not surprising.

**Key shift in voice:** The source jumps to the formula. The rewrite anchors in the question and the intuition (why differences are normally distributed) before the formula.

---

## Concept 4: Effect Size (Cohen's d)

**Source module:** m64420 (Cohen's d as a measure of effect size)

**What the source teaches:** Cohen's d as the difference of means divided by pooled standard deviation. Standards: 0.2 small, 0.5 medium, 0.8 large. Important note: d does not provide confidence bounds like hypothesis tests do.

**How the rewrite operates:** Integrated into the integration section, not a separate concept. Explains why a small p-value (statistical significance) is not the same as a large effect size (practical importance). Computes d for the brake pad example to show that the difference, while statistically significant, is medium in magnitude—large enough to matter but not huge. Emphasizes always reporting p-value and effect size together.

**Key shift in voice:** The source presents d as a technical calculation. The rewrite teaches d as the bridge between "is the difference real?" (p-value) and "is it big enough to matter?" (effect size).

---

## Bridge: Integration and the Logic Chain

All three tests follow the same four-step procedure from Chapter 9. The choice of test depends on three branches:
1. Independent or paired?
2. Means or proportions?
3. (For means) Equal or unequal population variances?

This is taught in the integration section, not at the start. The reader has worked through three examples and now sees the common structure.

---

## Ideas harvest for writing

### Openings and cold opens

- **Pharmaceutical trial (Chapter 10 opener):** Specific numbers (160 patients per arm), concrete question (is 12.4 vs. 10.1 point reduction real?), blinding design mentioned (raises the question without distracting). This works as a scene-anchor.
- **Manufacturing quality (Concept 1):** Two plants, same design spec, different outcomes. Question is immediate and economically motivated.
- **Physical therapy (Concept 2):** Before-and-after on the same person. The table format showing individuals and their improvements is more compelling than abstract notation.
- **Unemployment survey (Concept 3):** Two cities, political and economic stakes. The word "unemployment" carries weight.

### Specification moves

The chapter does this work:
- **Paired** (from Latin *par*, equal): data where each observation has a natural mate. Teaches the etymology, then the mechanism (subtraction of between-subject variability).
- **Pooled variance**: a weighted average of two sample variances, assuming equal population variances. Why pooled? It gives slightly more power if the assumption is true.
- **Degrees of freedom (Welch-Satterthwaite)**: when sample sizes or variances are unequal, the simple $n_1 + n_2 - 2$ formula is inaccurate.

### Analogies

The chapter uses one central analogy: **pairing is like measuring change in one person rather than comparing two different people.** This illuminates why pairing reduces noise. The analogy doesn't break down at the edges—it's fully accurate.

The unpooled vs. pooled choice is framed as a **trade-off, not a hierarchy**: pooled gains power at the cost of an assumption; unpooled is conservative. This reframes the "which is right?" question into "which matches your prior knowledge?"

### Trade-offs and decision trees

- **Independent vs. paired:** Is pairing in the study design, or arbitrary? Decision: use paired design only.
- **Unpooled vs. pooled:** Do you know the population SDs are equal? If no (almost always), use unpooled. If yes (rare), pooling gains power.
- **t-test vs. z-test:** Means or proportions? Means → t-test (estimate SD). Proportions → z-test (SD determined by p).

### Common misconceptions named and addressed

1. **Large samples are always reliable.** (No; bias matters more than size.)
2. **Sample means that look different must come from different populations.** (No; sampling variation explains observed differences.)
3. **Pooled variance is always better.** (Only if the assumption is true; unpooled is safer.)
4. **Paired data must show improvement.** (No; the test is symmetric.)
5. **A small p-value means the effect is large.** (No; significance ≠ magnitude. Always report effect size too.)

### Scale shifts

The chapter works from small studies (12 patients in rehabilitation, 400-person surveys) up to the large Phase III trial (160 per arm, 320 total) and hints at meta-analyses combining many trials. This shows the scaling logic: as sample size grows, p-values shrink for the same effect, but effect size (Cohen's d) stays the same.

### Worked examples

The source provides examples; the rewrite improves them:
- **Source brake pad example:** Two plants, mean lifespans 49.2K and 50.8K miles. Rewrite preserves this, adds context (why it matters for warranty), and walks through every arithmetic step.
- **Source rehabilitation example:** Employees' before-and-after scores on a performance review. Rewrite shifts to physical therapy (walking distance), which is more intuitive and concrete.
- **Source unemployment example:** The source uses a bank default rate example. Rewrite uses unemployment in two cities (more current, higher stakes).

### Computational detail

All chapter examples show the arithmetic in full:
- SE calculation: show each variance, each division, the sum, the square root.
- Test statistic: numerator, denominator, quotient.
- p-value: reference to t-table or z-table, notation of degrees of freedom, interpretation of the result.

This honors the CLAUDE.md rule: show the work on the page.

### Framing of p-values and hypothesis testing

The source treats hypothesis testing as a procedure to follow (state hypotheses, compute statistic, find critical value, make decision). The rewrite keeps the procedure but wraps it in honest language:

- **What a p-value means:** "Probability of seeing this difference or larger if the null is true."
- **What it doesn't mean:** "The probability the null is true," or "The effect is important," or "The alternative is 95% likely."

This is Montaignean: the rewrite names what the procedure does and doesn't do, protecting against misinterpretation.

### Connection to Chapter 9 and forward to Chapters 11+

- **Chapter 9 echoes:** The four-step procedure is identical. The only difference is that we're standardizing a difference of means (or proportions) instead of a single mean.
- **Chapter 11 (ANOVA):** Generalizes two-sample means test to many groups.
- **Chapter 13 (Regression):** Regression coefficients are tested using a t-test, which is conceptually a two-sample comparison.

---

## Pedagogical strengths in the source

1. **Multiple contexts:** The source covers independent means, pooled means, paired means, and proportions. This breadth is good; it shows the student that the same logic applies in different settings.
2. **Both worked examples and "try it" problems:** Source includes exercises the reader should attempt. Rewrite preserves this structure.
3. **Clear formula presentation:** Formulas are clearly stated and explained. Rewrite keeps them but adds step-by-step calculation for each example.

---

## Pedagogical gaps and fixes

1. **Weak motivation for test choice:** Source lists conditions without explaining why you'd choose one test over another. Rewrite builds a decision tree: are samples independent or paired? Are you testing means or proportions? Are you assuming equal variances?

2. **Abstract opening:** Source opens with "studies often compare two groups." Rewrite opens mid-scene in a clinical trial, with specific numbers and a question the reader cares about.

3. **Insufficient explanation of standard error formula:** Why does variance add, not average? Rewrite derives this from first principles: if one group is very variable, the difference is more variable.

4. **Effect size sidelined:** Source mentions Cohen's d in a separate section. Rewrite integrates it into the integration section, showing that p-value and effect size are complementary, not competing measures.

5. **Pooled variance presented as standard:** Source leads with pooled variance (m64421 before m55673). Rewrite leads with unpooled (safer), then explains when pooled is justified.

---

## Recommended follow-up or prerequisite reading

Before this chapter:
- Chapter 9 (Hypothesis Testing with One Sample): The four-step procedure is reused here.
- Chapter 7 (The Central Limit Theorem): The CLT justifies the normality of the difference of means.
- Chapter 2 (Descriptive Statistics): Computing means and standard deviations.

After this chapter:
- Chapter 11 (Chi-Square): Tests for independence in two-way tables (a variant on comparing proportions).
- Chapter 12 (ANOVA): Extends two-sample means to three or more groups.
- Chapter 13 (Linear Regression): Regression coefficients are tested using hypothesis tests on the slope.

