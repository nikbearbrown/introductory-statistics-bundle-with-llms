# Pantry — Continuous Random Variables

## Reference formulas

### Fundamental property

For a continuous random variable $X$ with probability density function $f(x)$:

$$P(c < X < d) = \int_c^d f(x)\,dx = \text{area under the curve from } x = c \text{ to } x = d$$

$$P(X = c) = 0 \text{ for any single value } c$$

Total area under $f(x)$ over all possible values equals 1.

---

## Uniform Distribution $X \sim U(a, b)$

**Definition:** A continuous random variable uniformly distributed on the interval $[a, b]$.

**Probability Density Function:**
$$f(x) = \frac{1}{b - a} \quad \text{for } a \leq x \leq b$$

**Mean:**
$$\mu = \frac{a + b}{2}$$

**Standard Deviation:**
$$\sigma = \sqrt{\frac{(b - a)^2}{12}} = \frac{b - a}{2\sqrt{3}}$$

**Cumulative Distribution Function (probability up to $x$):**
$$P(X \leq x) = \frac{x - a}{b - a} \quad \text{for } a \leq x \leq b$$

**Probability of an interval:**
$$P(c < X < d) = \frac{d - c}{b - a} \quad \text{for } a \leq c < d \leq b$$

**Interpretation:** All outcomes in $[a, b]$ are equally likely. The density is constant. Geometric interpretation: probability equals the fraction of the total interval width.

---

## Exponential Distribution $X \sim \text{Exp}(\mu)$ or $X \sim \text{Exp}(m)$

**Definition:** A continuous random variable modeling time (or distance) until the next occurrence of a random event, given that events arrive at a constant average rate.

**Parameters:**
- $\mu$ = mean time between events
- $m = \frac{1}{\mu}$ = decay parameter (rate)

**Probability Density Function:**
$$f(x) = \frac{1}{\mu}e^{-x/\mu} = m e^{-mx} \quad \text{for } x \geq 0$$

**Mean:**
$$\mu = E[X]$$

**Standard Deviation:**
$$\sigma = \mu$$

(Standard deviation equals the mean.)

**Cumulative Distribution Function:**
$$P(X \leq x) = 1 - e^{-x/\mu} = 1 - e^{-mx}$$

**Probability of waiting longer than $x$:**
$$P(X > x) = e^{-x/\mu} = e^{-mx}$$

**Probability of an interval:**
$$P(c < X < d) = e^{-c/\mu} - e^{-d/\mu}$$

**The Memoryless Property:**
$$P(X > r + t \mid X > r) = P(X > t) \quad \text{for all } r \geq 0, t \geq 0$$

This means: if you've already waited $r$ time units, the probability of waiting an additional $t$ units is the same as the unconditional probability of waiting $t$ units from the start.

**Interpretation:** Short times are far more probable than long times. The density is highest at zero and decays exponentially. Use when modeling time until a random event (customer arrival, equipment failure, next earthquake) occurs.

---

## Comparison: Uniform vs. Exponential

| Property | Uniform | Exponential |
|----------|---------|-------------|
| Domain | Finite interval $[a, b]$ | Non-negative $[0, \infty)$ |
| Density shape | Horizontal line (constant) | Decaying curve (highest at 0) |
| Mean | Midpoint: $\frac{a+b}{2}$ | $\mu$ |
| Std Dev | $\frac{b-a}{2\sqrt{3}}$ | $\mu$ (equals the mean) |
| Skewness | Symmetric (0) | Right-skewed (always) |
| Most likely outcome | All equally likely | Zero (mode at origin) |
| When to use | Perfect ignorance in a range | Time until next event |
| Memoryless | No | Yes |

---

## Computation walkthrough

### Uniform: Finding a percentile

**Problem:** $X \sim U(0, 20)$. Find the 60th percentile (value $k$ such that 60% of outcomes are below it).

**Solution:**
$$P(X < k) = 0.60$$
$$\frac{k - 0}{20 - 0} = 0.60$$
$$k = 12$$

**Answer:** The 60th percentile is 12. (60% of the interval $[0, 20]$ lies below 12.)

### Exponential: Probability of an interval

**Problem:** $X \sim \text{Exp}(5)$ (mean is 5). Find $P(2 < X < 8)$.

**Solution:**
$$P(2 < X < 8) = P(X < 8) - P(X < 2)$$
$$= \left(1 - e^{-8/5}\right) - \left(1 - e^{-2/5}\right)$$
$$= e^{-2/5} - e^{-8/5}$$
$$= e^{-0.4} - e^{-1.6}$$
$$\approx 0.6703 - 0.2019 = 0.4684$$

**Answer:** About 47% probability the outcome falls between 2 and 8.

### Exponential: Using the memoryless property

**Problem:** Calls arrive at a help desk with mean time between arrivals of 3 minutes. A call just arrived. Given that no new call has arrived in the past 10 minutes, what's the probability the next call arrives within 2 minutes?

**Setup:** This seems like: "It's been 10 minutes, the mean is 3 minutes—surely a call is imminent." But the exponential is memoryless.

**Solution:**
$$P(X < 10 + 2 \mid X > 10) = P(X < 2) = 1 - e^{-2/3} \approx 1 - 0.5134 = 0.4866$$

**Answer:** About 49% chance. The fact that 10 minutes have passed tells you nothing about what happens next.

---

## Worked examples from the chapter (summary for reference)

### Uniform: Bus waiting time

Bus arrives uniformly over 12 minutes.
- $P(\text{wait} < 3) = 3/12 = 0.25$
- 75th percentile: $k = 9$ minutes
- Mean: $\mu = 6$ minutes

### Exponential: Customer service

Calls arrive with mean 4 minutes between them.
- $P(\text{next call} < 1 \text{ min}) \approx 0.2212$
- $P(\text{next call} > 5 \text{ min}) \approx 0.2865$
- Median wait: $m \approx 2.77$ minutes (less than mean, due to right skew)

---

## Common errors and fixes

**Error:** "The pdf value at a point is the probability at that point."

**Fix:** The pdf is density, not probability. Probability comes from area. For continuous $X$, $P(X = c) = 0$ always, no matter what $f(c)$ is.

---

**Error:** "If $\mu = 10$, I'll wait exactly 10 minutes."

**Fix:** The mean is 10, but the variance is $\mu^2 = 100$ (for exponential). Many outcomes are less than 10, some are much longer. The most likely single outcome (mode) is zero.

---

**Error:** "Memoryless means the distribution changes based on how long you've waited."

**Fix:** Memoryless means it doesn't change. Your future waiting time has the same distribution regardless of past waiting, as if each moment starts a fresh "race" to the next event.

---

## Data patterns that suggest each distribution

### Uniform is plausible when:
- You have no information about where you are in a cycle.
- Outcomes are spread evenly across a defined range.
- You're modeling a baseline "random" scenario.

### Exponential is plausible when:
- You're measuring time until an event (arrival, failure, claim).
- Events arrive at a relatively constant average rate.
- Shorter times are far more common than longer times.
- You observe right-skewed data with many small values and a tail extending right.

