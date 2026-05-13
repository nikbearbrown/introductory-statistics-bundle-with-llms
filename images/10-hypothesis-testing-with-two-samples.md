# Images — Chapter 10

## Figure 1: Sampling Distribution of the Difference of Means

[FIGURE: Two populations with unknown means and standard deviations (shown as bell curves, slightly offset). Below them, a third distribution labeled "Sampling distribution of $\bar{x}_1 - \bar{x}_2$" centered at $\mu_1 - \mu_2$, normally distributed. Below that, a standard normal distribution (z-distribution) for reference. Arrows connecting each layer to show the CLT transformation from raw populations to the standardized difference.]

**Caption:** The central limit theorem applies to differences. Even if the two populations are not normal, the difference between their sample means follows an approximately normal distribution (or t-distribution when we estimate standard deviations). We standardize this difference to compute a test statistic.

---

## Figure 2: t-Distribution with Critical Regions (Two-Tailed Test, $\alpha = 0.05$)

[FIGURE: A t-distribution curve with approximately 75 degrees of freedom. The curve is centered at 0. Shaded regions in both tails at approximately $t = -1.99$ and $t = +1.99$. Each tail contains 2.5% of the area (labeled). The middle region (95%) is unshaded. A horizontal line at the test statistic $t = -2.32$ from the brake pad example, falling in the left tail (rejection region), with an arrow and label "observed test statistic".]

**Caption:** For a two-tailed test at $\alpha = 0.05$ with $df = 75$, the critical value is $\pm 1.99$. The observed test statistic $t = -2.32$ falls in the rejection region (left tail), so we reject $H_0$. The p-value (area in both tails beyond $\pm 2.32$) is approximately 0.023.

---

## Figure 3: Paired Data Example—Walking Distance Before and After Rehabilitation

[FIGURE: Twelve rows (one per patient). Each row shows a horizontal line from "Before" (left) to "After" (right). Patient 1: 150 m before, 240 m after (arrow upward, gap of 90 m). Patient 2: 120 m before, 180 m after (90 m gap). Patient 4: 100 m before, 190 m after (90 m gap). Patient 6: 160 m before, 260 m after (100 m gap, largest). Some patients show smaller improvements (20 m, 30 m). One patient shows a slight decline (−10 m). A dashed line at y = 0 (no change) for reference. Arrows above showing the distribution of differences, centered around +63 m (the mean difference).]

**Caption:** Each patient is a pair: measured before and after rehabilitation. The difference (after − before) is the data. Even though individuals improved by different amounts, the mean improvement of 63 meters is highly significant because the standard deviation of differences is small (38.2 meters) relative to the mean.

---

## Figure 4: Two-Proportion Test—Unemployment Rates in Two Cities

[FIGURE: Two bar charts side by side. Left chart: "City A" with a bar showing 0.12 (12%) unemployed and 0.88 (88%) employed, labeled "Unemployment: 12%". Right chart: "City B" with 0.10 (10%) unemployed and 0.90 (90%) employed, labeled "Unemployment: 10%". A bracket below connecting the two charts showing the difference: 0.02 (2 percentage points). Below that, the standard normal curve centered at 0, with $Z = 0.93$ marked (not in either tail, in the center region). Annotation: "$p = 0.35$ (fail to reject $H_0$)".]

**Caption:** The difference in sample proportions is 2 percentage points. When standardized by the pooled standard error, the z-statistic is 0.93, far from the critical value of ±1.96 (for $\alpha = 0.05$). The p-value of 0.35 indicates the observed difference can easily be explained by sampling variation alone.

---

## Figure 5: Effect Size (Cohen's d) Interpretation

[FIGURE: A horizontal number line from −2 to +2. Regions labeled: "−0.8 (large negative)", "−0.5 (medium negative)", "−0.2 (small negative)", "0 (no effect)", "+0.2 (small positive)", "+0.5 (medium positive)", "+0.8 (large positive)". The brake pad example's Cohen's d of −0.53 is marked on the line with a triangle, falling in the "medium negative" region. Below the line, three normal curves at d = −0.8, 0, and +0.8, showing increasing separation between the two group distributions as effect size grows.]

**Caption:** Cohen's *d* measures the standardized difference between two groups. The Midwest plant's pads (d = −0.53) are meaningfully worse than the West Coast plant's, not just statistically significantly different. Effect size and p-value together tell the full story.

---

## Figure 6: Power Curves for Two-Sample t-Test

[FIGURE: Three curves on a graph with "Effect Size (Cohen's d)" on the x-axis (0 to 1.0) and "Power (1 − β)" on the y-axis (0 to 1.0). Three curves representing different sample sizes: n = 20 per group (lowest curve), n = 50 per group (middle curve), n = 100 per group (top curve). All curves start near 0.05 (the Type I error rate at d = 0) and increase, approaching 1.0 as d increases. Annotations showing that to detect a medium effect (d = 0.5) with 80% power requires roughly 64 subjects per group (intersection of middle curve with y = 0.8).]

**Caption:** Power increases with larger effect sizes, larger sample sizes, and stronger evidence against the null. To design a study, you typically specify a minimum effect size you care about detecting, then calculate the sample size needed for 80% power.

---

## Figure 7: Paired vs. Independent Design—Variance Reduction

[FIGURE: Left side: "Independent samples". Two clouds of points (before and after groups) with considerable scatter. Horizontal line at "mean before" and "mean after", showing both the between-group difference and within-group variance. Right side: "Paired samples". A single cloud of difference scores centered near the mean difference. Annotation: "Paired design reduces variance by eliminating between-subject differences." A vertical measurement showing the SE for independent (larger) vs. paired (smaller), illustrating why paired tests are more powerful.]

**Caption:** In paired designs, variability between subjects (naturally stronger vs. naturally weaker people) is subtracted out, leaving only the within-subject change. This smaller variance produces a smaller standard error, higher test statistic, and greater power to detect an effect.

