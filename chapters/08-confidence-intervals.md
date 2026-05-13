# Chapter 8 — Confidence Intervals

## Three title options

1. **From One Sample to a Range: How we estimate what we don't know, and know how often we're right**
2. **The honest guess: Why a number plus or minus a margin tells you more than the number alone**
3. **Building bounds from randomness: Confidence intervals, from drug trials to polling**

---

## TL;DR

A confidence interval is a range of values—not a single guess—that we build from sample data to estimate a population parameter. The trade-off is always the same: wider intervals hold more confidence; narrower ones are more precise. You choose the level of confidence first. Then the math tells you the range. The key insight: 95% confidence does not mean "there's a 95% chance the parameter is in this interval." It means "95% of all intervals built this way will contain the true parameter." You'll understand that distinction by the end of this chapter, and it will change how you read every margin of error you encounter.

---

## Cold open: The moment the poll lands on your front door

Tuesday, 6:17 p.m. A woman on the phone says she's conducting a survey for the county health department. She asks: "In the last month, how many days would you say your mental health was not good?" You pause. You guess seven days. She thanks you and hangs up.

On the other end, 499 people have answered the same question. One caller said three days. Another said thirty. The median response is nine days. The woman writing the report knows the true population mean—the average across every resident in the county—is hidden from her. She will never know it exactly. But she can build a range.

She calculates the sample mean: 10.2 days. The sample standard deviation: 6.8 days. Then she does the math. She reports to her supervisor: "We estimate with 95% confidence that the true county average is between 9.3 and 11.1 days."

This is statistics doing what it was invented to do: turning one sample into a guess about the whole population, and telling you honestly how confident that guess is.

### Learning objectives

By the end of this chapter you will be able to:

- **Construct and interpret** confidence intervals for a population mean when the population standard deviation is known (using the z-distribution).
- **Construct and interpret** confidence intervals for a population mean when the population standard deviation is unknown (using the t-distribution), and **explain** why the interval gets wider.
- **Construct and interpret** confidence intervals for a population proportion and **identify** when the normal approximation is valid.
- **Calculate** sample size to achieve a desired margin of error at a specified confidence level.
- **Distinguish** the confidence level (a property of the procedure) from the probability statement about the parameter (which makes no sense once the interval is built).

### Prerequisites

Comfort with the central limit theorem. Ability to read and use a standard normal table and a t-table. Algebra with fractions and square roots. Understanding that $\mu$ denotes the population mean and $\bar{x}$ denotes the sample mean.

### Why this chapter matters

Every estimate you read that includes a margin of error—every poll, every drug trial result, every survey—is built on the ideas in this chapter. Politicians use confidence intervals to decide which candidate to support. Pharmaceutical companies use them to report whether a drug works. Your doctor reads them to know whether a treatment is safe. This chapter teaches you to build them yourself and to read them with the skepticism they deserve.

The margin of error is not magic. It's mathematics. And like all mathematics, it only works if you understand what you're measuring and what your assumptions are.

---

## Concept 1 — From point to range: Why one number is never enough

**Cold open: The Apple Music question**

A music-streaming company wants to know the average number of songs its users download per month. They survey 100 random users. The sample mean is 2.1 songs. So they report: "Our users download an average of 2.1 songs per month."

But the next month, a different sample of 100 users shows a sample mean of 1.9 songs. Did the true average drop? Or is this just randomness—the natural bounce that happens when you sample?

The company needs a different kind of estimate. Not a single number—called a **point estimate**. A range that acknowledges uncertainty. A **confidence interval** — that's the range of plausible values we have *confidence* (meaning long-run frequency, not probability) in, built from the sample data and expressed as $\text{point estimate} \pm \text{margin of error}$.

### The machinery: from the central limit theorem to a formula

The central limit theorem promised us this: if you draw repeated samples of size $n$ from a population with mean $\mu$ and standard deviation $\sigma$, the sample means follow a normal distribution with mean $\mu$ and standard deviation $\sigma / \sqrt{n}$ (the *standard error*).

So if we know $\sigma$, we can use the normal distribution to ask: what range captures 95% of all sample means?

