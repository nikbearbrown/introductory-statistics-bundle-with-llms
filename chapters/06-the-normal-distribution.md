# Chapter 6 — The Normal Distribution

## Three title options

1. **The Bell Curve That Won the War: How a handheld shape became the grammar of uncertainty**
2. **When Things Fall: Why so much of what we measure obeys one mathematical law**
3. **The Most Common Shape: From heights to exam scores, the normal distribution is everywhere—and how to speak its language**

---

## TL;DR

The normal distribution is the bell-shaped curve you've seen a hundred times without knowing why it appears everywhere. It's not just ornamental; it's a working tool. Once you know the mean and standard deviation of a normal population, the 68-95-99.7 rule tells you what percentage falls in any band around the middle. Z-scores let you translate any value from any normal distribution into a standardized position, so you can compare apples to apples. The standard normal table converts the complicated formula into a simple lookup. Everything that follows—confidence intervals, hypothesis testing, all of it—pivots on this one curve.

---

## Cold open: Sir Francis Galton's wisdom teeth

It's 1875 in London. Francis Galton, polymath and obsessive measurer, is studying heredity. He collects data on heights of parents and their children. He makes dots on a graph—each dot a child, horizontal position the father's height, vertical position the child's. The pattern that emerges is a cloud. It's not random scatter. The cloud has a shape: it swells around the middle, tapers toward the edges, and does so symmetrically. If you squint at the edges of that cloud and imagine it filled in, smoothed, rounded into a curve, you see a bell.

Galton had seen the same shape before. It appeared in measurements of acorns from different oak trees, in the chest circumferences of soldiers, in the strengths of cannons tested on the production line. He began to suspect he was looking at a fundamental law of nature—not something imposed by the laws of physics, but something intrinsic to variation itself. When you measure the same kind of thing in a population (heights, or test scores, or the time it takes someone to run a mile), and that measurement is determined by many small independent causes adding up, the result is a bell-shaped distribution. Galton didn't prove this mathematically—that came later—but he saw the pattern and named it: the curve of natural variation. We call it the normal distribution.

What makes it normal is not that it's common—though it is. What makes it normal is that it obeys one mathematical formula, and that formula depends on exactly two numbers: the mean ($\mu$, pronounced "mu," the Greek letter for "average") and the standard deviation ($\sigma$, "sigma," the measure of spread). Every bell-shaped distribution you'll ever meet has this same shape, this same proportions, once you translate its mean to zero and its spread to units of one. This is why the normal distribution is the skeleton key in statistics. It unlocks everything downstream.

This chapter teaches you to read that curve and to move fluently between it and the real data underneath.

### Learning objectives

By the end of this chapter you will be able to:

- **Identify** when the normal distribution is a reasonable model for data and when it's not.
- **Compute** z-scores that translate any value from any normal distribution into standard units.
- **Use** the empirical rule (68-95-99.7) to make instant estimates of what percentage of a population lies in any band around the mean.
- **Read** the standard normal table to find exact probabilities for any standardized interval.
- **Compare** values from different populations by converting them to z-scores and reading percentiles.
- **Recognize** when to use the normal distribution to approximate binomial probabilities and execute that approximation correctly.

### Prerequisites

Understanding of the mean and standard deviation from Chapter 2. Familiarity with z-scores as a concept (introduced in Chapter 3). Comfort with reading and interpreting probability as an area under a curve. Willingness to look values up in a table without understanding the calculus underneath.

### Why this chapter matters

The normal distribution is the gateway to inference. In Chapter 7, the central limit theorem will tell you that if you take repeated samples from any population and plot their means, those sample means form a normal distribution. That fact—that sample means are normally distributed even when the population they're drawn from is not—is the foundation of everything you'll do in the rest of this course. You cannot understand confidence intervals, hypothesis testing, or regression without understanding what the normal distribution is and how to move through it. This chapter equips you to do that.

Beyond the classroom, the normal distribution appears whenever a measurement or outcome is influenced by many small independent causes. Test scores. Heights. Weights. Lifetimes of electronic components. The IQ tests that steer lives. The dosages of medications that save them. The distribution is not decorative. It is consequential.

---

## Concept 1 — Where the normal curve comes from, and what it measures

The formula for the normal probability density function looks like this:

$$f(x) = \frac{1}{\sigma \sqrt{2\pi}} \cdot e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}$$

