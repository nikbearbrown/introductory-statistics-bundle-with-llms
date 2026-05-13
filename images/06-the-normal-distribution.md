# Images — Chapter 6: The Normal Distribution

## Figures to source or create

### Figure 6.1: The normal bell curve with labeled regions
**Description**: A smooth bell curve centered at the mean ($\mu$). Vertical lines mark:
- $\mu - 3\sigma$, $\mu - 2\sigma$, $\mu - \sigma$, $\mu$, $\mu + \sigma$, $\mu + 2\sigma$, $\mu + 3\sigma$ on the horizontal axis.
- Shaded bands showing the 68%, 95%, and 99.7% regions in different colors.
- Labels for each standard deviation band.
- Horizontal axis labeled "Value (in original units)" or "Z-score (standardized units)."

**Location in chapter**: Concept 1, after the introduction to the empirical rule.

**Purpose**: Show students visually what the empirical rule represents—regions of the curve.

---

### Figure 6.2: Height of a bell curve as a function of standard deviation
**Description**: Three normal curves with the same mean but different standard deviations ($\sigma$ small, medium, large). Show how:
- Smaller $\sigma$ produces a tall, narrow peak.
- Larger $\sigma$ produces a flat, wide curve.
- All three curves enclose the same total area (1.0) under them.

**Location in chapter**: Concept 1, explaining the role of $\sigma$ in the formula.

**Purpose**: Illustrate that $\sigma$ controls the *shape* of the normal distribution while the formula ensures the total probability remains 1.

---

### Figure 6.3: Z-score diagram—scaling and shifting
**Description**: Two side-by-side histograms:
- Left: Original normal distribution with raw scores on the x-axis (e.g., SAT scores 400–1600, mean ~1050).
- Right: The same data converted to z-scores (centered at 0, ranging from −3 to +3).
- Arrows showing the transformation from raw $x$ to standardized $z$.

**Location in chapter**: Concept 2, introducing z-scores.

**Purpose**: Make concrete the idea that standardization shifts the mean to 0 and rescales in units of standard deviations.

---

### Figure 6.4: Standard normal curve with table lookup regions
**Description**: A standard normal curve ($\mu=0$, $\sigma=1$) with:
- A vertical line at $z = 1.25$ (or some other positive value).
- Shaded region from 0 to 1.25 showing the area found in the table.
- Shaded regions to the left of 0 and to the right of 1.25 in a lighter shade, labeled with their areas computed from the table value.
- Numbers annotating each region: "0.5" to the left, "0.3944" in the center, "0.1056" to the right (for $z=1.25$ example).

**Location in chapter**: Concept 3, explaining how to use the standard normal table.

**Purpose**: Connect the abstract table value to regions of the curve.

---

### Figure 6.5: Cumulative probability—building from regions
**Description**: A sequence of three standard normal curves:
1. Shaded area from $-\infty$ to some value, say $z = 1.0$.
2. Same, but showing how the total is split: "0.5 (left of mean) + 0.3413 (mean to 1.0) = 0.8413."
3. Alternative: showing $P(z > 1.0) = 1 - 0.8413 = 0.1587$.

**Location in chapter**: Concept 3, after the table introduction.

**Purpose**: Train students to visually decompose probabilities into additive pieces using the symmetry and the table.

---

### Figure 6.6: Multiple z-scores and interval probabilities
**Description**: A standard normal curve with:
- Two vertical lines at, say, $z = -0.5$ and $z = 1.5$.
- Shaded region between them.
- Annotations: "Area from 0 to -0.5 = 0.1915; Area from 0 to 1.5 = 0.4332; Area between = 0.1915 + 0.4332 = 0.6247."

**Location in chapter**: Concept 3, worked example or integration section.

**Purpose**: Show how to find probabilities for intervals.

---

### Figure 6.7: Z-score interpretation—percentile ranks
**Description**: A standard normal curve with marked regions:
- $z = -2$: labeled "2.3rd percentile" or "bottom 2.3%"
- $z = 0$: labeled "50th percentile"
- $z = 1$: labeled "84th percentile"
- $z = 2$: labeled "97.5th percentile"

**Location in chapter**: Concept 2, when introducing z-score interpretation.

**Purpose**: Link z-scores directly to percentile positions students recognize.

---

### Figure 6.8: Histogram of real data (e.g., test scores) overlaid with normal curve
**Description**: A histogram of actual test scores with a smooth normal curve overlaid. The curve should fit reasonably well, showing:
- Single peak near the center.
- Symmetric tails.
- Concentration near the mean.

**Location in chapter**: Concept 1, when discussing when normal distribution is appropriate.

**Purpose**: Show that real data can approximate the normal distribution without being perfect.

---

### Figure 6.9: Skewed vs. normal distribution comparison
**Description**: Two histograms side by side:
- Left: A normal (symmetric) distribution.
- Right: A right-skewed distribution (e.g., income or response times).
- Annotations showing mean > median in the skewed case.

**Location in chapter**: Concept 1, when discussing when NOT to use normal distribution.

**Purpose**: Help students recognize visually when data deviate from normality.

---

### Figure 6.10 (Optional): Galton's quincunx or bean board
**Description**: A physical illustration or diagram of Galton's device: beans dropped through a series of pegs, falling into bins at the bottom. The resulting distribution of beans in the bins approximates a bell curve.

**Location in chapter**: Cold open or Concept 1.

**Purpose**: Historical grounding and intuitive explanation of where the bell curve comes from—chance, accumulation, symmetry.

---

## Data for standard normal table

A full standard normal z-table should be included (either as a separate appendix or linked). The table should show:

- Z-scores from 0.00 to 3.99 (in rows, with first two decimal places on the left; third decimal as column headers).
- Areas (probabilities) from 0 to z for each entry.
- Clear header explaining: "Area between 0 and z" or similar.

Example structure:

```
z       .00    .01    .02    .03  ...  .09
0.0    .0000  .0040  .0080  .0120      .0359
0.1    .0398  .0438  .0478  .0517      .0753
...
1.2    .3849  .3869  .3888  .3907      .4049
1.3    .4032  .4049  .4066  .4082      .4236
...
3.9    .49995 .49995 .49996 .49996     .50000
```

---

## Captions and attribution

- **Source**: Histograms and data distributions should be either from public datasets (e.g., Census Bureau for heights, College Board for SAT scores, NIH for medical measurements) or synthetic examples clearly labeled as such.
- **Attribution**: If images are taken from external sources, cite the source (e.g., "Adapted from OpenStax Introductory Statistics, Chapter 6").
- **Licensing**: Ensure all figures are either created fresh or used under CC-BY or similar open license.

---