The z-score formula tells us: for any value $z^*$, the range from $-z^*$ to $+z^*$ under the standard normal curve captures a certain percentage of the data.

- $z^* = 1.645$ captures 90% (35% on each side of the mean, since 0.45 + 0.45 = 0.90).
- $z^* = 1.96$ captures 95%.
- $z^* = 2.576$ captures 99%.

Now here's the key move. If $z^*$ captures 95% of sample means, and our sample mean $\bar{x}$ is within that band of the true mean, then the true mean $\mu$ is within $\bar{x} \pm z^* \cdot \sigma/\sqrt{n}$.

This is the confidence interval for a population mean, $\sigma$ known:

$$\bar{x} - z^* \cdot \frac{\sigma}{\sqrt{n}} \leq \mu \leq \bar{x} + z^* \cdot \frac{\sigma}{\sqrt{n}}$$

Or written more compactly:

$$\mu = \bar{x} \pm z^* \cdot \frac{\sigma}{\sqrt{n}}$$

**A gloss on the terms:** The quantity $z^*$ is the critical value — the z-score that marks the boundary of your desired confidence level. The quantity $\frac{\sigma}{\sqrt{n}}$ is the standard error (the standard deviation of the sampling distribution). Their product, $z^* \cdot \frac{\sigma}{\sqrt{n}}$, is the margin of error or error bound (EBM).

### The critical misunderstanding

Once you build a confidence interval, say $(1.8, 2.4)$, the interval is fixed. The parameter $\mu$ is also fixed. It's either in the interval or it's not.

So it makes no sense to say: "There's a 95% probability that $\mu$ is in this interval."

What 95% confidence means is this: if you repeated the sampling and interval-building procedure 100 times, about 95 of those intervals would contain the true parameter. The confidence is in the *procedure*, not in *this particular interval*.

This distinction saves you from a common trap: a student builds a 95% CI and thinks "I'm 95% sure the true mean is in this range." But you could be one of the 5 unlucky samples whose interval missed entirely. You'll never know.

### Worked example — Apple Music downloads, confidence interval with known σ

Suppose the population standard deviation of monthly downloads is known to be $\sigma = 1$ song (the company studied this years ago). A sample of 100 users gives $\bar{x} = 2.0$. Build a 95% confidence interval for the true population mean.

**Step 1:** Identify the given values.
- $\bar{x} = 2.0$
- $\sigma = 1$
- $n = 100$
- Confidence level 95%, so $z^* = 1.96$

**Step 2:** Calculate the standard error.

$$SE = \frac{\sigma}{\sqrt{n}} = \frac{1}{\sqrt{100}} = \frac{1}{10} = 0.1$$

**Step 3:** Calculate the margin of error.

$$EBM = z^* \cdot SE = 1.96 \cdot 0.1 = 0.196$$

**Step 4:** Build the interval.

$$\bar{x} - EBM \leq \mu \leq \bar{x} + EBM$$

$$2.0 - 0.196 \leq \mu \leq 2.0 + 0.196$$

$$1.804 \leq \mu \leq 2.196$$

**Interpretation:** We are 95% confident that the true average number of songs downloaded per month is between 1.8 and 2.2.

**What this means procedurally:** If the company repeated this survey 100 times with 100 new random samples, about 95 of the resulting intervals would contain the true population mean. The company never knows whether this particular interval did.

### Common misconceptions

**"95% confidence means there's a 95% chance the parameter is in the interval."** No. Once the interval is built, the parameter is either in it or not—probability doesn't apply. The 95% applies to the long-run frequency of the procedure.

**"A larger sample makes the interval narrower."** True. But only because a larger sample reduces the standard error. The math directly shows this: the standard error is $\sigma / \sqrt{n}$. As $n$ grows, the denominator grows, the fraction shrinks, and the margin of error shrinks.

**"The confidence level and the sample size do opposite things to interval width."** Not quite. A higher confidence level (say 99% instead of 95%) uses a larger $z^*$, which widens the interval. A larger sample size shrinks $1/\sqrt{n}$, which narrows it. They're independent levers.

---