Do not memorize it. Do not even try to understand it in detail. The point is this: it's a function that takes a value $x$ and tells you the *height* of the curve at that point. The curve is symmetric about the mean $\mu$. The mean, median, and mode are all the same number—they all sit at the peak of the bell. The curve tapers off to either side according to how many standard deviations you are away from the mean.

Here's what matters: this one formula generates an infinite family of bell curves, one for every possible choice of $\mu$ and $\sigma$. A distribution with mean 100 and standard deviation 15 has the same *shape* as a distribution with mean 500 and standard deviation 50—they're just shifted and stretched versions of each other. The shape itself is determined by one thing and one thing only: how many standard deviations away from the mean you are.

We denote a normal distribution with mean $\mu$ and standard deviation $\sigma$ as $N(\mu, \sigma)$. If your data follows a normal distribution with mean 70 and standard deviation 2.5, you'd write $X \sim N(70, 2.5)$. The tilde means "is distributed as," and the notation is read aloud as "X is distributed as normal with mean 70 and standard deviation 2.5."

### When is the normal distribution reasonable?

Not all data are normally distributed. Heights in a population are. Test scores often are, especially when the test is well-designed and the sample is large. But arrival times at an emergency room are not—they cluster during rush hours and thin out at 3 a.m. Income distributions are not normal—they have a long tail to the right, with a few very high earners pulling the mean above the median. Before you apply the normal distribution to data, you should plot it. Look at the histogram. Does it have a single peak? Does it taper off symmetrically to both sides, or does one tail stretch longer? Are there clusters or gaps? If the data are genuinely skewed, or multimodal, or have heavy outliers, the normal distribution is a poor fit. Statistical tests can tell you whether the data fit the normal distribution well enough. For now, trust your eyes: if the histogram doesn't look roughly bell-shaped, the normal distribution isn't the right tool.

### The trade-off: elegance for precision

The normal distribution is useful precisely because it's elegant. If you know the mean and standard deviation, you instantly know that 68% of your data lie within one standard deviation of the mean, 95% within two, and 99.7% within three. This is called the empirical rule, and it's a massive convenience. It means you don't have to calculate anything—you just remember the three numbers 68, 95, and 99.7, and you can estimate answers to a wide class of probability questions in your head.

The cost: you lose precision. The empirical rule gives you rough bands. It says that 68% of the data fall between $\mu - \sigma$ and $\mu + \sigma$. But what if you need to know what percentage falls between $\mu - 0.5\sigma$ and $\mu + 0.8\sigma$? The empirical rule won't tell you. For that, you need the standard normal table, and you need to know how to use it. That's the next concept.

---

## Concept 2 — Z-scores and the standard normal distribution

Imagine you're an admissions officer at a university. One applicant took the SAT and scored 1200. Another took the ACT and scored 28. Which score is better? You can't compare them directly—they're on different scales. The SAT ranges from 400 to 1600; the ACT ranges from 1 to 36. But what if both distributions are normal? Then you can translate both scores into a common language.

The common language is the **z-score**, also called the standardized score. A z-score tells you how many standard deviations a value is away from its population mean. The formula is simple:

$$z = \frac{x - \mu}{\sigma}$$

where $x$ is the value you're standardizing, $\mu$ is the population mean, and $\sigma$ is the population standard deviation.

Suppose the SAT has mean $\mu = 1050$ and standard deviation $\sigma = 200$. The applicant who scored 1200 has a z-score of:

$$z = \frac{1200 - 1050}{200} = \frac{150}{200} = 0.75$$

This applicant is 0.75 standard deviations above the mean.

Now suppose the ACT has mean $\mu = 21$ and standard deviation $\sigma = 5$. The applicant who scored 28 has a z-score of:

$$z = \frac{28 - 21}{5} = \frac{7}{5} = 1.4$$

This applicant is 1.4 standard deviations above the mean. So the second applicant did better *relative to peers taking the same test*. The score of 28 is more impressive than 1200.

Here's the key insight: when you convert any value to a z-score, you're expressing it in terms of distance from the mean, measured in standard deviations. Once everything is expressed in z-scores, the distribution becomes standardized. We call this the standard normal distribution, written $N(0, 1)$—mean zero, standard deviation one. This is the distribution Galton discovered: the universal shape of variation, stripped of any particular location or scale. Every normal distribution can be converted into this one standard form.

The interpretation of z-scores is straightforward:

- $z = 0$ means the value is exactly at the mean.
- $z = 1$ means the value is one standard deviation above the mean.
- $z = -1.5$ means the value is 1.5 standard deviations *below* the mean.
- $z = 2.3$ means the value is 2.3 standard deviations above the mean.

A positive z-score means the value is above the mean. A negative z-score means it's below. The magnitude tells you how far.

### The empirical rule applied to z-scores

Remember those percentages: 68, 95, 99.7? Now you can state them precisely in terms of z-scores.

For any normal distribution:

- About 68% of data fall between $z = -1$ and $z = +1$ (within one standard deviation of the mean).
- About 95% of data fall between $z = -2$ and $z = +2$ (within two standard deviations of the mean).
- About 99.7% of data fall between $z = -3$ and $z = +3$ (within three standard deviations of the mean).

This is profound. It means that if you know a value's z-score, you instantly know its percentile rank in the population.

If someone has a z-score of 1, they're at about the 84th percentile. (Half the population is below the mean—that's 50%—plus about 34% of the population between the mean and one standard deviation above it, for a total of 84%.)

If someone has a z-score of 2, they're at about the 97.5th percentile. (50% + 47.5% = 97.5%.)

If someone has a z-score of -1, they're at about the 16th percentile. (50% - 34% = 16%.)

### A worked example — comparing test scores

A student scores 85 on a statistics exam where the class mean is 80 and the standard deviation is 4. Another student scores 88 on an English exam where the class mean is 85 and the standard deviation is 6. Assuming both classes have normally distributed scores, who performed better relative to their peers?

*Statistics student:*

$$z = \frac{85 - 80}{4} = \frac{5}{4} = 1.25$$

This student is 1.25 standard deviations above the class mean. Using the empirical rule as a rough guide, this puts them around the 89th percentile.

*English student:*

$$z = \frac{88 - 85}{6} = \frac{3}{6} = 0.5$$

This student is only 0.5 standard deviations above the class mean. This puts them around the 69th percentile.

*Conclusion:* The statistics student performed better relative to peers, even though the raw score (85 vs. 88) was lower. The z-score accounts for the fact that the English class had more spread—getting 3 points above the mean is less impressive when the standard deviation is 6 than when it's 4.

### Common misconceptions

**"A z-score of 2 is twice as good as a z-score of 1."** No. A z-score measures position relative to the mean, not magnitude. It's a ranking system, not a proportion. A z-score of 2 puts you farther from the mean than a z-score of 1, but it doesn't mean your actual value is twice as large.

**"Z-scores are only for normal distributions."** True. The z-score formula makes sense for any distribution, but the *interpretation* of z-scores—the fact that a z-score of 1 corresponds to roughly the 84th percentile—relies on the normal distribution. For other distributions, you'd need different conversion tables.

---

## Concept 3 — Using the normal distribution to find probabilities

You know the mean and standard deviation. You have a value you want to evaluate. You need to find the probability that a randomly selected observation from the population falls above, below, or between certain points. How do you do it?

The answer is the standard normal table, also called the z-table. This is a lookup table that shows, for any z-score, the probability of getting a value between the mean (z=0) and that z-score in a standard normal distribution. You read down the first column to find your z-score, read across to find the second decimal place, and the number where row and column meet is the probability.

For example, if you look up z = 1.25, the table gives you 0.3944. This means the probability of getting a value between 0 and 1.25 standard deviations above the mean is 0.3944 or 39.44%.

Here's how to use the table to answer real questions:

**Question: What proportion of the population falls below a given value?**

Step 1: Convert the value to a z-score using $z = \frac{x - \mu}{\sigma}$.

Step 2: If the z-score is positive, look it up in the table to get the area between 0 and your z-score. Add 0.5 (the area to the left of the mean) to get the total area to the left of your value.

Step 3: If the z-score is negative, look up the absolute value, subtract the table value from 0.5 to account for being on the left side of the mean.

**Question: What proportion of the population falls above a given value?**

Find the proportion below it (using the steps above) and subtract from 1.

**Question: What proportion falls between two values?**

Convert both to z-scores. Look up both. Subtract the smaller area from the larger area.

### A worked example — final exam scores

The final exam scores in a statistics class are normally distributed with mean 75 and standard deviation 8. What percentage of students scored between 70 and 85?

*Step 1: Convert both boundaries to z-scores.*

