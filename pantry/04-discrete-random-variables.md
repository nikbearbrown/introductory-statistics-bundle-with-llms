# Pantry — Chapter 4: Discrete Random Variables

## Formulas at a glance

### Random Variables and PMF

**Probability mass function (PMF):** $P(X = x)$ or $P(x)$ — the probability that discrete random variable $X$ takes the value $x$.

**Validity conditions:**
- $0 \leq P(x) \leq 1$ for all $x$
- $\sum P(x) = 1$

### Expected Value and Variance

**Expected value (mean):** 
$$E(X) = \mu = \sum x \cdot P(x)$$

**Variance:** 
$$\text{Var}(X) = \sigma^2 = \sum (x - \mu)^2 \cdot P(x)$$

**Standard deviation:** 
$$\sigma = \sqrt{\sigma^2}$$

Alternative formula for variance (easier for computation):
$$\sigma^2 = E(X^2) - [E(X)]^2 = \sum x^2 \cdot P(x) - \mu^2$$

### Binomial Distribution

**Conditions:**
- Fixed number of trials: $n$
- Two outcomes per trial: success (probability $p$) or failure (probability $q = 1 - p$)
- Constant $p$ across trials
- Independent trials

**Probability mass function:**
$$P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$$

where $\binom{n}{k} = \frac{n!}{k!(n-k)!}$ (read "$n$ choose $k$")

**Mean:** $\mu = np$

**Variance:** $\sigma^2 = np(1-p)$

**Standard deviation:** $\sigma = \sqrt{np(1-p)}$

**Notation:** $X \sim \text{Binomial}(n, p)$

### Poisson Distribution

**Conditions:**
- Events occur at a constant average rate $\mu$ per interval (time or space)
- Events are independent
- Events are rare relative to the interval

**Probability mass function:**
$$P(X = k) = \frac{\mu^k e^{-\mu}}{k!}$$

