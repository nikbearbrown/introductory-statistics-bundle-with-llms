# Pantry — Chapter 6: The Normal Distribution

## Formulas

### Normal probability density function
$$f(x) = \frac{1}{\sigma\sqrt{2\pi}} \cdot e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}$$

Do not memorize. This generates the bell curve shape; its calculus integral gives probabilities.

### Standard notation
$$X \sim N(\mu, \sigma)$$

Read: "X is distributed as normal with mean $\mu$ and standard deviation $\sigma$."

### Z-score (standardization formula)
$$z = \frac{x - \mu}{\sigma}$$

Converts any value from any normal distribution into the standard normal ($N(0,1)$) scale.

### Reverse conversion (from z-score to raw value)
$$x = \mu + z \cdot \sigma$$

Solves for the raw value when you know the z-score, mean, and standard deviation.

## The empirical rule (68-95-99.7)

For any normal distribution $N(\mu, \sigma)$:

- **68%** of data fall within $\mu \pm 1\sigma$ (between $\mu - \sigma$ and $\mu + \sigma$)
- **95%** of data fall within $\mu \pm 2\sigma$ (between $\mu - 2\sigma$ and $\mu + 2\sigma$)
- **99.7%** of data fall within $\mu \pm 3\sigma$ (between $\mu - 3\sigma$ and $\mu + 3\sigma$)

Equivalently, in terms of z-scores:
- 68% of data have $-1 \le z \le 1$
- 95% of data have $-2 \le z \le 2$
- 99.7% of data have $-3 \le z \le 3$

## Standard normal table interpretation

The standard normal table (z-table) shows the area under the curve between $z=0$ and a given z-score value. Because the normal distribution is symmetric:

- Total area under the curve = 1.0
- Area to the left of the mean ($z < 0$) = 0.5
- Area to the right of the mean ($z > 0$) = 0.5
- The table only lists positive z-scores; use symmetry for negative values.

### Example: Using the table

Looking up $z = 1.25$: Find row 1.2 and column 0.05 (for the second decimal). The intersection gives 0.3944. This means:
- The area between $z=0$ and $z=1.25$ is 0.3944.
- The area to the left of $z=1.25$ is $0.5 + 0.3944 = 0.8944$.
- The area to the right of $z=1.25$ is $1 - 0.8944 = 0.1056$.

## Key percentile landmarks (from z-scores)

| z-score | Percentile rank | Interpretation |
|---------|-----------------|---|
| -3 | ~0.1% | Bottom 0.1% |
| -2 | ~2.3% | Bottom ~2% |
| -1 | ~16% | Bottom ~16% |
| 0 | 50% | Median |
| 1 | ~84% | Top ~16% |
| 2 | ~97.5% | Top ~2% |
| 3 | ~99.9% | Top 0.1% |

## Properties of the normal distribution

1. **Symmetric** about the mean. The curve is identical on both sides of $\mu$.
2. **Unimodal**: One peak, at the mean. Mean = Median = Mode.
3. **Bell-shaped**: Concentration near the mean, tapering smoothly to the tails.
4. **Determined by two parameters**: Any normal distribution is fully specified by knowing $\mu$ and $\sigma$.
5. **Continuous**: The curve is smooth; probabilities for specific exact values are zero. We calculate probabilities for *intervals*.
6. **Infinite tails**: The curve approaches but never touches the horizontal axis. Theoretically, any value is possible, though values far from the mean are extremely rare.

## When NOT to use the normal distribution

- Data are **skewed** (not symmetric). Check: if mean ≠ median, suspect skew.
- Data have **multiple modes** (multiple peaks).
- Data have **outliers** that pull away from the central cluster.
- Data are **bounded** (e.g., test scores 0–100) and near the bounds, the distribution may not look normal.
- Sample size is **very small** ($n < 30$), making it hard to assess normality from the histogram.

## Quick reference: Probability calculation steps

### To find $P(X < a)$ where $X \sim N(\mu, \sigma)$:
1. Compute $z = \frac{a - \mu}{\sigma}$.
2. Look up $z$ in the standard normal table.
3. If $z > 0$: Probability = 0.5 + (table value).
4. If $z < 0$: Probability = 0.5 − (table value for $|z|$).

### To find $P(a < X < b)$:
1. Compute $z_1 = \frac{a - \mu}{\sigma}$ and $z_2 = \frac{b - \mu}{\sigma}$.
2. Look up both z-scores.
3. Find $P(X < b)$ and $P(X < a)$.
4. Subtract: $P(a < X < b) = P(X < b) − P(X < a)$.

### To find $P(X > a)$:
1. Find $P(X < a)$ using the steps above.
2. Subtract from 1: $P(X > a) = 1 − P(X < a)$.

## Notation summary

| Symbol | Meaning |
|--------|---------|
| $\mu$ | Population mean |
| $\sigma$ | Population standard deviation |
| $\sigma^2$ | Population variance (standard deviation squared) |
| $X$ | A random variable following a normal distribution |
| $Z$ | A standard normal random variable ($\mu=0, \sigma=1$) |
| $z = \frac{x - \mu}{\sigma}$ | Z-score of a particular value $x$ |
| $N(\mu, \sigma)$ | Notation for a normal distribution with given mean and SD |
| $P(X < a)$ | Probability that X is less than $a$ |
| $P(a < X < b)$ | Probability that X falls between $a$ and $b$ |

## Common z-score values to remember

- $z = 0.67$ ≈ 25th percentile (bottom quartile)
- $z = 1.00$ = 84th percentile
- $z = 1.28$ ≈ 90th percentile
- $z = 1.645$ ≈ 95th percentile
- $z = 1.96$ ≈ 97.5th percentile (used in 95% confidence intervals)
- $z = 2.33$ ≈ 99th percentile

## Connection to other distributions

The normal distribution is used to **approximate** other distributions under certain conditions:

- **Binomial approximation**: When $n$ is large and $p$ is not too close to 0 or 1, and when both $np \geq 5$ and $n(1-p) \geq 5$, a binomial distribution can be approximated by a normal distribution with $\mu = np$ and $\sigma = \sqrt{np(1-p)}$.

---