## Concept 2 — When you don't know σ: The t-distribution and Student's story

**Cold open: William Gossett's problem**

It's 1908. William Gossett works at the Guinness brewery in Dublin. He runs small experiments on hops and barley—the crops that make beer. His sample sizes are always small: five, ten, maybe fifteen samples. He wants to estimate the mean quality of his barley batches from these tiny samples.

He calculates confidence intervals using the normal distribution. But they keep failing him. When he repeated an experiment, the true parameter fell outside his interval far more often than 5% of the time. The normal approximation wasn't working for small samples.

The problem: when you don't know the population standard deviation $\sigma$ and your sample is small, you substitute the sample standard deviation $s$ into the formula. But $s$ is itself random. It bounces around more than $\sigma$. Using the normal distribution to pretend $s$ is constant introduces error you can't ignore.

Gossett figured out the right distribution. It has heavier tails than the normal—it lets the interval get wider to account for the extra uncertainty. He published his discovery in 1908 under the pen name "A Student." The distribution is now called the **Student's t-distribution**.

### The t-distribution: Normal's more cautious cousin

The t-distribution is defined by one parameter: the **degrees of freedom** (df), which equals $n - 1$ for this application.

Why $n - 1$? When you calculate a sample standard deviation, you compute $n$ deviations from the sample mean. But the deviations sum to zero by definition. So the last deviation is determined by the first $n-1$. Only $n-1$ deviations are *free to vary*. Hence $n-1$ degrees of freedom.

The t-distribution has these properties:

- **It's symmetric** around zero, just like the normal distribution.
- **It has heavier tails.** More probability sits in the tails than in the normal. This is why the confidence intervals get wider.
- **As df increases (n gets larger), the t-distribution converges to the normal distribution.** At $df = \infty$, a t-value and a z-value are identical. At $df = 30$, they're very close. This is why many textbooks say "use t for $n < 30$ and z for $n \geq 30$"—the distributions are similar enough by that point that the distinction doesn't matter much in practice.

### The confidence interval formula with unknown σ

When the population standard deviation is unknown and you substitute the sample standard deviation $s$:

$$\mu = \bar{x} \pm t_{df, \alpha/2} \cdot \frac{s}{\sqrt{n}}$$

where $df = n - 1$, and $t_{df, \alpha/2}$ is the critical value from the t-table at $df = n-1$ and your chosen confidence level.

Notice the parallel to the z-formula. The only differences are: $s$ replaces $\sigma$, and $t_{df, \alpha/2}$ replaces $z^*$. Everything else—the logic, the structure, the interpretation—is identical.

### The t-table and how to use it

A t-table shows t-critical values by degrees of freedom (rows) and confidence level (columns, or sometimes as $\alpha$ or $\alpha/2$).

Suppose you have a sample of $n = 10$ and want a 95% confidence interval.

- $df = n - 1 = 9$
- For 95% confidence, $\alpha = 0.05$, so $\alpha/2 = 0.025$ (you split the 5% failure rate evenly into the two tails)
- Look at row 9, column 0.025
- The value is $t_{9, 0.025} = 2.262$

This means you extend 2.262 standard errors on each side of the sample mean.

### Worked example — Dow Jones Industrial Average, CEO earnings per share

A financial analyst randomly samples 10 stocks from the DJIA. Their earnings per share (EPS): $\bar{x} = 1.85$ with sample standard deviation $s = 0.395$. Build a 99% confidence interval for the true mean EPS of all DJIA industrials.

**Step 1:** Identify the given values.
- $\bar{x} = 1.85$
- $s = 0.395$
- $n = 10$, so $df = 9$
- Confidence level 99%, so $\alpha = 0.01$, $\alpha/2 = 0.005$
- From the t-table: $t_{9, 0.005} = 3.250$

**Step 2:** Calculate the standard error.

$$SE = \frac{s}{\sqrt{n}} = \frac{0.395}{\sqrt{10}} = \frac{0.395}{3.162} = 0.1249$$

**Step 3:** Calculate the margin of error.

$$EBM = t_{df, \alpha/2} \cdot SE = 3.250 \cdot 0.1249 = 0.406$$

