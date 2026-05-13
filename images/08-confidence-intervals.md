# Images and Figures: Confidence Intervals

Descriptions of visual assets needed for Chapter 8. These are scaffolded for creation.

---

## Figure 8.1: Sampling distribution and confidence interval region

**Description:** A standard normal curve (z-distribution) with the following annotations:
- Center at 0 (labeled $\mu$ for population mean, or $\mu_{\bar{x}}$ for sampling distribution).
- Two vertical lines at $z = -1.96$ and $z = 1.96$.
- The region between these lines shaded in light blue (95% of the area).
- The two tail regions (to the left of -1.96 and to the right of 1.96) shaded in light red (2.5% each, totaling 5%).
- Horizontal arrow spanning from -1.96 to 1.96, labeled "95% of sample means fall here."
- Caption: "The normal distribution: 95% of sample means within 1.96 standard deviations of the population mean."

**Relevant section:** Concept 1, illustration of the critical z-value and the interval region.

---

## Figure 8.2: z-distribution vs. t-distribution comparison

**Description:** Two overlaid curves on the same axes:
- The standard normal curve (z) in blue, labeled "Standard normal, z".
- A t-distribution curve (with df = 5) in red, labeled "Student's t, df = 5".
- Both centered at 0.
- The t-curve is noticeably taller and narrower in the center, with heavier tails.
- Vertical dashed lines at ±1.96 (the 95% z-critical value).
- Annotation: "t-distribution has heavier tails and captures less probability at ±1.96 than z."
- An arrow pointing to the tails of the t-curve, labeled "Extra probability here accounts for unknown σ".
- A table below showing critical values: "At 95% confidence, $z^* = 1.96$, $t_{5, 0.025} = 2.571$".

**Relevant section:** Concept 2, illustrating why Gossett's t-distribution was necessary.

---

## Figure 8.3: Confidence interval construction example (CI for mean, σ known)

**Description:** A stepped diagram showing the construction of a 95% CI for the Apple Music example:
- Row 1: Sample data: $\bar{x} = 2.0$, $\sigma = 1$, $n = 100$, CL = 95%.
- Row 2: Standard error calculation: $SE = 1/\sqrt{100} = 0.1$. Show the formula visually.
- Row 3: Critical value lookup: $z^* = 1.96$ (with a mini z-table or reference).
- Row 4: Margin of error: $EBM = 1.96 \times 0.1 = 0.196$.
- Row 5: Interval bounds: Lower = $2.0 - 0.196 = 1.804$, Upper = $2.0 + 0.196 = 2.196$.
- Row 6: Final interval: $(1.804, 2.196)$ or $2.0 \pm 0.196$.
- A number line below showing the interval as a thick bar from 1.804 to 2.196, with the point estimate 2.0 marked in the center.

**Relevant section:** Concept 1, worked example (Apple Music).

---

## Figure 8.4: Effect of sample size on interval width

**Description:** Three overlaid normal curves (sampling distributions) showing the effect of increasing $n$:
- Top curve: $n = 36$, $SE = 3/6 = 0.5$, interval approximately ±0.98, labeled "n = 36".
- Middle curve: $n = 100$, $SE = 3/10 = 0.3$, interval approximately ±0.59, labeled "n = 100".
- Bottom curve: $n = 400$, $SE = 3/20 = 0.15$, interval approximately ±0.29, labeled "n = 400".
- All centered at the same $\bar{x}$.
- Horizontal double-headed arrows showing the interval width for each.
- Caption: "As sample size increases, the standard error decreases, and the confidence interval narrows."

**Relevant section:** Concept 1, trade-offs section.

---

## Figure 8.5: Effect of confidence level on interval width

**Description:** Three overlaid normal curves showing the effect of changing confidence:
- Top curve: 90% confidence, $z^* = 1.645$, interval approximately ±1.645SE, labeled "90% confidence".
- Middle curve: 95% confidence, $z^* = 1.96$, interval approximately ±1.96SE, labeled "95% confidence".
- Bottom curve: 99% confidence, $z^* = 2.576$, interval approximately ±2.576SE, labeled "99% confidence".
- All centered at the same $\bar{x}$.
- Shaded regions showing the 90%, 95%, and 99% confidence areas under each curve.
- Caption: "As confidence level increases, the margin of error increases (interval widens)."

**Relevant section:** Concept 2, trade-offs section.

---

## Figure 8.6: t-distribution family (various degrees of freedom)

**Description:** A graph showing multiple t-distribution curves for different degrees of freedom:
- Curves for $df = 1, 3, 10, 30, \infty$ (the last one is the standard normal).
- $df = 1$ curve has the heaviest tails and is most different from normal.
- $df = \infty$ curve is labeled "Standard normal" and matches the z-curve.
- Vertical dashed lines at ±2 showing how the percentage captured changes with df.
- A table showing t-critical values for 95% confidence across df: $t_1 = 12.706$, $t_3 = 3.182$, $t_{10} = 2.228$, $t_{30} = 2.042$, $t_\infty = 1.96$.
- Caption: "As degrees of freedom increase, the t-distribution converges to the standard normal."

