# Images and Figures — Continuous Random Variables

## Figure descriptions (placeholders for actual graphics)

### Figure 5.1: Continuous vs. discrete random variables

[FIGURE: Side-by-side comparison]

**Left panel:** Discrete random variable (number of heads in 10 coin flips). Bar graph with distinct bars at $X = 0, 1, 2, \ldots, 10$. Heights are the probabilities. Height of bar at $X = 3$ might be 0.117, etc.

**Right panel:** Continuous random variable (waiting time at a bus stop, 0 to 12 minutes). Horizontal line at height $1/12 \approx 0.083$ from 0 to 12. Area under the line between any two points $c$ and $d$ is the probability $P(c < X < d)$.

**Caption:** Discrete outcomes have nonzero probability at each point (bar height). Continuous outcomes have zero probability at any single point; probability lives in intervals as area under the curve.

---

### Figure 5.2: Probability density function (pdf) is not probability

[FIGURE: Single uniform distribution curve]

Horizontal line at height $f(x) = 1/12$ from $x = 0$ to $x = 12$. 

**Shaded region:** Area from $x = 2$ to $x = 5$ is shaded light blue. The region is labeled "Area = 3 × (1/12) = 0.25 = $P(2 < X < 5)$."

**Arrow pointing to the line itself:** Labels "Height $f(x) = 1/12$ is density, not probability."

**Arrow pointing to the shaded area:** "Area under the curve = probability."

**Caption:** The height of the density function is not a probability. The area under the curve between two points is the probability. A thin slice at any single point has zero width, thus zero area, and zero probability.

---

### Figure 5.3: Uniform distribution $X \sim U(0, 15)$

[FIGURE: Rectangle with labeled axes and dimensions]

Horizontal axis labeled "$x$ (minutes)" from 0 to 15. Vertical axis labeled "$f(x)$" from 0 to about 0.1. 

A rectangle drawn from $(0, 0)$ to $(15, 1/15)$. The top edge is at height $f(x) = 1/15 \approx 0.0667$.

**Labeled dimensions:** Base = 15, Height = $1/15$. Area = $15 \times (1/15) = 1$.

**Shaded region A:** A lighter shade from $x = 0$ to $x = 5$ with area label "$P(X < 5) = 5/15 = 1/3$."

**Shaded region B:** A different shade from $x = 5$ to $x = 12.5$ with area label "$P(5 < X < 12.5) = 7.5/15 = 0.5$."

**Caption:** Uniform distribution on $[0, 15]$. Probability of any interval is the fraction of the total width. The 75th percentile is at $x = 11.25$ (where the left region contains 75% of the total area).

---

### Figure 5.4: Exponential distribution with three decay parameters

[FIGURE: Three overlapping decay curves]

Horizontal axis labeled "$x$ (time)" from 0 to 10. Vertical axis labeled "$f(x)$" from 0 to about 1.5.

Three curves overlaid:
1. $m = 1.5$ (steepest decay). Labeled with $f(0) = 1.5$. Decays steeply.
2. $m = 1.0$ (medium decay). Labeled with $f(0) = 1.0$. Moderate curve.
3. $m = 0.5$ (gentlest decay). Labeled with $f(0) = 0.5$. Flattest curve.

All curves start positive at the vertical axis and approach zero as $x$ increases.

**Caption:** Three exponential distributions with different decay parameters. Higher $m$ (or equivalently, lower $\mu$) means faster decay—shorter times are much more probable. All exponential distributions are right-skewed with the mode at zero.

---

### Figure 5.5: Waiting time probabilities (exponential, $\mu = 4$ minutes)

[FIGURE: Single exponential curve with shaded regions]

Horizontal axis labeled "$x$ (minutes)" from 0 to 20. Vertical axis labeled "$f(x)$" from 0 to about 0.25.

Exponential curve $f(x) = (1/4)e^{-x/4}$, starting at $(0, 0.25)$ and asymptotically approaching zero.

**Shaded region A:** From $x = 0$ to $x = 1$ in light blue. Label: "$P(X < 1) \approx 0.221$."

**Shaded region B:** From $x = 1$ to $x = 10$ (the rest of the area from 0 to 10) in a lighter shade. Label: "$P(1 < X < 10) \approx 0.632$."

**Unshaded region:** From $x = 10$ onwards. Label: "$P(X > 10) \approx 0.082$."

**Caption:** Exponential distribution with mean 4 minutes. Most probability is concentrated in short times. Long waits are possible but increasingly rare.

---

### Figure 5.6: Cumulative distribution function (CDF) for uniform and exponential

[FIGURE: Two side-by-side line graphs]

**Left panel (Uniform CDF):**
Horizontal axis "$x$" from 0 to 15. Vertical axis "$F(x) = P(X \leq x)$" from 0 to 1.