**Step 4:** Build the interval.

$$\bar{x} - EBM \leq \mu \leq \bar{x} + EBM$$

$$1.85 - 0.406 \leq \mu \leq 1.85 + 0.406$$

$$1.444 \leq \mu \leq 2.256$$

**Interpretation:** We are 99% confident that the true mean EPS of all DJIA industrial stocks is between \$1.44 and \$2.26.

### Trade-offs: Why t-intervals are wider than z-intervals

Compare two scenarios. A sample of 20 gives $\bar{x} = 100$ and $s = 10$.

Using z (if we pretended we knew $\sigma = 10$):
- $z^* = 1.96$ (95% confidence)
- $SE = 10/\sqrt{20} = 2.236$
- $EBM = 1.96 \cdot 2.236 = 4.38$
- Interval: $(95.62, 104.38)$, width 8.76

Using t (since we actually don't know $\sigma$):
- $df = 19$, $t_{19, 0.025} = 2.093$
- $SE = 10/\sqrt{20} = 2.236$
- $EBM = 2.093 \cdot 2.236 = 4.68$
- Interval: $(95.32, 104.68)$, width 9.36

The t-interval is 0.6 units wider. Gossett's insight: this extra width is the honest price of not knowing $\sigma$. You buy safety.

### Common misconceptions

**"t is for small samples; z is for large samples."** More precisely: use t whenever you don't know $\sigma$. When $n \geq 30$ and you don't know $\sigma$, the t-interval and a z-interval using $s$ are so similar that many practitioners treat them as interchangeable. But t is the theoretically correct choice.

**"Degrees of freedom is just n."** No. It's $n - 1$ because one degree of freedom is "spent" calculating the sample standard deviation.

**"The t-table has infinitely many rows."** The table usually ends at $df = 30$ or $df = 40$, then jumps to $df = \infty$. The row for $\infty$ gives the z-values. This is where you see that $t_{\infty, 0.025} = 1.96 = z^*$.

---

## Concept 3 — Proportions: From binomial to normal to confidence

**Cold open: The poll published the morning of the election**

Election day. A news outlet publishes their final poll: "In a sample of 1,200 likely voters, 52% say they will vote for Candidate A. Margin of error: ±3 percentage points, 95% confidence."

What does "52% ± 3%" mean? It means the outlet estimates the true proportion of all voters who support Candidate A is between 49% and 55%. If 49% of the true population supports A, Candidate A loses. At 51%, it's a toss-up. At 55%, it's a landslide. The same sample, but the range determines the narrative.

### Sample proportion: the point estimate

Let $p$ denote the true population proportion (the proportion of all voters who support Candidate A). We never know $p$ exactly. But from a sample of $n$ voters, we can calculate $\hat{p}$ (read "p-hat"), the **sample proportion**:

$$\hat{p} = \frac{x}{n}$$

where $x$ is the number of successes (voters who support A) and $n$ is the sample size.

This $\hat{p}$ is our point estimate of $p$.

### The sampling distribution of the sample proportion

By the central limit theorem, if $n$ is large enough, the sample proportion $\hat{p}$ is approximately normal with:

- Mean: $\mu_{\hat{p}} = p$
- Standard deviation: $\sigma_{\hat{p}} = \sqrt{\frac{p(1-p)}{n}}$

**The condition for validity:** Both $np$ and $n(1-p)$ must be at least 5. If 52% of 1,200 support A, then $np = 1200 \cdot 0.52 = 624$ and $n(1-p) = 1200 \cdot 0.48 = 576$. Both exceed 5. The normal approximation is valid.

### The confidence interval for a population proportion

$$\hat{p} = p \pm z^* \sqrt{\frac{\hat{p}(1 - \hat{p})}{n}}$$

Or written as a range:

$$\hat{p} - z^* \sqrt{\frac{\hat{p}(1 - \hat{p})}{n}} \leq p \leq \hat{p} + z^* \sqrt{\frac{\hat{p}(1 - \hat{p})}{n}}$$

**Notice:** We substitute $\hat{p}$ for the unknown $p$ in the standard deviation formula, because we don't know $p$. This is analogous to using $s$ instead of $\sigma$ for means. The margin of error again follows the familiar pattern: $z^* \cdot SE$.

### Worked example — Smartphone ownership in a large city

A market research firm surveys 500 randomly selected adults in a large city. Of them, 421 own a smartphone. Build a 95% confidence interval for the true proportion of adults in the city who own smartphones.

**Step 1:** Check the condition and identify the given values.
- $n = 500$
- $x = 421$ (number who own smartphones)
- $\hat{p} = 421/500 = 0.842$
- $\hat{q} = 1 - \hat{p} = 0.158$
- Check: $np = 500 \cdot 0.842 = 421 \geq 5$ ✓ and $n(1-p) = 500 \cdot 0.158 = 79 \geq 5$ ✓
- Confidence level 95%, so $z^* = 1.96$

**Step 2:** Calculate the standard error.

$$SE = \sqrt{\frac{\hat{p}(1 - \hat{p})}{n}} = \sqrt{\frac{0.842 \cdot 0.158}{500}} = \sqrt{\frac{0.133}{500}} = \sqrt{0.000266} = 0.0163$$

**Step 3:** Calculate the margin of error.

$$EBM = z^* \cdot SE = 1.96 \cdot 0.0163 = 0.0319 \approx 0.032$$

**Step 4:** Build the interval.

$$\hat{p} - EBM \leq p \leq \hat{p} + EBM$$

$$0.842 - 0.032 \leq p \leq 0.842 + 0.032$$

$$0.810 \leq p \leq 0.874$$

**Interpretation:** We are 95% confident that between 81.0% and 87.4% of all adults in the city own smartphones.

### Trade-off: Proportions at the extreme

A quirk of proportions: the standard error $\sqrt{\hat{p}(1-\hat{p})/n}$ is largest when $\hat{p} = 0.5$. At the extremes (say $\hat{p} = 0.1$ or $\hat{p} = 0.9$), the standard error shrinks, and so does the margin of error.

This makes intuitive sense. If 95% of a sample owns a smartphone, you're more confident about that number than if 50% own one. The 50-50 split has the most uncertainty.

### Common misconceptions

**"The normal approximation always works for proportions."** Only if $np \geq 5$ and $n(1-p) \geq 5$. Small samples with extreme proportions (like 2 successes out of 5 trials) require exact binomial methods, not the normal approximation.

**"Proportions are easier than means."** Proportions require one fewer calculation (no degrees of freedom, so always use z), but they have the strict condition on the sample size and the validity threshold. Neither is universally easier.

**"The confidence interval for a proportion is always symmetric around $\hat{p}$."** Yes, it is—because we're using the normal approximation. (There are other methods, like the Wilson score interval, that produce asymmetric intervals, but they're beyond this course.)

