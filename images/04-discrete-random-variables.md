# Images and Figures — Chapter 4: Discrete Random Variables

## List of figures to produce

These figures support the narrative. Each should include a clear caption that explains what the student should observe.

### Figure 4.1 — Binomial PMF: small $p$, large $n$

**Context:** Concept 3, worked example on vaccine effectiveness.

**Specification:**
- Bar chart (histogram) of a binomial distribution with $n = 20$, $p = 0.70$.
- X-axis: number of successes (0 to 20).
- Y-axis: probability $P(X = k)$ (0 to 0.25).
- Label the mode (peak) at $k = 14$ (since $np = 14$).
- Shade the region $P(X \geq 15)$ in a contrasting color to highlight the answer to the worked example.

**Caption:** The binomial distribution with $n = 20$ trials and $p = 0.70$ probability of success. The distribution is slightly left-skewed because $p > 0.5$. The shaded region represents $P(X \geq 15)$, the probability of at least 15 successes, which is approximately 0.42. The mean is $\mu = 14$ and standard deviation is $\sigma \approx 2.05$. Most outcomes fall between 11 and 17 successes.

### Figure 4.2 — Binomial PMF: varying $p$

**Context:** Concept 3, to show how the binomial shape changes with probability.

**Specification:**
- Three bar charts side-by-side, each with $n = 10$ but $p = 0.25, 0.50, 0.75$.
- All with the same scale for easy comparison.
- Left panel: right-skewed (few successes likely when $p$ is small).
- Middle panel: symmetric (when $p = 0.5$).
- Right panel: left-skewed (many successes likely when $p$ is large).

**Caption:** How the binomial distribution changes with the probability of success $p$. When $p = 0.25$ (left), successes are rare and the distribution is right-skewed. When $p = 0.50$ (center), the distribution is symmetric around the mean. When $p = 0.75$ (right), failures are rare and the distribution is left-skewed. The mean shifts from $np = 2.5$ (left) to $5$ (center) to $7.5$ (right).

### Figure 4.3 — Poisson PMF: varying $\mu$

**Context:** Concept 4, to show different Poisson distributions.

**Specification:**
- Three bar charts, each a Poisson distribution with $\mu = 2, 5, 10$.
- All with the same style; X-axis goes to at least 20.
- Show how the distribution spreads and becomes more symmetric as $\mu$ increases.

**Caption:** The Poisson distribution with different mean rates $\mu$. When the average rate is low ($\mu = 2$, left), outcomes are skewed right; most events are 0–4 occurrences. When $\mu = 5$ (center), the distribution is more spread but still slightly right-skewed. When $\mu = 10$ (right), the distribution is nearly symmetric and the range of likely values is wider. Note that in all three cases, the standard deviation is $\sigma = \sqrt{\mu}$, so variability increases with the mean.

### Figure 4.4 — Expected value as a balance point

**Context:** Concept 2, to illustrate the intuition behind expected value.

**Specification:**
- A number line from 0 to 4, with a fulcrum (balance point) at $\mu = 1.7$ (from the bakery example).
- Probabilities indicated as "weights" at each value: $x = 1$ has weight 0.30, $x = 2$ has weight 0.44, $x = 3$ has weight 0.20, $x = 4$ has weight 0.06.
- Show the fulcrum balanced at 1.7, suggesting that the probabilities on each side balance out.

**Caption:** The expected value as a balance point. If each outcome is a weight on a seesaw (weighted by its probability), the fulcrum must be placed at $\mu = 1.7$ for the seesaw to balance. This is the weighted average of all outcomes.

### Figure 4.5 — Binomial vs. Poisson comparison

**Context:** Concept 4, to show the relationship between binomial and Poisson.

**Specification:**
- Two overlaid bar charts on the same axes: binomial with $n = 100$, $p = 0.05$ (so $np = 5$), and Poisson with $\mu = 5$.
- One color for binomial bars, another for Poisson bars, with transparency so both are visible.
- X-axis: 0 to 15 successes/events.
- They should look nearly identical, illustrating that Poisson approximates binomial when $n$ is large and $p$ is small.