Straight diagonal line from $(0, 0)$ to $(15, 1)$. Flat at 0 for $x < 0$. Flat at 1 for $x > 15$.

Label: "$F(x) = x/15$ for $0 \leq x \leq 15$." Horizontal dashed line at $F = 0.75$ intersects the diagonal at approximately $x = 11.25$ (the 75th percentile).

**Right panel (Exponential CDF):**
Horizontal axis "$x$" from 0 to 20. Vertical axis "$F(x) = P(X \leq x)$" from 0 to 1.

Curve starting at $(0, 0)$ and asymptotically approaching 1. Shape is an increasing concave curve (increasing rate of increase near zero, then leveling off).

Label: "$F(x) = 1 - e^{-x/\mu}$." Horizontal dashed line at $F = 0.5$ intersects the curve at approximately $x = 2.8$ (the median, less than the mean $\mu = 4$).

**Caption:** Cumulative distributions show probability up to value $x$. Uniform CDF is a straight line (linear accumulation). Exponential CDF is a curve (rapid accumulation at small $x$, then leveling off).

---

### Figure 5.7: Memoryless property illustration

[FIGURE: Timeline with labeled points]

Horizontal timeline from 0 to 20, labeled "Time (minutes)".

**First scenario (top):** "Starting fresh"
- Vertical line at $t = 0$ labeled "START."
- Vertical line at $t = 1$ labeled "Next event by here?"
- Shaded region from 0 to 1, labeled "$P(X < 1) \approx 0.22$."

**Second scenario (bottom):** "Already waited 10 minutes"
- Vertical line at $t = 10$ labeled "NOW (already waited 10 min)."
- Vertical line at $t = 11$ labeled "Next event by here?"
- Shaded region from 10 to 11, labeled "$P(X < 11 | X > 10) = P(X < 1) \approx 0.22$."

**Arrow between scenarios:** "Same probability!"

**Caption:** The memoryless property: the probability of the next event arriving within 1 minute is the same whether you start from the beginning or from 10 minutes in. Past waiting history is irrelevant.

---

### Figure 5.8: Why exponential is right-skewed

[FIGURE: Histogram-style representation of outcomes]

Horizontal axis "$x$ (time in units of $\mu$)" from 0 to 5. 

Bars of decreasing height, representing the probability density (density, not count):
- Bar from 0 to 0.5 with height about 0.7
- Bar from 0.5 to 1 with height about 0.43
- Bar from 1 to 1.5 with height about 0.27
- Bar from 1.5 to 2 with height about 0.16
- Bar from 2 to 3 with height about 0.05
- Bar from 3 to 5 with height about 0.01 (tiny)

**Mean marker:** Vertical dashed line at $x = 1$ labeled "$\mu = 1$."
**Median marker:** Vertical dashed line at $x \approx 0.69$ labeled "Median $\approx 0.69\mu$."
**Mode marker:** Label at $x = 0$ saying "Mode = 0."

**Caption:** The exponential distribution is always right-skewed. The median is less than the mean. Most outcomes cluster near zero; occasional large values pull the mean upward.

---

### Figure 5.9: Uniform (rectangular) vs. exponential (decaying)

[FIGURE: Two density functions on the same axes for comparison]

Horizontal axis "$x$" from 0 to 10. Vertical axis "$f(x)$" from 0 to 0.15.

**Uniform curve:** Horizontal line at $f(x) = 0.1$ from $x = 0$ to $x = 10$. Labeled "$U(0, 10)$."

**Exponential curve:** Starting at $f(0) = 0.1$ and decaying toward zero. Labeled "$\text{Exp}(\mu = 10)$."

**Shaded regions:**
- From 0 to 2: regions under both curves are shaded with different colors.
- Labels: "Uniform: $P(X < 2) = 0.2$" and "Exponential: $P(X < 2) \approx 0.18$" (approximately equal at the beginning).

- From 8 to 10: again shaded.
- Labels: "Uniform: $P(X > 8) = 0.2$" and "Exponential: $P(X > 8) \approx 0.45$" (very different at the tail).

**Caption:** Uniform (constant density) and exponential (decaying density) have the same mean ($\mu = 5$ for uniform, $\mu = 10$ for exponential shown). But the shapes differ dramatically: uniform spreads probability evenly; exponential concentrates probability at small values.

---

## Summary of visual patterns

- **Uniform:** Rectangle. Density is constant. All intervals of equal width have equal probability.
- **Exponential:** Decay curve. Density is highest at zero and decreases exponentially. Short times far more probable than long ones.
- **CDF (Uniform):** Straight line from $(a, 0)$ to $(b, 1)$.
- **CDF (Exponential):** Curve from $(0, 0)$ approaching $(∞, 1)$, concave (curve bending down as it rises).