---

## Integration — Confidence, precision, and the sample size question

Return to the polling company from the chapter opening. They want to estimate the true proportion of county residents who report poor mental health within a margin of error of ±2.5 percentage points, at 95% confidence. How many people do they need to survey?

This is the **sample size formula**. It comes from rearranging the margin of error formula.

For a population proportion:

$$n = \frac{(z^*)^2 \cdot \hat{p}(1-\hat{p})}{e^2}$$

where $e$ is the desired margin of error.

There's a catch: to calculate $n$, you need to estimate $\hat{p}$. But you don't have the sample yet. 

Three strategies:

1. **Use a prior estimate.** If the company ran a similar survey last year and found $\hat{p} = 0.15$, use that.
2. **Assume the worst case.** The product $\hat{p}(1-\hat{p})$ is largest when $\hat{p} = 0.5$. So use $\hat{p} = 0.5$ to get a conservative (larger) sample size.
3. **Use preliminary data.** Run a small pilot survey, get a rough estimate of $\hat{p}$, then calculate the full sample size needed.

**Example:** The polling company wants $e = 0.025$ (margin of error ±2.5%), and they have no prior information. Use strategy 2: $\hat{p} = 0.5$.

$$n = \frac{(1.96)^2 \cdot 0.5(1-0.5)}{(0.025)^2} = \frac{3.8416 \cdot 0.25}{0.000625} = \frac{0.9604}{0.000625} = 1537$$