where $e \approx 2.71828$ (Euler's number)

**Mean:** $\mu$

**Variance:** $\sigma^2 = \mu$

**Standard deviation:** $\sigma = \sqrt{\mu}$

**Notation:** $X \sim \text{Poisson}(\mu)$

**Poisson as a limit of binomial:** If $n$ is large, $p$ is small, and $np = \mu$ is moderate, then $\text{Binomial}(n, p) \approx \text{Poisson}(\mu)$.

---

## Key definitions

**Binomial experiment:** A statistical experiment where you perform $n$ independent trials, each with two outcomes (success/failure), and the probability of success $p$ is constant across trials.

**Bernoulli trial:** A single trial with two outcomes (success/failure) and constant probability $p$.

**Combinatorial formula:** $\binom{n}{k} = \frac{n!}{k!(n-k)!}$. Gives the number of ways to choose $k$ items from $n$ items (unordered).

**Discrete random variable:** A random variable that takes on countable values, usually whole numbers (e.g., 0, 1, 2, 3, ...).

**Expected value:** The long-run average of a random variable across many repetitions. $E(X) = \mu$.

**Factorial:** $n! = n \cdot (n-1) \cdot (n-2) \cdots 1$. By definition, $0! = 1$.

**Poisson distribution:** A discrete probability distribution modeling the number of rare events occurring at a constant average rate in a fixed interval.

**Probability mass function (PMF):** A function giving the probability that a discrete random variable takes a specific value.

**Random variable:** A rule assigning a number to each outcome of an experiment.

**Variance:** The average squared distance from data points to the mean. Measures spread. $\sigma^2 = \text{Var}(X)$.

---

## Common computational patterns

### Computing binomial probabilities by hand

1. **Identify $n$, $p$, and $k$ (the number of successes you're interested in).**

2. **Compute $\binom{n}{k}$:**
   - $\binom{n}{k} = \frac{n!}{k!(n-k)!}$
   - For small $n$, compute factorials. For large $n$, use a calculator or software.

3. **Compute $p^k$ and $(1-p)^{n-k}$.**

4. **Multiply: $P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$.**

5. **For cumulative probabilities (e.g., $P(X \leq k)$ or $P(X \geq k)$), sum the individual probabilities:**
   - $P(X \leq k) = \sum_{i=0}^{k} P(X = i)$
   - $P(X \geq k) = \sum_{i=k}^{n} P(X = i)$
   - Or use the complement: $P(X \geq k) = 1 - P(X \leq k - 1)$

### Computing Poisson probabilities by hand

1. **Identify $\mu$ (the expected number of events in the interval) and $k$ (the number you're interested in).**

2. **Compute $\mu^k$ and $e^{-\mu}$.**
   - $e^{-\mu}$ is found on a calculator (often written as $\exp(-\mu)$ or $e^{-\mu}$).
   - For $\mu = 1$, $e^{-1} \approx 0.3679$.
   - For $\mu = 2$, $e^{-2} \approx 0.1353$.
   - For $\mu = 5$, $e^{-5} \approx 0.0067$.

3. **Compute $k!$.**

4. **Compute $P(X = k) = \frac{\mu^k e^{-\mu}}{k!}$.**

5. **For cumulative probabilities, sum individual probabilities.**

### Computing expected value and variance

**From a probability distribution:**

| $x$ | $P(x)$ |
|---|---|
| $x_1$ | $p_1$ |
| $x_2$ | $p_2$ |
| $\vdots$ | $\vdots$ |

1. **Expected value:** $E(X) = x_1 p_1 + x_2 p_2 + \cdots$

2. **Variance (direct formula):**
   - Compute $(x_i - E(X))^2$ for each $i$.
   - $\text{Var}(X) = (x_1 - E(X))^2 p_1 + (x_2 - E(X))^2 p_2 + \cdots$

3. **Variance (shortcut):**
   - $E(X^2) = x_1^2 p_1 + x_2^2 p_2 + \cdots$
   - $\text{Var}(X) = E(X^2) - [E(X)]^2$

4. **Standard deviation:** $\sigma = \sqrt{\text{Var}(X)}$

**For binomial:** $E(X) = np$, $\text{Var}(X) = np(1-p)$, $\sigma = \sqrt{np(1-p)}$

**For Poisson:** $E(X) = \mu$, $\text{Var}(X) = \mu$, $\sigma = \sqrt{\mu}$

---

## Worked examples (detailed solutions)

### Example 1: Binomial — Defect testing

**Problem:** A quality engineer inspects 20 items. The defect rate is 5%. What is the probability that at most 2 items are defective?

**Solution:**

Binomial with $n = 20$, $p = 0.05$, $q = 0.95$.

$P(X \leq 2) = P(X = 0) + P(X = 1) + P(X = 2)$

$P(X = 0) = \binom{20}{0} (0.05)^0 (0.95)^{20} = 1 \cdot 1 \cdot 0.3585 = 0.3585$

$P(X = 1) = \binom{20}{1} (0.05)^1 (0.95)^{19} = 20 \cdot 0.05 \cdot 0.3773 = 0.3774$

$P(X = 2) = \binom{20}{2} (0.05)^2 (0.95)^{18} = 190 \cdot 0.0025 \cdot 0.3974 = 0.1887$

$P(X \leq 2) = 0.3585 + 0.3774 + 0.1887 = 0.9246$

**Interpretation:** There's about a 92.5% chance that at most 2 items out of 20 are defective, assuming the 5% defect rate holds.

### Example 2: Poisson — Arrivals at a clinic

**Problem:** A clinic receives patient walk-ins at an average rate of 4 per hour. What is the probability that the clinic receives more than 6 walk-ins in the next hour?

**Solution:**

Poisson with $\mu = 4$.

$P(X > 6) = 1 - P(X \leq 6) = 1 - [P(X=0) + P(X=1) + \cdots + P(X=6)]$

Individual probabilities:
- $P(X=0) = \frac{4^0 e^{-4}}{0!} = \frac{1 \cdot 0.0183}{1} = 0.0183$
- $P(X=1) = \frac{4^1 e^{-4}}{1!} = \frac{4 \cdot 0.0183}{1} = 0.0733$
- $P(X=2) = \frac{4^2 e^{-4}}{2!} = \frac{16 \cdot 0.0183}{2} = 0.1465$
- $P(X=3) = \frac{4^3 e^{-4}}{3!} = \frac{64 \cdot 0.0183}{6} = 0.1954$
- $P(X=4) = \frac{4^4 e^{-4}}{4!} = \frac{256 \cdot 0.0183}{24} = 0.1954$
- $P(X=5) = \frac{4^5 e^{-4}}{5!} = \frac{1024 \cdot 0.0183}{120} = 0.1563$
- $P(X=6) = \frac{4^6 e^{-4}}{6!} = \frac{4096 \cdot 0.0183}{720} = 0.1042$

$P(X \leq 6) = 0.0183 + 0.0733 + 0.1465 + 0.1954 + 0.1954 + 0.1563 + 0.1042 = 0.8894$

$P(X > 6) = 1 - 0.8894 = 0.1106$

**Interpretation:** There's about an 11% chance of more than 6 walk-ins in an hour. The clinic should plan to handle peaks of 6–8 patients comfortably.

### Example 3: Recognizing the distribution

**Problem:** A hospital tracks medication errors. Chart review of 100 patient records found 3 errors. Over the past year, the hospital processes 50,000 medication administrations. Estimate the probability of observing 0 medication errors in a random sample of 100 administrations.

**Solution:**

The error rate is $p = 3/100 = 0.03$. If we draw a sample of 100, this is binomial with $n = 100$, $p = 0.03$.

But $n$ is large and $p$ is small, so we can use the Poisson approximation with $\mu = np = 100 \cdot 0.03 = 3$.

$P(X = 0) = \frac{3^0 e^{-3}}{0!} = \frac{1 \cdot 0.0498}{1} = 0.0498$

**Interpretation:** There's about a 5% chance of zero errors in the next 100 administrations. Most of the time (95% of samples of 100), we'd expect at least one error.

---

## Factorial table (for reference)

| $n$ | $n!$ |
|---|---|
| 0 | 1 |
| 1 | 1 |
| 2 | 2 |
| 3 | 6 |
| 4 | 24 |
| 5 | 120 |
| 6 | 720 |
| 7 | 5,040 |
| 8 | 40,320 |
| 9 | 362,880 |
| 10 | 3,628,800 |

---

## Binomial tables (partial)

**For $P(X = k)$ with $n = 10$, selected values of $p$:**

| $k$ | $p = 0.10$ | $p = 0.25$ | $p = 0.50$ | $p = 0.75$ |
|---|---|---|---|---|
| 0 | 0.3487 | 0.0563 | 0.0010 | 0.0000 |
| 1 | 0.3874 | 0.1877 | 0.0098 | 0.0000 |
| 2 | 0.1937 | 0.2816 | 0.0439 | 0.0004 |
| 3 | 0.0574 | 0.2503 | 0.1172 | 0.0031 |
| 4 | 0.0112 | 0.1460 | 0.2051 | 0.0162 |
| 5 | 0.0015 | 0.0584 | 0.2461 | 0.0584 |

(For full tables, consult a statistics textbook or use software.)

---

## When to use each distribution

| Distribution | When to use | Key parameters |
|---|---|---|
| **Binomial** | Fixed number of independent trials, two outcomes per trial, constant success probability | $n$ (number of trials), $p$ (probability of success) |
| **Poisson** | Rare events in a fixed interval (time or space), events independent and at constant average rate | $\mu$ (average rate per interval) |
| **Hypergeometric** | Sampling without replacement from a finite population with two categories | $N$ (population size), $K$ (number of "successes" in population), $n$ (sample size) |

(Hypergeometric is deferred to Chapter 4 Appendix; we focus on binomial and Poisson in the main chapter.)

---

## R/Python snippets for calculation

### R

```r
# Binomial probabilities
dbinom(k, n, p)       # P(X = k)
pbinom(k, n, p)       # P(X <= k)
1 - pbinom(k-1, n, p) # P(X >= k)

# Poisson probabilities
dpois(k, mu)          # P(X = k)
ppois(k, mu)          # P(X <= k)
1 - ppois(k, mu)      # P(X > k)

# Example: P(X = 3) with binomial n=20, p=0.05
dbinom(3, 20, 0.05)

# Example: P(X <= 5) with Poisson mu=4
ppois(5, 4)
```

### Python

```python
from scipy.stats import binom, poisson

# Binomial probabilities
binom.pmf(k, n, p)    # P(X = k)
binom.cdf(k, n, p)    # P(X <= k)

# Poisson probabilities
poisson.pmf(k, mu)    # P(X = k)
poisson.cdf(k, mu)    # P(X <= k)

# Example: P(X = 3) with binomial n=20, p=0.05
binom.pmf(3, 20, 0.05)

# Example: P(X <= 5) with Poisson mu=4
poisson.cdf(5, 4)
```