**Relevant section:** Concept 2, overview of t-distribution.

---

## Figure 8.7: Procedure interpretation: Repeating the study 100 times

**Description:** A conceptual diagram showing:
- The top shows a population with unknown mean $\mu$ (labeled "True parameter, $\mu$, unknown").
- Below, 100 small sample boxes, each representing a random sample of size $n$.
- From each sample, a horizontal line (confidence interval) is drawn.
- Each line is centered at the sample mean $\bar{x}_i$ and extends ±EBM on each side.
- About 95 of the lines intersect with a vertical dotted line at the true $\mu$ position.
- About 5 lines miss (lie entirely above or below $\mu$).
- Caption: "95% confidence procedure: In repeated sampling, about 95 of 100 intervals contain the true parameter. This particular interval (yours) either does or it doesn't—you'll never know which."

**Relevant section:** Concept 1, "The critical misunderstanding" and Integration sections.

---

## Figure 8.8: Confidence interval for a proportion

**Description:** A similar stepped diagram as Figure 8.3, but for the smartphone ownership example:
- Row 1: Sample data: $x = 421$, $n = 500$, $\hat{p} = 0.842$, CL = 95%.
- Row 2: Condition check: $np = 421 \geq 5$ ✓, $n(1-p) = 79 \geq 5$ ✓. "Normal approximation is valid."
- Row 3: Standard error: $SE = \sqrt{\frac{0.842 \times 0.158}{500}} = 0.0163$.
- Row 4: Critical value: $z^* = 1.96$.
- Row 5: Margin of error: $EBM = 1.96 \times 0.0163 = 0.0319 \approx 0.032$ or 3.2%.
- Row 6: Interval: $0.842 \pm 0.032 = (0.810, 0.874)$ or "81.0% to 87.4%".
- A number line showing the interval from 0.810 to 0.874, with 0.842 at the center.

**Relevant section:** Concept 3, worked example (smartphone ownership).

---

## Figure 8.9: Sample size formula and its implications

**Description:** A table or graph showing the relationship between margin of error and required sample size:

**Left side (table):**
| Desired margin of error | Sample size (p = 0.5, 95% confidence) |
|---|---|
| ±10% (0.10) | 97 |
| ±5% (0.05) | 385 |
| ±3% (0.03) | 1,067 |
| ±2% (0.02) | 2,401 |
| ±1% (0.01) | 9,605 |

**Right side (graph):**
A curve showing sample size (y-axis) vs. margin of error (x-axis). The curve should be hyperbolic, showing that as margin of error decreases, sample size increases dramatically. Mark the table values on the curve.

Caption: "Halving the margin of error requires quadrupling the sample size. Precision has a cost."

**Relevant section:** Integration section, sample size calculation.

---

## Figure 8.10: The cost of confidence vs. precision

**Description:** A three-panel visual:

**Panel A: Varying confidence level (margin of error fixed at ±3%)**
- Bar chart showing sample size needed for 90%, 95%, and 99% confidence.
- 90% CI: n ≈ 740
- 95% CI: n ≈ 1,067
- 99% CI: n ≈ 1,840
- Label: "Higher confidence requires larger sample."

**Panel B: Varying margin of error (confidence fixed at 95%)**
- Bar chart showing sample size needed for ±5%, ±3%, and ±1% margin of error.
- ±5%: n ≈ 385
- ±3%: n ≈ 1,067
- ±1%: n ≈ 9,605
- Label: "Higher precision (smaller margin) requires much larger sample."

**Panel C: The trade-off summary**
- A conceptual diagram with three axes: confidence level, margin of error, and sample size.
- An arrow showing: increase confidence → increase sample size; decrease margin → increase sample size.
- Label: "You can't have high confidence and small margins of error without a large sample."

**Relevant section:** Integration section, discussing the three-way trade-off.

---

## Notes on asset creation

These figures should be created in a vector format (SVG or similar) so they scale cleanly across different screen sizes and print resolutions. Figures 8.1, 8.2, 8.4, 8.5, and 8.6 are particularly suited to dynamic media: small HTML5 widgets or interactive plots where a user can adjust parameters (sample size, confidence level, $\sigma$) and see the interval change in real time.

The color scheme should be consistent with the rest of the textbook:
- Primary curves: blue.
- Secondary curves for comparison: red or orange.
- Shaded confidence regions: light blue.
- Tail regions (outside confidence): light red or light gray.
- Axis labels: black or dark gray.
- Critical values and annotations: bold sans-serif font.

All figures should include axis labels, legends, and a descriptive caption below. Figures should be numbered sequentially (8.1, 8.2, etc.) and referenced by number in the chapter text.