So they need to survey about 1,537 people to achieve that precision at 95% confidence with no prior knowledge of the true proportion.

**The trade-off revealed:** To cut the margin of error in half, you must *quadruple* the sample size. The formula has $e^2$ in the denominator. This is why polling companies face a real cost when they want more precision.

### From confidence level to precision

**Scenario 1:** Confidence level 95%, margin of error ±3%.
- $z^* = 1.96$, $\hat{p} = 0.5$
- $n = \frac{(1.96)^2 \cdot 0.25}{(0.03)^2} = \frac{0.9604}{0.0009} = 1067$

**Scenario 2:** Confidence level 99%, margin of error ±3%.
- $z^* = 2.576$, $\hat{p} = 0.5$
- $n = \frac{(2.576)^2 \cdot 0.25}{(0.03)^2} = \frac{1.656}{0.0009} = 1840$

Higher confidence costs sample size. The 99% confident poll requires 773 more respondents than the 95% confident poll, both at the same margin of error.

### A scale shift: Replicating the procedure

Imagine the polling company repeats this study 100 times, surveying 1,537 new random samples each time. They build a 95% confidence interval from each sample.

- About **95 of those 100 intervals** will contain the true population proportion.
- About 5 will miss.

You'll never know which category your interval falls into. But if you trust the procedure (random sampling, known σ or large n, correct formula), you should trust that 95 of 100 intervals work.

This is what "95% confidence" means procedurally. Not "this interval has a 95% chance of being right," but "this procedure produces right intervals 95% of the time."

---

## Exercises

### Warm-up

**Exercise 8.1** *(LO: construct CI for a mean, σ known.)* A sample of 50 college freshmen shows a mean SAT math score of $\bar{x} = 510$ with a known population standard deviation $\sigma = 100$. Build a 90% confidence interval for the true mean SAT math score of all college freshmen. Interpret the result.

**Exercise 8.2** *(LO: construct CI for a mean, σ unknown.)* A sample of 12 patients in a sleep study slept an average of $\bar{x} = 8.1$ hours with sample standard deviation $s = 1.2$ hours. Build a 95% confidence interval for the true mean hours of sleep. What is the degrees of freedom? Why does the t-value differ from the z-value you would use if σ were known?

**Exercise 8.3** *(LO: construct CI for a proportion.)* In a random sample of 400 households, 68 say they own a tablet computer. Build a 95% confidence interval for the true proportion of all households that own tablets. Check that the conditions for normal approximation are met.

### Application

**Exercise 8.4** *(LO: compare confidence levels.)* Using the data from Exercise 8.2 (sample mean 8.1 hours, $s = 1.2$, $n = 12$), construct both a 90% and a 99% confidence interval. Compare the margins of error and the interval widths. Explain why the 99% interval is wider.

**Exercise 8.5** *(LO: interpret margins of error.)* A poll reports: "52% of voters approve of the president's job performance, margin of error ±4%, 95% confidence." What does this statement mean? Is it correct to say "there's a 95% chance the true approval rate is between 48% and 56%"? Why or why not?

**Exercise 8.6** *(LO: sample size calculation.)* A company wants to estimate the proportion of its website visitors who make a purchase, with a margin of error of ±3% at 95% confidence. How many visitors must they track? If they want to cut the margin of error to ±2%, how many visitors are needed? What is the relationship between margin of error and sample size?

### Synthesis

**Exercise 8.7** *(LO: integrate means and proportions.)* You are designing a survey to estimate (1) the mean household income in a county and (2) the proportion of households below the poverty line. For the mean, you have a rough estimate of the standard deviation ($s \approx \$20,000$). For the proportion, you have a pilot estimate of about 12% below the line. Build a 95% confidence interval for each, assuming a sample size of 200. Which estimate is more precise (narrower interval relative to the estimate)? Why?

**Exercise 8.8** *(LO: recognize limitations and biases.)* A survey of 500 gym members finds that the mean weight loss after six months is 12 pounds, $s = 8$ pounds. Build a 95% CI. But identify two ways this interval might be misleading: (1) a bias in who responded, and (2) an assumption about the underlying distribution.