Lower boundary: $z_1 = \frac{70 - 75}{8} = \frac{-5}{8} = -0.625$

Upper boundary: $z_2 = \frac{85 - 75}{8} = \frac{10}{8} = 1.25$

*Step 2: Look up both z-scores in the standard normal table.*

For z = 1.25, the table gives 0.3944. This is the area between the mean and 1.25 standard deviations above it.

For z = -0.625, the absolute value is 0.625. Looking that up (rounding to 0.63), the table gives approximately 0.2357. This is the area between the mean and 0.625 standard deviations below it.

*Step 3: Add the two areas.*

Total area = 0.2357 + 0.3944 = 0.6301

*Interpretation:* About 63% of students scored between 70 and 85. Or, if you randomly select a student, there's a 0.63 probability their score falls in that range.

### The crucial symmetry

The normal distribution is symmetric about the mean. This means that the area to the left of the mean equals the area to the right. Each equals 0.5 or 50%. It also means that the distance from the mean to, say, 85 on the right produces the same area as the same distance on the left. A z-score of -1 covers the same area (34%) as a z-score of +1. The standard normal table only lists positive z-scores because of this symmetry—you can apply the same areas to negative z-scores by symmetry.

This symmetry is so important that some textbooks write the z-score formula as:

$$z = \frac{|x - \mu|}{\sigma}$$

with absolute value bars, to emphasize that only the distance from the mean matters for the area calculation, not the direction.

### Common misconceptions

**"If my z-score is 2, then 2% of the population is above me."** No. If your z-score is 2, then about 97.5% of the population is below you (and 2.5% is above). The table gives you areas, not percentages of the tail.

**"The normal distribution table works for all distributions."** No. This table is specific to the normal distribution. For other distributions, you'd need different tables or calculations.

---

## Integration — from raw scores to confidence and back

Return to the beginning. You have a population. You measure something—heights, test scores, assembly times, dosages. The measurements are normally distributed. You want to know: what's the probability that a randomly selected measurement falls in some range?

Here's the three-step process, the one you'll use over and over:

1. **Standardize**: Convert the raw value to a z-score using $z = \frac{x - \mu}{\sigma}$.

2. **Lookup**: Read the standard normal table to find the area (probability) corresponding to that z-score.

3. **Interpret**: Translate the probability back into a statement about the original population.

Let's say the heights of adult men in the United States are normally distributed with mean 70 inches and standard deviation 2.5 inches. A randomly selected man walks into a room. What's the probability he's taller than 72 inches?

*Standardize:* $z = \frac{72 - 70}{2.5} = \frac{2}{2.5} = 0.8$

*Lookup:* The z-table shows that the area between 0 and 0.8 is 0.2881. This is the probability of being between 70 and 72 inches.

*Interpret:* Since we want "taller than 72," and the total area to the right of the mean is 0.5, the probability of being above 72 is $0.5 - 0.2881 = 0.2119$ or about 21.2%.

In the next chapter, you'll learn what happens when you don't have one randomly selected individual, but instead a sample of them. You'll learn that the means of those samples form a normal distribution even if the population doesn't. That discovery—the central limit theorem—is what makes statistics inference possible. But it all rests on understanding this curve, this one shape, this grammar of variation.

For now, practice the process until it's automatic: standardize, lookup, interpret. The pattern repeats in a thousand forms.

---

## Exercises

### Warm-up

**Exercise 6.1** *(LO: standardize and interpret z-scores.)* A population of adult women has mean height 65.5 inches and standard deviation 2.2 inches, normally distributed. What is the z-score for a woman who is 68 inches tall? Interpret this z-score in a complete sentence.

**Exercise 6.2** *(LO: use the empirical rule.)* IQ scores are normally distributed with mean 100 and standard deviation 15. Using the 68-95-99.7 rule, what percentage of the population has an IQ between 85 and 115?

**Exercise 6.3** *(LO: read the standard normal table.)* Using the standard normal table, find the probability (area) that a z-score falls between 0 and 1.5. Then find the probability that a z-score falls below -1.5.

### Application

**Exercise 6.4** *(LO: convert to z-score and interpret percentile.)* A student scores 92 on an exam where the mean is 85 and the standard deviation is 6. What is the student's z-score? Using the 68-95-99.7 rule as an approximation, what percentile rank does this correspond to (approximately)?

