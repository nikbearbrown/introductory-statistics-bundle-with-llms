# Images and Visualizations: Chapter 9 — Hypothesis Testing with One Sample

Note: Original source material contained placeholder figure references. Recommended visualizations below.

---

## Figure 9.1: Sampling distribution under H₀ with critical regions (two-tailed test)

**What it shows:** A standard normal distribution centered at μ₀. The rejection regions (typically colored red) occupy the outermost 2.5% in each tail (for α = 0.05). The fail-to-reject region (green) occupies the central 95%.

**When to use:** Explaining the critical value approach and what it means for a test statistic to be "in the rejection region" or "not extreme enough."

**Visual elements:**
- Horizontal axis: z-scores or sample means
- Vertical axis: probability density
- Vertical lines at z = ±1.96 (for α = 0.05, two-tailed)
- Shaded regions in both tails beyond the critical values
- Label indicating rejection region vs. fail-to-reject region

---

## Figure 9.2: Type I and Type II errors in context

**What it shows:** Two overlapping normal distributions: one centered at μ₀ (H₀ true) and one centered at μₐ (H₀ false). The critical value partitions these. Area in the H₀ distribution beyond the critical value = α (Type I error). Area in the Hₐ distribution within the fail-to-reject region = β (Type II error). Area in the Hₐ distribution beyond the critical value = power (1 - β).

**When to use:** Visualizing the trade-off between Type I and Type II errors and explaining why you can't minimize both simultaneously.

**Visual elements:**
- Two overlapping bell curves
- Vertical line at critical value
- Shaded region (left tail) under H₀ curve = α
- Shaded region (left tail) under Hₐ curve = β
- Labeled arrows and legend

---

## Figure 9.3: P-value visualization (one-tailed test)

**What it shows:** A standard normal distribution. A vertical line marks the observed test statistic. The p-value is the area in the tail beyond that line (for a one-tailed test) or in both tails equally extreme (for a two-tailed test).

**When to use:** Explaining what a p-value represents: the probability of observing a test statistic this extreme or more extreme, if H₀ is true.

**Visual elements:**
- Standard normal distribution
- Vertical line at observed z-value (e.g., z = 2.1)
- Shaded tail area beyond the line (colored red)
- Label: "p-value = area in tail = 0.0179" (example)
- Caption clarifying this is probability of data given H₀, not probability of H₀ given data

---

## Figure 9.4: Decision tree for hypothesis test

**What it shows:** A flowchart guiding the user through the five-step process.

**Steps:**
1. State H₀ and Hₐ. Is it one-tailed or two-tailed?
2. Set significance level α. (0.05 is standard.)
3. Choose test statistic. (Is σ known? Is n large?)
4. Calculate. (Plug in numbers.)
5. Compare and decide. (Is test statistic more extreme than critical value? Is p-value < α?)
6. Conclude in two ways: formal statistical statement and action.

**Visual elements:** Boxes with decision points, arrows showing flow, example outcomes at terminal nodes.

---

## Figure 9.5: Comparing z-test and t-distribution

**What it shows:** Two overlaid distributions: the standard normal (z) and the t-distribution with df = 10 (showing the wider tails). As df increases, the t-distribution approaches the normal.

**When to use:** Explaining why the t-distribution is used when σ is unknown and n is small, and why it matters (wider tails account for uncertainty).

**Visual elements:**
- Two curves (z in blue, t in red)
- Vertical lines at critical values (e.g., ±1.96 for z, ±2.228 for t with df = 10)
- Label indicating the t-distribution is wider, more spread

---

## Figure 9.6: P-hacking illustration

**What it shows:** A grid of 20 hypothesis tests, each with a 5% significance level. Under the null hypothesis (no real effect), we expect about 1 in 20 to show p < 0.05 by random chance. If a researcher runs 20 tests and reports only the significant one, the result looks like evidence of an effect when it's actually just noise.

**When to use:** Illustrating the multiple comparisons problem and why pre-registration protects against p-hacking.

**Visual elements:**
- 20 boxes, each representing one hypothesis test
- Most boxes show p > 0.05 (colored green, "not significant")
- 1–2 boxes show p < 0.05 (colored red, "significant")
- Annotation: "If only the red box is reported, readers think there's evidence of an effect. But it's just chance variation under the null."

---

## Figure 9.7: One-tailed vs. two-tailed tests

**What it shows:** Two standard normal distributions side by side.

Left (two-tailed): Critical values at both tails (e.g., ±1.96 for α = 0.05). The rejection region is split: 2.5% in each tail.

Right (one-tailed): Critical value in one tail only (e.g., 1.645 for α = 0.05 right-tailed). The rejection region is all 5% in the upper tail.

**When to use:** Explaining the difference between one-tailed and two-tailed tests and why the choice of test affects the critical value.

**Visual elements:**
- Two side-by-side distributions
- Shaded rejection regions (red)
- Vertical lines marking critical values
- Labels indicating the split in two-tailed vs. concentrated in one-tailed

---

## Figure 9.8: Sampling distribution of sample proportion

**What it shows:** A histogram or smooth curve representing the distribution of sample proportions under H₀ (centered at p₀). Illustrates that with large enough sample, the binomial is well-approximated by normal.

**When to use:** Explaining the basis for the z-test for proportions and the conditions (np > 5, nq > 5).

**Visual elements:**
- Normal-looking distribution centered at p₀
- Label indicating this is the sampling distribution of p' under H₀
- Note on the conditions required for normal approximation

---

## Notes on translation of source figures

The original OpenStax source contained 6 placeholder `<figure>` elements (ids: fs-idm165993648, eip-id7318150, eip-idm376525904, eip-id1169346631895, eip-id1164402606956, fs-idm149132800) in modules 01, 04, 04, 04, 04, and 05. These were diagrams showing:

- Hypothesized distribution of sample means under H₀
- Test statistics and critical regions
- Type I and Type II error regions
- P-value areas on the normal curve
- One-tailed vs. two-tailed test regions

The visualizations recommended above capture the conceptual content. In a production version, high-quality diagrams should be created to illustrate these concepts clearly and consistently with the Attenborough × Feynman pedagogical style (clear labels, emphasis on the machinery, honest representation of uncertainty).