### Challenge

**Exercise 8.9** *(LO: compare procedures.)* A pharmaceutical company runs a clinical trial of a new blood pressure drug. They measure the systolic blood pressure of 25 patients before and after treatment. The mean reduction is 15 mmHg with $s = 10$ mmHg. (a) Build a 95% confidence interval using the t-distribution. (b) How would the interval change if the sample size were 100 instead of 25? (c) How would it change if the standard deviation were 5 mmHg instead of 10? (d) Explain the direction of each change in terms of the margin of error formula.

**Exercise 8.10** *(LO: open-ended reasoning.)* A researcher publishes a study claiming: "We are 95% confident that the mean improvement in students' test scores after using our tutoring program is between 3 and 7 points." Critique this claim. What would you want to know about the study design, sample, and assumptions to decide whether to believe it?

---

## Chapter summary

You can now do five things you probably could not do an hour ago.

You can **build a confidence interval for a population mean** when you know or can assume the population standard deviation, using the z-distribution and the formula $\bar{x} \pm z^* \cdot \frac{\sigma}{\sqrt{n}}$. You understand that the interval gets narrower with larger samples and wider with higher confidence.

You can **build a confidence interval when the standard deviation is unknown**, using the t-distribution and $\bar{x} \pm t_{df, \alpha/2} \cdot \frac{s}{\sqrt{n}}$, and you understand why Gossett's discovery (the t-distribution) was necessary: because the sample standard deviation $s$ is itself random, and the normal distribution underestimates the uncertainty when $n$ is small.

You can **build a confidence interval for a population proportion**, using $\hat{p} \pm z^* \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$, and you know to check that $np \geq 5$ and $n(1-p) \geq 5$ before you trust the normal approximation.

You can **calculate the sample size** needed to achieve a desired margin of error at a specified confidence level, and you understand the cost: halving the margin of error requires quadrupling the sample size.

Most importantly, you understand the distinction that saves you from a pervasive error: **95% confidence is a statement about the procedure, not about this particular interval.** If you build confidence intervals the right way 100 times, about 95 will contain the true parameter. But any single interval either does or doesn't. You'll never know which. That honest uncertainty is the whole point.

---

## What would change my mind

Evidence that the true population parameter falls outside the confidence interval I built would show that either my procedure was biased, my randomization failed, or I was one of the small fraction of samples whose intervals miss. More broadly, if I observed that across many repeated samplings, fewer than 95% of my 95% confidence intervals contained the true parameter, I would suspect a violation in one of my assumptions: perhaps the population isn't normal, or the samples aren't truly random, or the standard deviation changed.

---

## Still puzzling

I don't yet have a fully satisfying intuition for why replacing $\sigma$ with $s$ requires the heavier tails of the t-distribution rather than a simple adjustment factor. Gossett's derivation (the t as a ratio of normal and chi-squared) makes mathematical sense, but I haven't yet developed a picture that shows *why* that particular construction captures the added uncertainty. The math works; the mechanism remains slightly opaque.

---

## Tags

confidence-intervals, margin-of-error, hypothesis-testing-foundation, central-limit-theorem, z-distribution, t-distribution, sample-size-planning, polling, clinical-trials, parameter-estimation

---

## Connections forward

In Chapter 9, you will use confidence intervals as the foundation for hypothesis testing. The logic reverses: instead of building an interval around a sample statistic and asking "where is the parameter?", you'll assume a parameter value and ask "how consistent is this sample with that assumption?" Both procedures rest on the sampling distributions you learned here (normal for large samples, t for small).

In Chapter 10, you'll build confidence intervals for the difference between two population means or proportions. The formulas grow more complex, but the structure—point estimate ± margin of error—remains unchanged. You'll see that comparing two samples is just a careful extension of estimating one.

In applied work—medicine, public policy, business analytics—confidence intervals are your working tool for converting uncertainty into a decision. When a clinical trial estimates that a drug reduces symptoms by 5 to 15 points, confidence intervals tell you whether you're confident enough in that range to approve the drug. This chapter gives you the machinery. The chapters that follow show you how to use it.
---

