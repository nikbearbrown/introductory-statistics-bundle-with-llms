# Pantry: Chapter 7 — The Central Limit Theorem

## Worked example calculations in detail

### Concept 1, Example: Male heights, standard error

Population: $\mu = 70$ inches, $\sigma = 2.5$ inches
Sample size: $n = 40$ men

Standard error calculation:
$$\sigma_{\bar{x}} = \frac{\sigma}{\sqrt{n}} = \frac{2.5}{\sqrt{40}}$$

$$\sqrt{40} = \sqrt{4 \times 10} = 2\sqrt{10} \approx 6.325$$

$$\sigma_{\bar{x}} = \frac{2.5}{6.325} = 0.395 \text{ inches}$$

Checking with $n = 100$:
$$\sigma_{\bar{x}} = \frac{2.5}{\sqrt{100}} = \frac{2.5}{10} = 0.25 \text{ inches}$$

Ratio: $0.395 / 0.25 = 1.58$, which matches $\sqrt{100/40} = \sqrt{2.5} \approx 1.58$.

---

### Concept 3, Example: SAT scores, probability calculation

Population: $\mu = 1050$, $\sigma = 150$
Sample: $n = 25$ students, $\bar{x} = 1100$

Standard error:
$$\sigma_{\bar{x}} = \frac{150}{\sqrt{25}} = \frac{150}{5} = 30$$

Z-score:
$$z = \frac{1100 - 1050}{30} = \frac{50}{30} = 1.667$$

Using standard normal table or software:
- $P(Z \leq 1.67) = 0.9525$
- $P(Z > 1.67) = 1 - 0.9525 = 0.0475$

So there is a 4.75% chance of observing a sample mean of 1100 or higher if the true population mean is 1050.

---

### Blood pressure medication example (Exercise 6)

Population: $\mu = 140$ mmHg, $\sigma = 15$ mmHg (untreated)
Sample: $n = 100$ patients, $\bar{x} = 135$ mmHg (treated)

Standard error:
$$\sigma_{\bar{x}} = \frac{15}{\sqrt{100}} = \frac{15}{10} = 1.5 \text{ mmHg}$$

Z-score (testing whether the treated mean differs from the untreated population mean):
$$z = \frac{135 - 140}{1.5} = \frac{-5}{1.5} = -3.33$$

Interpretation: The sample mean is 3.33 standard errors *below* the untreated population mean. Using a standard normal table:
- $P(Z \leq -3.33) \approx 0.0004$ (about 0.04%)

This is an extremely strong signal that the medication lowers blood pressure.

---

### GPA estimation example (Exercise 7)

Population SD: $\sigma = 0.4$
Sample 1: $n = 50$ graduates, $\bar{x} = 3.2$ GPA

Standard error:
$$\sigma_{\bar{x}} = \frac{0.4}{\sqrt{50}} = \frac{0.4}{7.071} \approx 0.0566$$

To achieve standard error of 0.025:
$$0.025 = \frac{0.4}{\sqrt{n}}$$

$$\sqrt{n} = \frac{0.4}{0.025} = 16$$

$$n = 256$$

Verification: $\sigma_{\bar{x}} = \frac{0.4}{\sqrt{256}} = \frac{0.4}{16} = 0.025$. ✓

---

### Espresso machine example (Exercise 4)

Population: $\mu = 2$ ounces, $\sigma = 0.1$ ounces
Sample: $n = 30$ shots

Standard error:
$$\sigma_{\bar{x}} = \frac{0.1}{\sqrt{30}} = \frac{0.1}{5.477} \approx 0.0183$$

Lower bound: $\bar{x} = 1.98$ ounces
$$z = \frac{1.98 - 2.0}{0.0183} = \frac{-0.02}{0.0183} = -1.09$$

Upper bound: $\bar{x} = 2.02$ ounces
$$z = \frac{2.02 - 2.0}{0.0183} = \frac{0.02}{0.0183} = 1.09$$

Using standard normal table:
- $P(Z \leq 1.09) \approx 0.8621$
- $P(Z \leq -1.09) \approx 0.1379$
- $P(-1.09 \leq Z \leq 1.09) = 0.8621 - 0.1379 = 0.7242$ or 72.4%

---

## Standard normal table values used in examples