**Exercise 6.5** *(LO: find probability using the normal distribution.)* The lifetimes of a certain brand of lightbulb are normally distributed with mean 1000 hours and standard deviation 120 hours. What is the probability that a randomly selected lightbulb lasts more than 1200 hours?

**Exercise 6.6** *(LO: compare values across populations using z-scores.)* A student scores 78 on a history exam (mean 75, SD 4) and 82 on a biology exam (mean 80, SD 5). On which exam did the student perform better relative to classmates? Show your z-score calculations.

### Synthesis

**Exercise 6.7** *(LO: integrate the full process.)* A company manufactures ball bearings with a diameter that should be 2 cm. The actual diameters are normally distributed with mean 2.0 cm and standard deviation 0.05 cm. The company accepts bearings between 1.95 and 2.05 cm. (a) What percentage of bearings will be accepted? (b) What percentage will be too large?

**Exercise 6.8** *(LO: apply to real-world decision making.)* A nurse must administer a medication to patients. The dose is normally distributed in the population—patients metabolize drugs at different rates. The recommended dose is 100 mg with standard deviation 15 mg. The nurse wants to know what proportion of patients will metabolize the dose within a safe range of 75 to 125 mg. Using the normal distribution, calculate this proportion.

### Challenge

**Exercise 6.9** *(LO: reverse the process—find the value given the probability.)* In a standardized test with mean 500 and standard deviation 100, what score puts a student in the 90th percentile? (Hint: first find the z-score that corresponds to the 90th percentile using the table, then solve for x using $x = \mu + z \cdot \sigma$.)

**Exercise 6.10** *(LO: integrate and extend.)* Manufacturing tolerances often use the 99.7% rule. A factory produces screws with mean diameter 10 mm and standard deviation 0.1 mm, normally distributed. To keep 99.7% of screws within acceptable bounds, between what two diameters should screws fall? Why is the 99.7% rule useful for manufacturing?

---

## Chapter summary

You can now do five things you probably could not do before.

You can **identify when a normal distribution is reasonable** for data and recognize when it's not by looking at a histogram.

You can **translate any value from any normal distribution into a z-score**, a standardized position that lets you compare across populations on a common scale.

You can **apply the empirical rule** (68-95-99.7) to estimate percentages in your head, instantly, without a calculator.

You can **read a standard normal table** and use it to find the exact probability that a value falls above, below, or between specified boundaries.

And you have learned that **the normal distribution is not decorative**. It is the foundation of inference. Everything you do from this point forward—confidence intervals, hypothesis tests, regression models—rests on understanding this curve.

The thing to watch for is **confusing the direction of the question**. "Above this value" and "below this value" require opposite moves with the table. "Between these two values" requires subtraction. These are mechanical steps, but they're easy to reverse. When in doubt, sketch the curve, shade the region you're interested in, and count from the picture before you count from the numbers.

What you should now be able to teach a friend who asks: why the bell curve appears everywhere; what a z-score actually measures; how to convert a raw score into a percentile rank; why the normal distribution makes comparisons across different populations possible.

---

## Connections forward

In Chapter 7, you'll meet the central limit theorem, which says that sample means are normally distributed even when the population they're drawn from is not. This is the most important fact in statistics. It's what allows you to take a sample of 30 people and make inferences about the entire population of millions. The theorem rests entirely on the foundation you've built in this chapter.

Chapters 8 and 9 use the normal distribution to construct confidence intervals and test hypotheses. You'll use z-scores again and again, reading tables, translating back and forth between raw data and standardized position. The normal distribution becomes your lingua franca.

Chapter 13 will return to the normal distribution when you learn linear regression. The errors—the residuals—in a good regression model should themselves be normally distributed. The normal distribution is not just a probability distribution at that point. It's a diagnostic. It tells you whether your model is working.

For now, the skill is fluency with the curve. Know its shape. Know what z-scores mean. Know how to read the table. The geometry of normal distributions—the symmetry, the tails, the concentration near the mean—will become intuitive as you use it. The pattern is always the same: standardize, lookup, interpret. Master that three-step dance and the rest of statistics is within reach.

---

## Still puzzling

I don't fully understand why so many naturally occurring measurements—heights, test scores, measurement errors—follow this specific mathematical curve and not some other distribution. The central limit theorem (next chapter) provides one explanation, but the visual intuition for why the normal distribution in particular must arise from sums of random effects remains opaque to me.

