# Chapter 9 — Hypothesis Testing with One Sample

## Three title options

1. **Can the Evidence Decide? Testing claims against data when the stakes are real**
2. **The Burden of Proof: How statistics settles the question of whether something is actually true**
3. **When Data Speaks Loudly Enough: Building the logic to overturn what we thought was true**

---

## TL;DR

Hypothesis testing is a procedure for asking whether data from a sample provide strong enough evidence to reject a claim about a population parameter. The logic is asymmetric: the status quo (null hypothesis) is presumed true unless the evidence against it is strong enough—we control how strong by setting a significance level α. You learn to set up the test, choose the right distribution (z or t), compute a test statistic, find a p-value, and decide whether to reject the null hypothesis.

---

## Cold open: The moment the advisory committee votes

May 2004. An FDA advisory committee sits around a table. On one side: a pharmaceutical company with data from a clinical trial showing that their new drug reduces pain in osteoarthritis patients. On the other side: committee members who must decide whether to approve the drug for the market, knowing that approval will affect millions of people.

The company presents the numbers: patients taking the drug improved more than patients taking placebo. The difference is real, they argue. The committee asks: how real? Could this difference have happened by chance—by random noise in the data—even if the drug does nothing? Or is the signal strong enough that we should believe the drug works?

This is the question hypothesis testing answers. It's not a question of whether the drug helps everyone (nobody expects that). It's a question of whether the evidence is strong enough to reject the status quo: "this drug doesn't work."

The asymmetry matters. A drug company wants to prove its product works. The committee's job is to ask for strong evidence before overturning the default position: no approval until proven otherwise. This is not bias. It's a rational response to the stakes. The burden of proof lies with anyone asking us to change our minds.

This chapter teaches you that logic, and how to implement it with the tools statistics provides.

### Learning objectives

By the end of this chapter you will be able to:

- **State** null and alternative hypotheses correctly, identifying one-tailed and two-tailed tests.
- **Distinguish** between Type I and Type II errors and **explain** the trade-off between them.
- **Compute** the test statistic (z or t) for a single population mean, **compare** it to the critical value, and **make a decision**.
- **Calculate** the p-value and **interpret** it correctly (probability of the data given the null, not probability of the null given the data).
- **Conduct** hypothesis tests for a single population proportion.
- **Apply** the five-step procedure (set hypotheses, choose significance level, select test statistic, calculate, decide) to real scenarios with stakes.

### Prerequisites

Confidence intervals (Chapter 8). The central limit theorem (Chapter 7). Standard normal and t-distributions. Comfort with Greek letters and subscript notation.

### Why this chapter matters

In Chapter 8, you learned to build confidence intervals: "we're 95% confident the population mean is in this range." Now you learn to ask a different question: "The data show X. Is this evidence strong enough to reject the claim that the population parameter is Y?" Confidence intervals say where the parameter likely lives. Hypothesis testing says whether the data contradict a specific claim.

This matters because in science, medicine, manufacturing, and policy, we constantly face claims that need testing. A new teaching method. A drug that treats depression. A manufacturing process that's gone out of adjustment. A poll that predicts an election outcome. In each case, someone is asking us to change what we do based on evidence. Hypothesis testing provides the logic to say: sufficient evidence, or not yet.

You'll encounter the language of p-values, significance levels, and "statistical significance" for the rest of your career. You need to understand not just how to compute these, but what they actually mean—and what they don't mean. The most common misunderstanding is that a p-value tells you the probability your hypothesis is true. It does not. It tells you the probability of observing data this extreme or more extreme, assuming the null hypothesis is true. The conditional direction matters profoundly.

---

## Concept 1 — The Logic of Hypothesis Testing: Null, Alternative, Error, and the Burden of Proof

**Cold open: A court and the burden of proof**

A defendant stands trial. The court begins with a presumption: the defendant is innocent. This is the status quo. The burden of proof lies with the prosecution. The prosecution must present evidence—witness testimony, physical evidence, DNA—strong enough that the jury has no reasonable doubt (usually interpreted as 95% certainty) that the defendant is guilty. If the evidence is not that strong, the jury says "not guilty," not because they're convinced of innocence, but because the evidence failed to meet the threshold for conviction.

Notice the asymmetry. The presumption favors the defendant. The prosecution must overcome that presumption with strong evidence. The defense doesn't have to prove innocence; they only need to show reasonable doubt.