| z-score | Cumulative P(Z ≤ z) |
|---------|---------------------|
| 1.09    | 0.8621              |
| 1.50    | 0.9332              |
| 1.67    | 0.9525              |
| 3.33    | 0.9996              |

---

## Key formulas summary

**Mean of sampling distribution of sample means:**
$$\mu_{\bar{x}} = \mu$$

**Standard error of the mean:**
$$\sigma_{\bar{x}} = \frac{\sigma}{\sqrt{n}}$$

**Z-score for sample mean:**
$$z = \frac{\bar{x} - \mu}{\sigma/\sqrt{n}}$$

**Central Limit Theorem statement:**
$$\bar{x} \sim N\left(\mu, \frac{\sigma}{\sqrt{n}}\right)$$

**Law of Large Numbers (informal):**
$$\bar{x} \to \mu \text{ as } n \to \infty$$

---

## Simulation data: Understanding the CLT visually

The CLT is best understood by simulation. Here is what happens when you repeatedly sample from different distributions:

### Normal population (original distribution already normal)
- Sample size $n = 10$: Sampling distribution looks normal immediately. ✓
- Sample size $n = 25$: Indistinguishable from perfect normal.
- Conclusion: If population is normal, CLT applies exactly even for small $n$.

### Uniform population (completely flat, symmetric)
- Sample size $n = 10$: Sampling distribution shows some edge-effects; not quite normal yet.
- Sample size $n = 25$: Looks normal; the edges are smoothed.
- Sample size $n = 50$: Nearly perfect normal.
- Conclusion: For symmetric distributions, $n \approx 20$–25 is sufficient.

### Exponential population (highly right-skewed)
- Sample size $n = 10$: Sampling distribution is noticeably skewed.
- Sample size $n = 30$: Closer to normal but still slightly skewed.
- Sample size $n = 50$: Very close to normal.
- Sample size $n = 100$: Virtually indistinguishable from normal.
- Conclusion: For skewed distributions, $n \geq 50$ is often prudent.

The rule of thumb "$n \geq 30$" works for most practical distributions but is conservative for symmetric ones and optimistic for very skewed ones.

---

## Common standard errors (quick reference)

For a population with $\sigma = 10$:

| Sample size | Standard error |
|-------------|----------------|
| $n = 4$     | 5.00          |
| $n = 9$     | 3.33          |
| $n = 16$    | 2.50          |
| $n = 25$    | 2.00          |
| $n = 36$    | 1.67          |
| $n = 49$    | 1.43          |
| $n = 64$    | 1.25          |
| $n = 100$   | 1.00          |
| $n = 400$   | 0.50          |

Observe: To halve the standard error, you must quadruple the sample size.

---

## Historical note: John Kerrich's coin flip experiment

John Kerrich was a Danish-born mathematician imprisoned in an internment camp during World War II (1940–1945). With time on his hands and a single coin, he flipped it 10,000 times and recorded the results.

Results:
- Expected number of heads (if fair): 5,000
- Actual number of heads: 5,067
- Difference: 67
- Proportion of heads: 5,067 / 10,000 = 0.5067

The proportion 0.5067 is extremely close to the theoretical 0.5. The sample mean converges to the population mean (Law of Large Numbers) and follows a normal distribution (CLT)—exactly as the theory predicts.

This is one of the most famous empirical confirmations of the CLT in statistics education.

---

## Data for manufacturing example

A manufacturer produces 25-pound weights. Due to normal variation in the casting process:
- Actual weight range: 24 to 26 pounds
- Distribution: uniform (equally likely anywhere in this range)
- Mean: $\mu = 25$ pounds
- Standard deviation (for uniform): $\sigma = \frac{26 - 24}{2\sqrt{3}} = \frac{2}{2\sqrt{3}} = \frac{1}{\sqrt{3}} \approx 0.5774$ pounds

Sample of 100 weights:
- Standard error: $\sigma_{\bar{x}} = \frac{0.5774}{\sqrt{100}} = 0.05774$ pounds
- The sampling distribution of the mean is approximately normal with mean 25 and SE 0.058.

Example question: What is $P(\bar{x} < 24.9)$?

$$z = \frac{24.9 - 25}{0.05774} = \frac{-0.1}{0.05774} \approx -1.73$$

$$P(Z < -1.73) \approx 0.0418 \text{ or } 4.18\%$$

So there is about a 4% chance the sample mean falls below 24.9 pounds.