## LLM Exercise — Chapter 8: Confidence Intervals (Analyze One Dataset Project)

**Project:** Analyze One Real Dataset.
**What you're building this chapter:** CIs for mean and proportion on key variables.
**Tool:** **Claude Code** + **Claude Project**.

---

**The Prompt:**

```
Chapter 8 of my Analyze-One-Dataset project. Chapter 8 covered:
CI for one mean using t-distribution when σ is unknown (CI = x̄ ±
t*·s/√n; t* depends on n-1 degrees of freedom and the confidence
level); CI for one proportion (CI = p̂ ± z*·√(p̂(1-p̂)/n));
interpretation (95% CI: if we repeated the sampling many times,
95% of the resulting CIs would contain the true parameter —
NOT "95% probability the true parameter is in this interval");
sample-size formulas to achieve a target margin of error.

Write the brief's "Confidence Intervals" section in 500-800 words.

1. **CI for a mean.** Pick a quantitative variable. Compute:
   - Sample mean x̄.
   - Sample SD s.
   - Sample size n.
   - For 95% CI: t* with n-1 df (use scipy.stats.t.ppf(0.975,
     df=n-1)).
   - Margin of error = t* · s / √n.
   - Lower bound = x̄ − ME; Upper bound = x̄ + ME.
   - Interpret: "We are 95% confident that the true population
     mean of [variable] lies between [lower] and [upper]."
   - Also compute the 90% and 99% CIs for comparison.

2. **CI for a proportion.** Pick a categorical variable's specific
   level (e.g., proportion of items that meet a particular
   criterion). Compute:
   - Sample proportion p̂.
   - Standard error = √(p̂(1-p̂)/n).
   - For 95% CI: z* = 1.96.
   - Margin of error = z* · SE.
   - Lower and upper bounds.
   - Check the rule of thumb (np̂ ≥ 10 AND n(1-p̂) ≥ 10) for
     normal approximation validity.

3. **Sample-size calculation.** If you wanted a 95% CI for the
   proportion with margin of error ≤ 0.02 (2 percentage points),
   how large would n need to be? Use n = (z*/ME)² · p̂(1-p̂).
   - If your current n is smaller than required, note that and
     interpret accordingly.
   - If your current n is much larger than needed, your study
     could have been smaller.

4. **The interpretation discipline.** The common mistake is
   saying "there's a 95% probability the parameter is in the
   interval." That's wrong. The parameter is fixed; the interval
   is random. State the correct interpretation explicitly.

End with the practical conclusion: given the CIs, what can you
say about [your big question from Ch 1] with calibrated
confidence?
```

---

**What this produces:** A 500-800 word section with 2-3 confidence intervals, sample-size calculation, and a calibrated interpretation. The "what we can say with confidence" framing is the discipline this chapter trains.

**How to adapt this prompt:**

- *For your own project:* Pick variables whose CIs are operationally meaningful — the interval's width tells you how precisely you've measured the parameter.
- *For ChatGPT / Gemini:* Works as written.
- *For Claude Code:* `scipy.stats.t.interval(0.95, df, loc=mean, scale=SE)` is the one-liner; building from scratch with formulas is the pedagogically valuable version.
- *For a Claude Project:* Append.

**Connection to previous chapters:** Ch 7's standard error feeds directly into Ch 8's margin of error.

**Preview of next chapter:** Chapter 9 covers hypothesis testing with one sample. You'll test one specific claim about your dataset (e.g., "the mean is X" or "the proportion is Y").


---

## 🕰️ AI Wayback Machine

**Jerzy Neyman** was Polish-American statistician who built the modern theory of confidence intervals and hypothesis testing in the 1930s with Egon Pearson.

**Run this:**

```
Who is Jerzy Neyman, and how does their work connect to confidence intervals we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Jerzy Neyman"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Jerzy Neyman's framework to a small dataset you actually have.
- Add a constraint: "Answer including criticisms or limits of Jerzy Neyman's framework."

What changes? What gets better? What gets worse?