This is the logic of hypothesis testing, and it's not accidental. Scientists, regulators, and statisticians adopted it deliberately, and for good reason. The status quo—the way things are now, the standard practice, the assumed state—has an advantage in this framework. It takes strong evidence to overturn it.

### The null hypothesis and the alternative hypothesis

Every hypothesis test involves two competing claims:

The **null hypothesis**, written $H_0$ (aitch-naught), is the statement we assume to be true unless the data convincingly show otherwise. It is a claim of no difference, no effect, no change. "The drug has no effect." "The mean weight of the population is 150 pounds." "The proportion of voters who support the measure is 0.5." The null is the status quo, the default, the thing we would continue believing if we had no data.

Notice that $H_0$ always includes an equals sign (=, ≤, or ≥). This is a mathematical convention, but it reflects the logic: if the parameter equals the hypothesized value, the data should scatter randomly around that value. We test whether the data are consistent with that scatter, or whether they deviate too far to be believed.

The **alternative hypothesis**, written $H_a$ or $H_1$, is the claim we're testing. It is what we would conclude if the null hypothesis is rejected. "The drug has an effect." "The mean weight is not 150 pounds." "The proportion is not 0.5." The alternative is the contender, the new claim, the thing seeking to displace the null.

$H_a$ never includes an equals sign. It uses ≠, <, or >.

Two scenarios determine which test you're running:

**Two-tailed test:** The alternative hypothesis allows the parameter to differ from the null in either direction. If $H_0: \mu = 100$, then $H_a: \mu \neq 100$. We reject the null if the sample mean is too far above or too far below 100. The two tails of the distribution—both higher and lower—are where the "too different" values live. This is appropriate when we care about difference in either direction.

**One-tailed test:** The alternative hypothesis specifies a direction. If $H_0: \mu \leq 100$ and $H_a: \mu > 100$, we reject the null only if the sample mean is too much higher. We place all the "too extreme" probability in one tail. This is appropriate when we have a specific direction of interest: is the new process faster (not just different)? Does the drug reduce side effects (not just change them)?

### Type I and Type II errors—the trade-off you can't escape

Here's the uncomfortable truth: you can make an error either way. If you reject the null when it's actually true, that's a **Type I error**. You've rejected a good null hypothesis. If you fail to reject the null when it's actually false, that's a **Type II error**. You've let a false claim stand.

The probabilities are denoted by Greek letters:

$\alpha$ (alpha) = P(Type I error) = probability of rejecting the null when the null is true.

$\beta$ (beta) = P(Type II error) = probability of failing to reject the null when the null is false.

The power of the test is $(1 - \beta)$. It measures the test's ability to correctly reject the null when the null is false.

Here's what makes this harder: as you try to make $\alpha$ smaller (fewer false rejections), $\beta$ tends to grow larger (more false non-rejections), and vice versa. You can't drive both to zero. You face a trade-off. You choose to control $\alpha$ because the presumption favors the status quo—you want it to be hard to reject, so you make false rejection unlikely. $\beta$ follows wherever it will, and you hope it's small, but you're not guaranteed to control it directly.

#### A worked example—imagining the errors

Suppose the null hypothesis is: "This sleeping bag can withstand temperatures of –15°F." The alternative is: "It cannot."

A Type I error: You conclude the bag is inadequate when, in fact, it really can handle –15°F. You reject a good sleeping bag. Consequence: you don't use a bag that would have kept you warm.

A Type II error: You conclude the bag is adequate when, in fact, it cannot handle –15°F. You fail to reject a bad null. Consequence: you sleep outside in –15°F weather with an insufficiently rated bag. You risk hypothermia.

Which error has worse consequences? Type II — by a wide margin. Staying warm is life-critical.

So you'd set $\alpha$ high (maybe 0.20 instead of 0.05) to reduce the risk of Type II. You accept a higher false-rejection rate to protect against the worse error. The trade-off is deliberate.

### Common misconceptions

**"Accepting the null hypothesis means it's true."** No. Failing to reject the null means the data are consistent with it. The null might be true. It might also be false, but you don't have enough evidence yet. The language is careful: we "reject" or "fail to reject," never "accept."

**"The burden of proof is balanced between H0 and Ha."** No. The null has the advantage. It takes roughly 95% or 99% certainty to reject it. The alternative must clear a high bar. This is intentional—we make false rejection uncommon.

**"If α = 0.05, there's a 95% chance my conclusion is correct."** This misreads the meaning of α. It is the probability of a Type I error under the assumption that the null is true. It doesn't quantify the probability that your conclusion is right or wrong. That depends on how often the null is actually true in situations like the one you're in—information the test doesn't give you.

