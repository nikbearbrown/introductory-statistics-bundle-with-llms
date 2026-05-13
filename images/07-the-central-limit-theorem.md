# Images and Figures: Chapter 7 — The Central Limit Theorem

## FIGURE 7.1: Three layers of distribution

**Caption:** The population distribution, a single sample, and the sampling distribution of sample means are three different things. (A) Population distribution: The distribution of all individual measurements. (B) One sample: A random sample of measurements from the population. (C) Sampling distribution: The theoretical distribution of sample means if you repeated sampling many times.

**Description:**
- Panel A (top): A roughly bell-shaped curve labeled "Population distribution of individual tablets (500 mg ± 12 mg)." The x-axis shows "Vitamin C content (mg)" from 460 to 540. A shaded area indicates the distribution centered at 500 mg with standard deviation 12 mg.
- Panel B (middle): A histogram of 25 individual measurements labeled "One random sample of 25 tablets." The sample mean is marked with a vertical line at 498.5 mg. The x-axis is the same as Panel A.
- Panel C (bottom): A narrow, normal bell curve labeled "Sampling distribution of sample means (if we repeated sampling forever)." The x-axis shows "Sample mean (mg)" from 490 to 510. The curve is centered at 500 mg with a much tighter standard deviation (the standard error, 2.4 mg). A vertical line marks the observed sample mean at 498.5 mg.

**Pedagogical purpose:** Clarify the distinction between three distributions that often confuse students: the distribution of the population, the distribution of a single sample, and the theoretical sampling distribution that the CLT describes.

---

## FIGURE 7.2: Effect of sample size on standard error

**Caption:** As sample size increases, the standard error decreases. Here, all three sampling distributions come from the same population ($\mu = 70$, $\sigma = 2.5$), but with different sample sizes.

**Description:**
- Three overlapping normal curves, all centered at 70 inches.
- Curve 1 (widest): Labeled "$n = 10$, SE = 0.79 inches." Extends roughly from 68 to 72 inches.
- Curve 2 (medium): Labeled "$n = 40$, SE = 0.40 inches." Extends roughly from 69 to 71 inches.
- Curve 3 (narrowest): Labeled "$n = 100$, SE = 0.25 inches." Extends roughly from 69.5 to 70.5 inches.
- The curves are vertically scaled so that the area under each is 1 (they are probability distributions), which makes the narrower curves taller.
- Shaded regions at both sides of each curve indicate the tails where data become less likely.

**Pedagogical purpose:** Visually demonstrate the square-root law: sample size increases do not linearly reduce standard error, but rather by the square root of the sample size increase. This shows why going from $n = 10$ to $n = 40$ improves precision more dramatically than going from $n = 40$ to $n = 100$.

---

## FIGURE 7.3: The CLT with non-normal populations

**Caption:** The Central Limit Theorem applies to any population distribution. Here we see three very different population shapes and how their sampling distributions become increasingly normal as sample size increases.

**Description:**

### Row 1: Normal population
- Population distribution: A standard bell curve, already normal.
- Sampling distribution at $n = 10$: Bell curve, looks normal.
- Sampling distribution at $n = 25$: Bell curve, looks normal.
- Sampling distribution at $n = 50$: Bell curve, looks normal.
- Conclusion label: "Even small $n$ produces normal sample means."

### Row 2: Uniform population
- Population distribution: A flat rectangle from 6 to 10, labeled "Uniform [6, 10]."
- Sampling distribution at $n = 10$: Histogram with a somewhat rectangular shape, edges visible.
- Sampling distribution at $n = 25$: Histogram that looks more like a bell, edges smoothing out.
- Sampling distribution at $n = 50$: Histogram that is very close to a bell curve.
- Conclusion label: "Sample means become normal around $n = 20$–30."

### Row 3: Exponential population
- Population distribution: A right-skewed curve that starts high at the left and decays to the right, labeled "Exponential."
- Sampling distribution at $n = 10$: Histogram that is noticeably right-skewed.
- Sampling distribution at $n = 25$: Histogram that is less skewed; more bell-shaped in the center but still has a right tail.
- Sampling distribution at $n = 50$: Histogram that looks much more like a normal distribution, though some skewness might remain visible.
- Conclusion label: "Skewed populations require $n \geq 50$ or larger."

**Pedagogical purpose:** Demonstrate that the CLT works for populations of very different shapes, and that the rule of thumb ($n \geq 30$) is a reasonable practical guideline, though the exact value depends on how far the population is from normal.

---

## FIGURE 7.4: The z-score for a sample mean

**Caption:** A sample mean can be standardized just like an individual observation. The z-score tells us how many standard errors the sample mean is from the population mean.

**Description:**
- A normal curve centered at $\mu = 64$ ounces.
- The x-axis shows bottle volumes in ounces: 63.5, 64.0, 64.2, 64.5.
- A vertical line at the population mean $\mu = 64$ is labeled.
- Another vertical line at the observed sample mean $\bar{x} = 64.2$ is labeled.
- The distance between them is labeled "$\bar{x} - \mu = 0.2$ ounces."
- Below the curve, a bracket shows "SE = 0.133 ounces."
- A label states: "$z = 0.2 / 0.133 = 1.50$ standard errors."
- The area to the right of $\bar{x} = 64.2$ (the upper tail) is shaded, labeled "P = 0.0668 or 6.68%."