**Caption:** Binomial distribution with $n = 100$, $p = 0.05$ (blue bars) and Poisson distribution with $\mu = 5$ (red outline). When $p$ is small and $n$ is large such that $np$ is moderate, the Poisson is an excellent approximation to the binomial. This is why Poisson distributions are useful: they're much easier to compute than binomial when $n$ is very large.

### Figure 4.6 — Standard deviation bands for Poisson

**Context:** Chapter integration, to help interpret operational decisions.

**Specification:**
- A Poisson distribution with $\mu = 5$ (e.g., call center arrivals).
- Overlay bands showing $\mu$, $\mu \pm \sigma$, and $\mu \pm 2\sigma$.
- Color the region within one standard deviation (5 ± 2.24) in one shade, two standard deviations in a lighter shade.
- Label the probabilities: 68% within $\pm \sigma$, 95% within $\pm 2\sigma$ (approximately, for Poisson).

**Caption:** Expected arrivals (Poisson, $\mu = 5$) with standard deviation bands. The shaded region within one standard deviation ($\mu \pm \sigma = 5 \pm 2.24$) contains about 68% of outcomes. About 95% of outcomes fall within two standard deviations ($5 \pm 4.47$). An operational manager would staff to handle outcomes in the two-standard-deviation band (roughly 1–9 arrivals) to cover 95% of typical hours.

---

## Guidance for figure creation

### Software recommendations

- **R + ggplot2:** Excellent for publication-quality bar charts and overlays.
- **Python + matplotlib or seaborn:** Good for quick, professional plots.
- **Desmos:** Online graphing tool suitable for simpler figures.
- **GeoGebra:** Good for interactive visualizations (though not needed for static textbook).

### Style guidelines

- Use a clear, sans-serif font (Helvetica, Arial, or similar).
- Label axes fully: "Number of successes ($k$)" not just "$k$."
- Include a legend when multiple distributions are shown.
- Use consistent color schemes across figures (e.g., binomial always blue, Poisson always red).
- Ensure figures are high resolution (at least 300 dpi for print).
- Provide a descriptive caption (2–3 sentences) that explains what the student should observe.

---

## Data and parameters for figure generation

### Binomial figures

**Figure 4.1 – Binomial PMF ($n=20$, $p=0.70$):**
```
k = 0, 1, 2, ..., 20
P(X=k) = C(20,k) * (0.70)^k * (0.30)^(20-k)
Example values:
P(X=14) ≈ 0.1916 (mode)
P(X=13) ≈ 0.1643
P(X=15) ≈ 0.1304
```

**Figure 4.2 – Binomial PMF with varying $p$ ($n=10$):**
```
p = 0.25: mean = 2.5, mode at k=2 or k=3
p = 0.50: mean = 5, mode at k=5
p = 0.75: mean = 7.5, mode at k=7 or k=8
```

### Poisson figures

**Figure 4.3 – Poisson PMF with varying $\mu$:**
```
μ = 2: P(X=k) = (2^k * e^-2) / k! for k=0,1,2,...,15
μ = 5: P(X=k) = (5^k * e^-5) / k! for k=0,1,2,...,20
μ = 10: P(X=k) = (10^k * e^-10) / k! for k=0,1,2,...,25
```

**Figure 4.6 – Poisson ($\mu=5$) with standard deviation bands:**
```
μ = 5
σ = √5 ≈ 2.236
Bands: [μ-σ, μ+σ] = [2.764, 7.236]
        [μ-2σ, μ+2σ] = [0.528, 9.472]
```

---

## Alternatives and extensions

### Interactive figure suggestions (if platform supports them)

1. **Slider for binomial parameters:** Allow students to adjust $n$ and $p$ and see the distribution update in real-time.
2. **Poisson vs. Binomial overlay with slider:** Change $n$ and $p$ such that $np$ is constant; watch Poisson approximate binomial.
3. **Expected value visualization:** Show the balance point moving as probabilities change.

### Figure checklist before publication

- [ ] All axes are labeled with units.
- [ ] Legend (if applicable) is clear and positioned consistently.
- [ ] Color scheme is color-blind-friendly (avoid red-green combinations).
- [ ] Figures are referenced in the chapter text by number (e.g., "Figure 4.1").
- [ ] Captions are informative and guide student interpretation.
- [ ] Source data or formulas used are documented (in this file, they are).
- [ ] File sizes are reasonable (not bloated; suitable for PDF and web distribution).