---

## Concept 2 — The Anatomy of a Hypothesis Test: Test Statistics, Critical Values, and P-Values

**Cold open: Drawing a line in the sand**

Imagine you're a manager at a manufacturing plant. A machine is supposed to dispense 8 ounces of liquid into each bottle. You take a random sample of 35 bottles and measure them. The sample mean is 7.91 ounces. The sample standard deviation is 0.173 ounces.

Is the machine broken? Or is this normal variation?

You can't tell just by looking at the difference (7.91 vs. 8). You need to ask: how far from 8 is 7.91, measured in standard deviations? If it's a small distance, say 0.5 standard deviations, it's noise. If it's 3 standard deviations, it's a signal. The test statistic quantifies this distance. Then you decide: beyond how many standard deviations do I shut down the machine?

### Building the test statistic from the Central Limit Theorem

Recall from Chapter 7 that if you take many samples of size $n$ from a population with mean $\mu_0$ and standard deviation $\sigma$, the sample means $\bar{X}$ are normally distributed with mean $\mu_0$ and standard error $\sigma/\sqrt{n}$:

$$\bar{X} \sim N\left(\mu_0, \frac{\sigma}{\sqrt{n}}\right)$$

This is the foundation of hypothesis testing. Under the null hypothesis, we assume the population mean equals $\mu_0$ (the hypothesized value). If the null is true, sample means should scatter randomly around $\mu_0$ in a normal pattern.

Now, take your actual sample and compute $\bar{x}$ (the sample mean). How many standard errors is $\bar{x}$ away from $\mu_0$? That's the test statistic:

$$Z = \frac{\bar{x} - \mu_0}{\sigma/\sqrt{n}}$$

(This is the z-test, used when you know $\sigma$—rare in practice, but clear in logic.)

This z-score tells you where your sample mean sits on the standard normal distribution. If $Z = 2$, your sample mean is 2 standard errors above the hypothesized value. On the standard normal curve, that's pretty far out—about 2.3% of the distribution lies beyond that point.

**Critical values and decision rules.** You decide, before collecting data, what threshold you're willing to cross. If you set $\alpha = 0.05$, you're saying: I will reject the null if the test statistic falls in the outermost 5% of the distribution (assuming the null is true).

For a two-tailed test with $\alpha = 0.05$, you split the 5% into two tails: 2.5% in each tail. The critical values are $Z_{0.025} = 1.96$ and $Z_{-0.025} = -1.96$. If your calculated test statistic $|Z| > 1.96$, you reject the null.

For a one-tailed test (say, $\alpha = 0.05$ with $H_a: \mu > \mu_0$), you put all 5% in the upper tail. The critical value is $Z_{0.05} = 1.645$. You reject the null only if $Z > 1.645$.

The decision rule is straightforward:
- If the test statistic is more extreme than the critical value, reject $H_0$.
- If the test statistic is not more extreme, fail to reject $H_0$.

### The P-value approach—probability, not proof

The critical value approach asks: is my test statistic in the rejection region? The p-value approach asks a subtly different question: how likely is a test statistic this extreme, if the null is true?

The **p-value** is the probability of observing a test statistic as extreme as, or more extreme than, the one you calculated, assuming the null hypothesis is true. It's a conditional probability: P(data this extreme | null is true).

It is not P(null is true | data). That's a common mistake, and it's a different question entirely. The p-value doesn't tell you how likely the null is. It tells you how surprising your data are under the assumption that the null is true.

Here's the decision rule:
- If p-value < α, reject $H_0$. The data are too surprising under the null to keep believing it.
- If p-value ≥ α, fail to reject $H_0$. The data are not surprising enough.

Example: You test whether a coin is fair. You flip it 100 times and get 58 heads. Under the assumption that the coin is fair, what's the probability of getting 58 or more heads (or 58 or more tails, for a two-tailed test)? If that probability is, say, 0.12, then the p-value is 0.12. You set α = 0.05. Since 0.12 > 0.05, you fail to reject the null that the coin is fair. The data are not surprising enough to conclude the coin is biased.

#### A worked example—Jeffrey's goggles

Jeffrey, eight years old, has been swimming the 25-yard freestyle in a mean time of 16.43 seconds with standard deviation 0.8 seconds. His father Frank buys him goggles and times 15 swims. The new mean is 16 seconds. Frank thinks the goggles helped.

**Set up the test:**