**Pedagogical purpose:** Show how standardizing a sample mean using the standard error allows us to calculate probabilities. The formula and interpretation are visually grounded.

---

## FIGURE 7.5: The Law of Large Numbers

**Caption:** As you take larger and larger samples, the sample mean converges to the population mean. Each point is the mean of a sample of size $n$; successive points use larger values of $n$.

**Description:**
- A horizontal line at $y = 100$, labeled "True population mean ($\mu$)."
- Scatter plot above and below this line showing sample means for progressively larger samples.
- First cluster of points (labeled "$n = 5$"): Points scattered widely around 100, ranging roughly from 95 to 105.
- Second cluster (labeled "$n = 20$"): Points closer to 100, scattered roughly from 98 to 102.
- Third cluster (labeled "$n = 50$"): Points even tighter, scattered roughly from 99 to 101.
- Fourth cluster (labeled "$n = 100$"): Points clustered very close to 100, scattered roughly from 99.5 to 100.5.
- The overall pattern shows convergence: as $n$ increases, sample means cluster tighter around the true population mean.
- Annotations point out: "Wider spread with small $n$" and "Narrower spread with large $n$."

**Pedagogical purpose:** Visualize the Law of Large Numbers: as sample size increases, the sample mean converges to the population mean, and the variability of sample means shrinks.

---

## FIGURE 7.6: Casino table example—nightly take converges

**Caption:** A real-world example: the nightly "take" (profit) at a craps table converges to the house edge as the number of hours of operation increases.

**Description:**
- Line graph showing the cumulative house profit over 16 hours.
- X-axis: Time (hours), from 0 to 16.
- Y-axis: Cumulative house profit as a percentage of money wagered.
- A jagged line that fluctuates up and down, showing hourly variation.
- Early hours (0–4): The line bounces around wildly, from +8% to −2%.
- Middle hours (4–12): The line is still bouncy but the range tightens. The bounces are smaller.
- Late hours (12–16): The line has stabilized around +2.4%, the theoretical house edge.
- A horizontal dashed line at +2.4% represents "Expected house edge (theoretical)."
- Annotation: "With few hours, variance is high" (pointing to early jagged section).
- Annotation: "With many hours, variance shrinks; converges to theoretical value" (pointing to the late, flat section).

**Pedagogical purpose:** Show that the CLT and Law of Large Numbers apply to real-world data, not just textbook examples. As the casino runs more trials (more spins of the roulette wheel, more rolls of the dice), the average outcome converges to its theoretical expectation.

---

## FIGURE 7.7: Standard error decreases with sample size (manufacturing example)

**Caption:** In manufacturing quality control, larger samples give more precise estimates of the true process mean.

**Description:**
- Three normal curves stacked vertically, all centered at $\mu = 25$ pounds.
- Top curve: Labeled "Population distribution ($n = 1$): SD = 0.5774 lb." Very wide.
- Middle curve: Labeled "Sampling distribution at $n = 25$: SE = 0.115 lb." Narrower.
- Bottom curve: Labeled "Sampling distribution at $n = 100$: SE = 0.058 lb." Very narrow, tall.
- All three curves have their peak area shaded.
- Horizontal arrows beneath each curve show the range $\mu \pm 1 \text{ SE}$ or $\mu \pm 1 \sigma$.
- The ranges shrink dramatically as $n$ increases.

**Pedagogical purpose:** Show that in practice (e.g., manufacturing), larger samples allow more precise estimates of the true population mean. This is why quality control engineers prefer large samples.

---

## FIGURE 7.8: Comparison—individual vs. sample mean distributions

**Caption:** The distribution of individual observations is much wider than the distribution of sample means. Individual scores vary far more than averages.

**Description:**
- Two normal curves on the same graph.
- Curve 1 (wider, lighter shading): Labeled "Distribution of individual SAT scores ($\sigma = 150$)." Extends roughly from 550 to 1550.
- Curve 2 (narrower, darker shading): Labeled "Distribution of sample means, $n = 25$ ($\sigma_{\bar{x}} = 30$)." Extends roughly from 990 to 1110, centered at 1050.
- Both curves centered at $\mu = 1050$.
- Annotations explain: "An individual student might score anywhere in this wide range. But the average of 25 students clusters much tighter."

**Pedagogical purpose:** Clarify a common misconception: the CLT does not say individual observations are normally distributed; it says *means* of samples are normally distributed. This figure shows why using the standard error (not the population SD) is correct when making inferences about sample means.

---

## Notes on all figures

All figures should use consistent notation:
- Greek letters $\mu$, $\sigma$, $\bar{x}$ for clarity.
- Shaded regions under curves for probabilities.
- Vertical lines to mark means and observed values.
- Labels in the body text (not just figure captions) so students know exactly what each region represents.

Colors (suggested):
- Population distribution: Light blue.
- Sample distribution: Medium blue.
- Sampling distribution: Dark blue or dark green.
- Shaded probability regions: Light red or orange.

All axes should be clearly labeled with units (e.g., "ounces," "inches," "pounds").