---

## What would change my mind

If I encountered a large, well-measured population of a familiar quantity (e.g., adult heights, standardized test scores) that visibly deviated from the normal distribution and could not be explained by truncation, selection effects, or measurement error, I would revise my assumption that the normal distribution is nearly universal. So far I haven't.

---

## Tags

`normal-distribution`, `z-scores`, `standard-normal`, `probability`, `empirical-rule`, `68-95-99.7`, `inference-foundation`

---
---

## LLM Exercise — Chapter 6: The Normal Distribution (Analyze One Dataset Project)

**Project:** Analyze One Real Dataset.
**What you're building this chapter:** normality assessment of key variables + z-score interpretation.
**Tool:** **Claude Code** + **Claude Project**.

---

**The Prompt:**

```
Chapter 6 of my Analyze-One-Dataset project. Chapter 6 covered the
Normal distribution N(μ, σ²); the standard Normal Z = (X − μ)/σ;
the empirical rule (68%/95%/99.7% within ±1, ±2, ±3 SDs); using
tables or software to find P(Z < z), P(Z > z), P(a < Z < b);
inverse normal: given a probability, find the corresponding x.

Write the brief's "Normality Analysis" section in 400-600 words.

1. **Pick a quantitative variable that you suspect is approximately
   Normal.** Often: heights, IQ scores, lab measurements, mean
   reaction times. Sometimes: test scores, daily returns on liquid
   markets (though see Ch 5 caveat about fat tails).

2. **Visualize.** Histogram + overlay of theoretical Normal with
   the sample mean and SD. Note where the empirical density
   matches and where it deviates.

3. **Q-Q plot.** Plot the variable's quantiles against the
   theoretical Normal quantiles. If approximately Normal, the
   points form a straight line. Deviations indicate:
   - S-shape: heavier or lighter tails than Normal.
   - Curved: skewness.
   - Steps: discretization (not continuous).

4. **Formal normality test.** Run Shapiro-Wilk (`scipy.stats.
   shapiro`). Note: with n > 5000, normality tests reject the
   null even for slight deviations (very high power). Use the
   visual + test together; the visual is more informative.

5. **Z-score computation.** Pick three values from your data:
   the maximum, the minimum, and one moderate point. Compute
   z for each. Look up the corresponding probabilities.
   - For the maximum: P(X > max in a Normal distribution with
     your sample mean and SD).
   - For the minimum: P(X < min similarly).
   The probabilities should be tiny (well below 1/n) if these
   are genuine extremes of a Normal distribution. If P(X > max)
   is, say, 0.10, your data has 10× more such extremes than a
   Normal predicts — your variable isn't Normal.

6. **Empirical rule check.** Compare empirical to theoretical:
   - Theoretical: 68%/95%/99.7% within ±1, ±2, ±3 SDs.
   - Empirical: count what fraction of data actually falls in
     each range.

End with the verdict: is your variable approximately Normal?
What kind of deviation (heavier tails? skew?) does it show?
This shapes which inference methods will be appropriate later.
```

---

**What this produces:** A 400-600 word section with Q-Q plot, empirical-vs-theoretical comparison, and a defensible normality assessment.

**How to adapt this prompt:**

- *For your own project:* If NO variable in your dataset is approximately Normal, you'll rely on CLT (Ch 7) for inference. Note that here.
- *For ChatGPT / Gemini:* Works as written.
- *For Claude Code:* `scipy.stats.shapiro`, `scipy.stats.probplot` for Q-Q.
- *For a Claude Project:* Append.

**Connection to previous chapters:** Ch 2's empirical-rule check, Ch 5's fitting work, and Ch 6's formal normality assessment build a layered evaluation.

**Preview of next chapter:** Chapter 7 covers the CLT. You'll simulate or bootstrap sampling distributions of the mean from your data and verify (or refute) the CLT's promise.


---

## 🕰️ AI Wayback Machine

**Carl Friedrich Gauss** was mathematician whose 1809 work on least squares put the normal distribution at the center of statistical practice.

**Run this:**

```
Who is Carl Friedrich Gauss, and how does their work connect to the normal distribution we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Carl Friedrich Gauss"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Carl Friedrich Gauss's framework to a small dataset you actually have.
- Add a constraint: "Answer including criticisms or limits of Carl Friedrich Gauss's framework."

What changes? What gets better? What gets worse?