$H_0: \mu = 16.43$ (the goggles had no effect)

$H_a: \mu < 16.43$ (the goggles made him faster)

This is a one-tailed test (left tail).

**Choose the distribution and test statistic:**

$n = 15$, $\bar{x} = 16$ seconds, $\sigma = 0.8$ (known from past swims), population is normal.

Use the z-test:

$$Z = \frac{16 - 16.43}{0.8/\sqrt{15}} = \frac{-0.43}{0.2065} = -2.08$$

**Calculate the p-value:**

On the standard normal, how much area lies to the left of $Z = -2.08$? Looking at a standard normal table, $P(Z < -2.08) \approx 0.0187$ or 1.87%.

**Make a decision:**

Set α = 0.05. The p-value is 0.0187. Since 0.0187 < 0.05, reject $H_0$.

**Conclusion:**

At the 5% significance level, there is sufficient evidence to conclude that Jeffrey's mean swimming time is less than 16.43 seconds with the goggles. The data support Frank's belief.

### The one-tailed vs. two-tailed distinction

When the alternative hypothesis is directional (μ > μ₀ or μ < μ₀), all the rejection probability goes into one tail. When the alternative is non-directional (μ ≠ μ₀), it splits.

This has a practical consequence: for the same α and the same test statistic, a one-tailed test is more likely to reject the null. The critical value is smaller (1.645 instead of 1.96 for α = 0.05). But you pay a cost: you're only looking for deviation in one direction. If the effect goes the other way, you'll miss it even if it's real.

### Common misconceptions

**"A p-value of 0.045 means there's a 4.5% chance the null hypothesis is true."** No. It means: if the null is true, there's a 4.5% chance of observing data this extreme or more extreme. Very different. The p-value is about the data given the null, not the null given the data.

**"A p-value of 0.045 with α = 0.05 means we barely rejected the null, so the effect is small."** Not necessarily. The p-value measures rarity, not size. A tiny p-value with a large sample size can accompany a small practical effect. A large p-value can hide a meaningful effect that you didn't have the power (sample size) to detect.

**"Statistical significance means practical significance."** No. A drug that reduces pain by 0.2 points on a 100-point scale might be statistically significant (p < 0.05) with a large enough sample, but it's not clinically meaningful. Size and significance are different questions.

---

## Concept 3 — Hypothesis Tests for Means and Proportions

**Cold open: The machinery works across many contexts**

Whether you're testing whether a new sales trainee meets the company standard, whether a manufacturing machine is calibrated correctly, or whether a public health intervention is effective, the logic is identical. What changes is which distribution you use—the z-distribution or the t-distribution—and which parameter you're testing (mean or proportion). But the five-step procedure applies everywhere.

### Hypothesis tests for a single population mean

You have three scenarios, determined by sample size and whether you know the population standard deviation.

**If σ is known and n is large (≥ 30), or the population is normal regardless of n:**

Use the z-test:

$$Z = \frac{\bar{x} - \mu_0}{\sigma/\sqrt{n}}$$

Critical values come from the standard normal table.

**If σ is unknown and n is small (< 30):**

Substitute the sample standard deviation $s$ for σ and use the Student's t-distribution:

$$t = \frac{\bar{x} - \mu_0}{s/\sqrt{n}}$$

degrees of freedom: $df = n - 1$

Critical values come from the t-table with $df = n - 1$. The t-distribution is wider and flatter than the normal (shorter tails), which accounts for the extra uncertainty from estimating σ. As $n$ grows, the t-distribution approaches the normal.

**If σ is unknown and n is large (≥ 30):**

You can use either approach. Many statisticians use the z-test and substitute $s$ for σ, because with large $n$, the t-distribution is very close to normal. Others use the t-test because it's technically more precise. Both are defensible.

#### A worked example—Sales and company standards

Jasmine is new to the sales team. Company policy requires new hires to close contracts averaging at least $100 over their trial period. In 16 sales calls, Jasmine closed contracts for a mean value of $108, with a sample standard deviation of $12.

Does she meet the standard at the 95% confidence level (α = 0.05)?

**Set up the test:**

$H_0: \mu \leq 100$ (she hasn't met the standard)

$H_a: \mu > 100$ (she has met the standard)

This is a one-tailed test (right tail).

**Choose the test statistic:**

$n = 16$ (small), σ unknown. Use the t-test with $df = 15$.

$$t = \frac{108 - 100}{12/\sqrt{16}} = \frac{8}{3} = 2.67$$

**Find the critical value:**

For $df = 15$ and α = 0.05 (one-tailed, right tail), the critical value is $t_{0.05, 15} = 1.753$.

**Make a decision:**

The calculated t-statistic (2.67) exceeds the critical value (1.753). Reject $H_0$.

**Conclusion:**

At the 5% significance level, there is sufficient evidence to conclude that Jasmine's mean contract value exceeds $100. She meets the company standard.

### Hypothesis tests for a single population proportion

Testing a proportion follows the same logic, but uses a different test statistic based on the binomial distribution approximated by the normal.

When testing a claim about the proportion $p$ of successes in a population:

Set up $H_0: p = p_0$ (or ≤ or ≥) and $H_a: p \neq p_0$ (or > or <).

Conditions: The sample size must be large enough that $np' > 5$ and $nq' > 5$, where $p' = x/n$ is the sample proportion and $q' = 1 - p'$.

Test statistic:

$$Z = \frac{p' - p_0}{\sqrt{\frac{p_0 q_0}{n}}}$$

where $q_0 = 1 - p_0$.

This z-score tells you how many standard deviations the sample proportion is from the hypothesized proportion.

#### A worked example—Bank lending practices

A bank believes 50% of first-time borrowers take out smaller loans than other borrowers. They sample 100 first-time borrowers and find 53 took out smaller loans. Test whether the proportion differs from 50% at the 5% significance level.

**Set up the test:**

$H_0: p = 0.50$

$H_a: p \neq 0.50$

Two-tailed test.

**Check the condition:**

$np' = 100 \times 0.53 = 53 > 5$ ✓

$nq' = 100 \times 0.47 = 47 > 5$ ✓

**Calculate the test statistic:**

$$Z = \frac{0.53 - 0.50}{\sqrt{\frac{0.50 \times 0.50}{100}}} = \frac{0.03}{0.05} = 0.60$$

**Find the critical values:**

For a two-tailed test with α = 0.05, the critical values are ±1.96.

**Make a decision:**

The calculated z-statistic (0.60) lies between the critical values (−1.96 and 1.96). Fail to reject $H_0$.

**Conclusion:**

At the 5% significance level, there is insufficient evidence to conclude that the proportion of first-time borrowers taking out smaller loans differs from 50%. The data are consistent with the bank's belief.

### Common misconceptions

**"A larger sample always leads to rejecting the null."** No. A larger sample gives you more power to detect a true effect, but it doesn't make you reject a null that's actually true. If the null is true, a larger sample is more likely to show data very close to the null, reinforcing the decision not to reject.

**"The t-test is always safer than the z-test."** The t-test is technically more appropriate when σ is unknown and n is small, because it accounts for the extra uncertainty. But with large n, the two are nearly identical, and the choice between them is a minor detail.

**"A test for a proportion requires the data to be normally distributed."** No. The test assumes the population proportion has a binomial distribution. You approximate it with normal via the central limit theorem. The data themselves don't have to be normally distributed; the population of successes/failures does, which is a different thing.

---

## Integration: The Five-Step Procedure, Replication Crisis, and P-Hacking

You now have the pieces. Here's how they fit together.

### The five-step procedure for any hypothesis test

This template works for every hypothesis test you'll ever conduct.

**Step 1: State the null and alternative hypotheses.** Review the question. What parameter is being tested (mean, proportion)? Is this a claim about a specific value, or a direction? Write $H_0$ and $H_a$ carefully.

**Step 2: Set the level of significance (α).** This is a policy decision. Common choices are 0.05 (5%), 0.01 (1%), and rarely 0.10 (10%). Higher α means easier rejection, more power, but higher Type I error risk. Choose based on the consequences of false rejection.

**Step 3: Select the test statistic and find the critical value.** Based on the hypotheses and sample size, choose z or t. Sketch the distribution, mark the critical value(s), and shade the rejection region.

**Step 4: Calculate the test statistic from your data.** Use the sample mean (or proportion), sample standard deviation, and sample size to compute the statistic. Mark it on the sketch.

**Step 5: Reach a conclusion.** If the test statistic is in the rejection region (or p-value < α), reject $H_0$. Write two statements: one formal ("At the 5% significance level, there is sufficient evidence to conclude..."), one action-oriented ("The machine is miscalibrated and requires adjustment").

### The replication crisis and the misuse of p-values

Here's where the method meets reality. Hypothesis testing works beautifully in theory. In practice, it has become a source of false claims.

The problem: If you run 20 hypothesis tests, all testing null hypotheses that are actually true (no real effect), you expect 1 to 2 to be "statistically significant" just by chance (that's what α = 0.05 means). But if you publish only the tests that come out significant, readers see evidence of effects that don't actually exist. This is p-hacking: running many tests, adjusting the analysis in ways that aren't pre-specified, and reporting only what worked. It's not lying—it's a misuse of the method.

The replication crisis in psychology, medicine, and other fields arose partly from this. A stunning result published in a prestigious journal couldn't be replicated when an independent lab tried. Why? Because the original researchers ran dozens of tests (some explicitly, some implicitly by trying different data transformations), and p-values alone don't distinguish real effects from noise when you've done multiple comparisons.

How to protect yourself:
- Pre-register your test: write down your hypothesis and analysis plan before looking at the data.
- Report the actual p-value, not just "significant" or "not significant." A p-value of 0.049 and 0.0001 are both < 0.05, but they tell different stories.
- If you run multiple tests, adjust α (the Bonferroni correction: divide α by the number of tests).
- Replicate when possible. One study with p < 0.05 is interesting. Independent replication is convincing.
- Remember that "not significant" doesn't mean the null is true. It means you didn't gather enough evidence to reject it yet.

### Common misconceptions

**"The p-value is the probability that my result happened by chance."** Ambiguous and misleading. The p-value is the probability of the data given the null. All data happen to some probability; the question is whether they're consistent with the null or whether they contradict it so sharply that the null becomes unbelievable.

**"A p-value is garbage if you didn't pre-register your test."** Not garbage, but less trustworthy. Pre-registration commits you to a single test, so the p-value accurately describes the probability of that specific data under the null. Without pre-registration, you've implicitly run multiple tests, and the p-value alone can't tell readers how many.

**"Significance level α is an objective property of data."** No. α is a choice you make before the test. Different fields, different risk tolerances, lead to different choices. Drug approval might demand α = 0.01 (very strong evidence). Marketing research might accept α = 0.10 (you're more willing to try something that might not work).

---

## Synthesis and Implications

You now understand the machinery of hypothesis testing well enough to apply it, critique it, and recognize when it's being misused.

The core idea is simple: the status quo is presumed true. It takes strong evidence—evidence rarer than α allows—to reject it. You control how high the bar is by choosing α. You choose based on the consequences of false rejection. A test of whether a parachute works should demand very strong evidence before approval. An experiment exploring whether a new marketing approach might increase clicks can accept weaker evidence because the stakes are lower.

The method is powerful because it's rigorous. But it's also been distorted by misunderstanding p-values and by the pressure to publish surprising findings. As you apply this method—in science, in policy, in business—remember what it can and cannot do. It can tell you whether data are consistent with a hypothesis. It cannot prove the hypothesis is true. It cannot tell you whether an effect matters, only whether it's rare under the null. And it assumes that you tested the hypothesis you stated, not that you tested everything and reported what worked.

The example of the FDA committee matters not because they apply formulas, but because they understand the logic. They demand strong evidence before approving a drug because the alternative—approving something that doesn't work—can harm people who might have tried something effective instead. The statistical test is the machinery. Understanding what it means, and what it doesn't mean, is the skill.

---

## Exercises

### Warm-up

**Exercise 9.1** *(LO: state hypotheses correctly.)* For each scenario, write the null and alternative hypotheses. State whether it's a one-tailed or two-tailed test.

(a) A company claims its new battery lasts longer than 40 hours. You want to test this claim.

(b) A researcher tests whether the mean height of students in a college differs from the national average of 67 inches.

(c) A manufacturer tests whether the proportion of defective items is at most 2%.

**Exercise 9.2** *(LO: distinguish Type I and Type II errors.)* For the battery scenario in 9.1(a), describe a Type I error and a Type II error in context. Which is worse, and why?

**Exercise 9.3** *(LO: compute a z-statistic.)* A sample of 64 students has a mean test score of 72 with a standard deviation of 8. The population standard deviation is known to be 8. Test whether the mean score differs from 70 at the 5% significance level. Compute the z-statistic.

### Application

**Exercise 9.4** *(LO: conduct a t-test for a mean.)* A coffee shop claims its employees' mean time to prepare a cappuccino is 3.5 minutes. A quality auditor samples 16 cappuccinos and finds a mean preparation time of 3.8 minutes with a standard deviation of 0.6 minutes. At the 5% significance level, test whether the mean time exceeds 3.5 minutes. State your conclusion.

**Exercise 9.5** *(LO: conduct a test for a proportion.)* A political poll claims 45% of voters support a ballot measure. A journalist surveys 200 voters and finds 98 support it. Test whether the true proportion differs from 45% at the 5% significance level. State the null and alternative hypotheses, calculate the z-statistic, and state your conclusion.

**Exercise 9.6** *(LO: interpret p-values correctly.)* A researcher reports a p-value of 0.032 for a two-tailed test with α = 0.05. What does this p-value tell you? Should you reject the null? Explain what the p-value does and does not mean.

### Synthesis

**Exercise 9.7** *(LO: apply the five-step procedure.)* Lake Tahoe Community College (LTCC) tracks student sleep hours. A study claims LTCC students sleep less than 7 hours per night on average. A sample of 22 students yields a mean of 7.24 hours with a standard deviation of 1.93 hours. At the 5% significance level, does the data support the claim that students sleep less than 7 hours? Conduct the full five-step test.

**Exercise 9.8** *(LO: recognize p-hacking and replication issues.)* A marketing team runs hypothesis tests on 10 different advertising approaches, each at the 5% significance level. One approach shows p = 0.047. They declare it the winner and launch the campaign. What's wrong with this logic? How could they improve it?

### Challenge

**Exercise 9.9** *(LO: connect to real stakes and trade-offs.)* A new screening test for a disease is proposed. The manufacturer claims it correctly identifies the disease 95% of the time. In practice, you're testing whether the sensitivity (proportion of true positives) is at least 0.95. If you set α = 0.01, you make false rejection rare. But what happens to the Type II error risk? Why might a doctor prefer to increase α (say, to 0.10) for this test?

**Exercise 9.10** *(LO: critical thinking on statistical claims.)* You read a news article: "Study shows dark chocolate improves heart health: p < 0.05." What would you want to know before changing your diet? What does the p-value not tell you about the effect size, the sample, or the real-world importance of the finding?

---

## Chapter summary

You can now do three things you couldn't do before reading this chapter.

You can **set up a hypothesis test** by identifying the null and alternative hypotheses, distinguishing one-tailed from two-tailed tests, and understanding the asymmetry of the framework: the status quo has the advantage, and the burden of proof lies with anyone seeking to overthrow it.

You can **conduct a hypothesis test** by choosing the appropriate test statistic (z or t), computing it from your sample data, comparing it to a critical value or computing a p-value, and reaching a conclusion with clear language about what you found and what action follows.

You can **interpret a p-value correctly** and recognize when it's being misused. You understand that the p-value is the probability of data this extreme if the null is true, not the probability that the null is true given the data. You recognize that statistical significance and practical significance are different. You know that p-hacking—running many tests and reporting only the significant ones—inflates false findings.

Most importantly, you understand that hypothesis testing is not magic. It's a disciplined way of asking "Is the evidence strong enough to change my mind?" The discipline protects against wishful thinking and random chance. But the method assumes honesty: that you test what you claim to test, not that you test everything and report what worked.

What you should now be able to teach a friend: why the null hypothesis always gets the benefit of the doubt; what a p-value actually measures; why you can't drive both Type I and Type II error rates to zero; and how to spot when hypothesis tests are being misused to create false certainty.

---

## Connections forward

In this chapter, you tested claims about a single population parameter (mean or proportion). In Chapter 10, you'll test whether two populations differ. The logic is identical; the machinery extends. In Chapter 11, you'll test whether categories are independent (chi-square). In Chapter 12, you'll test whether more than two groups differ in their means (ANOVA). All follow the same five-step structure.

But the more immediate connection is to the replication crisis and the careful use of p-values. As you encounter claims throughout your career—in medicine, policy, science, business—you'll ask: was this tested once or repeatedly? Was the test pre-registered or discovered after the fact? How large is the effect, not just how unlikely? Is it reproducible? These are the questions that distinguish real findings from statistical artifacts.

The FDA committee that votes on a new drug uses this logic. A researcher designing an experiment uses it. A manufacturer tracking machine calibration uses it. You now speak their language and can judge the strength of their evidence.

---

## What would change my mind

A study showing that p-values calculated post-hoc (after data collection), without pre-registration, are systematically inflated would challenge the emphasis I've placed on pre-registration. Evidence that null hypotheses are true more often in practice than the literature suggests would deepen concern about Type I error. Conversely, a demonstration that pre-registration eliminates the replication crisis would strongly support the recommendations in the "Integration" section.

## Still puzzling

I don't fully understand why the p-hacking problem persists even in fields where it has been thoroughly documented. There are plausible explanations (publish-or-perish pressure, confirmation bias, misunderstanding of p-values), but I haven't found a study that measures which factors matter most or how to effectively counter them without relying solely on better statistical literacy.

---

## Tags

hypothesis testing, null hypothesis, p-values, Type I error, Type II error, test statistic, z-test, t-test, proportion test, statistical significance, replication crisis, p-hacking, one-sample inference

---

## LLM Exercise — Chapter 9: Hypothesis Testing with One Sample (Analyze One Dataset Project)

**Project:** Analyze One Real Dataset.
**What you're building this chapter:** the first hypothesis test — testing a specific claim about your dataset.
**Tool:** **Claude Code** + **Claude Project**.

---

**The Prompt:**

```
Chapter 9 of my Analyze-One-Dataset project. Chapter 9 covered
the four-step hypothesis-test procedure:
1. State H₀ and H_a (and decide one-tailed vs. two-tailed).
2. Compute the test statistic (t for means; z for proportions).
3. Find the p-value (probability of test statistic this extreme
   or more, under H₀).
4. Compare p-value to α (typically 0.05); reject H₀ if p < α,
   else fail to reject.
Type I error (false positive: reject H₀ when it's true) probability
= α. Type II error (false negative: fail to reject H₀ when it's
false) probability = β. Power = 1 − β. The p-value is NOT the
probability H₀ is true; it's the probability of seeing data this
extreme IF H₀ were true.

Write the brief's "One-Sample Hypothesis Test" section in 500-800
words.

1. **State a specific claim to test.** Pick a defensible
   benchmark — a population mean someone has claimed, a
   proportion threshold (e.g., is the proportion of X different
   from 0.50?), a regulatory standard, a previously-published
   result.

2. **State the hypotheses formally.**
   - H₀: parameter = specific value (the no-effect statement).
   - H_a: parameter ≠ specific value (two-tailed) OR > / <
     (one-tailed, justified by directional theory).
   - Significance level α (typically 0.05).

3. **Compute the test statistic.**
   - For one-sample t-test (mean): t = (x̄ − μ₀) / (s/√n).
   - For one-sample z-test (proportion): z = (p̂ − p₀) /
     √(p₀(1−p₀)/n).
   - Show the computation with actual numbers.

4. **Find the p-value.**
   - For t-test: use scipy.stats.t (sf for upper, 2× for two-
     tailed).
   - For z-test: use scipy.stats.norm.
   - Report the p-value to 3-4 decimal places.

5. **Make and interpret the decision.**
   - "Reject H₀" or "Fail to reject H₀."
   - State the conclusion in plain language: "the data provide
     [strong / moderate / weak / no] evidence against the
     null hypothesis that [restate]."
   - Do NOT say "accept H₀" — failing to reject is not the same
     as proving the null.

6. **Discuss error risk.** With α = 0.05, what's the probability
   we made a Type I error (assuming H₀ is actually true)? What
   could we say about Type II error (we'd need to specify the
   true parameter to compute it)?

End with: how would the conclusion change if we used α = 0.01
instead? What does the interplay between α and conclusion say
about "significance" as a discipline?
```

---

**What this produces:** A 500-800 word section with one formal hypothesis test. The p-value-interpretation discipline is the most consequential output.

**How to adapt this prompt:**

- *For your own project:* The test should answer a real question. A "test for the sake of testing" produces sterile output.
- *For ChatGPT / Gemini:* Works as written.
- *For Claude Code:* `scipy.stats.ttest_1samp(data, popmean)` for the one-liner. Building from scratch teaches the underlying mechanics.
- *For a Claude Project:* Append.

**Connection to previous chapters:** Ch 8's CIs and Ch 9's tests are dual: if the null value is outside the 95% CI, then p < 0.05. Verify this on your data.

**Preview of next chapter:** Chapter 10 covers two-sample tests. You'll compare two groups in your dataset.


---

## 🕰️ AI Wayback Machine

**William Gosset** was wrote as "Student" while working at Guinness — and introduced the t-test in 1908 to handle small-sample inference.

**Run this:**

```
Who is William Gosset, and how does their work connect to hypothesis testing we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"William Gosset"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply William Gosset's framework to a small dataset you actually have.
- Add a constraint: "Answer including criticisms or limits of William Gosset's framework."

What changes? What gets better? What gets worse?
