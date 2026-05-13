# Chapter 4 — Discrete Random Variables

## Three title options

1. **Counting What Happens: From binomial trials to Poisson arrivals — probability distributions that match the real world**
2. **The Math of Discrete Outcomes: Why some probabilities follow patterns, and how to recognize which ones**
3. **What You Can Count: When trials are independent, how distributions emerge from them**

---

## TL;DR

A random variable translates the uncertain outcome of an experiment into a number. For discrete random variables—those that land on whole-number values—we can write down every possible outcome and its probability, creating a probability distribution. The binomial distribution handles repeated independent trials with two outcomes (success/failure) and fixed sample size. The Poisson distribution handles rare, independently occurring events in a fixed interval of time or space. When you know which distribution governs a situation, you can calculate not just individual probabilities but the expected average outcome and how much variation to expect around that average.

---

## Cold open: The factory floor, 4 p.m.

A quality-control engineer at a manufacturing plant sits at a desk with a stack of printed circuit boards, freshly pulled from the assembly line. She's inspecting them for defects. She knows from months of data that about 3% of boards leave the line with a visible flaw. She needs to sample 50 boards. She has three questions. First: what's the probability that exactly two of the 50 boards are defective? Second: if I'm pulling boards one at a time, rejecting each defective one and returning it to production, what's the probability I'll have to pull ten boards to find the first good one? Third: on average, across many batches of 50, how many defects should I expect to see?

This is not abstraction. The engineer's salary, the plant's reputation, the customer's decision whether to buy, all hang on what these numbers say.

The mathematics that answers those questions is the subject of this chapter. It begins with a simple idea—a rule for translating random outcomes into numbers — and builds to three practical distributions that appear, again and again, whenever you have independent trials, when you're counting rare events, or when you're asking "how long until success?" The machinery is not hard. The payoff is that you stop guessing about what the data will do and start predicting it.

### Learning objectives

By the end of this chapter you will be able to:

- **Define** a discrete random variable and **distinguish** it from a continuous one by identifying the sample space.
- **Construct** a probability mass function (PMF) for a discrete random variable and **verify** that probabilities sum to one.
- **Calculate** the expected value (mean) and variance of a discrete random variable, both from first principles and using distribution formulas.
- **Recognize** when a situation fits the binomial model, and **apply** the binomial formula to compute probabilities, $\mu$, and $\sigma$.
- **Apply** the Poisson distribution to model rare events in fixed intervals and **explain** when it approximates the binomial.
- **Solve** practical problems in quality control, clinical trials, and operational planning using discrete distributions.

### Prerequisites

- Comfort with probability notation ($P(A)$, union, intersection, complement) from Chapter 3.
- Arithmetic with fractions and decimals.
- The combinatorial formula $\binom{n}{x} = \frac{n!}{x!(n-x)!}$, re-introduced when needed.

### Why this chapter matters

Most real-world problems don't hand you a smooth curve. They hand you counts: defects per batch, successes per trial, arrivals per hour, infections per control group. These are discrete outcomes. Once you see the pattern — recognize which distribution governs the situation — you can shift from "let me guess" to "the mathematics says the probability is this, the expected value is that." That shift is where statistics becomes useful. In the clinic, a researcher uses the binomial distribution to ask whether a drug's success rate is better than placebo's. In the call center, a manager uses the Poisson distribution to decide how many lines to install. In the quality lab, the engineer uses the binomial to decide when a batch is safe to ship.

---

## Concept 1 — What a random variable is, and how to write down its probability

**Cold open: The study that could change practice**

A pharmaceutical company runs a trial of a new vaccine. Fifty thousand people get the vaccine; fifty thousand get a placebo. The researchers count how many people in each group get sick. The count itself is the random variable — before the trial happens, the number is uncertain; after the trial, it's a number written down. The researchers need to talk about this number, calculate its probability under different assumptions, and decide whether the evidence is strong enough to change medicine.

The language they use is the language of random variables. It lets them be precise about what they're measuring and what the uncertainty means.

### Definition and notation

A **random variable** — abbreviated RV, usually written as an uppercase letter like $X$, $Y$, or $Z$ — is a rule that assigns a number to each outcome in the sample space. The sample space is the set of all possible outcomes of an experiment. Once the outcome happens, the random variable takes on a specific value, written in lowercase: $x$, $y$, or $z$.

Example: Flip three fair coins. The sample space is the set of all 8 outcomes: $\{TTT, TTH, THT, THH, HTT, HTH, HHT, HHH\}$. Define the random variable $X$ as the number of heads. After flipping, if you get $HTH$, then the random variable $X$ takes the value $x = 2$.

A **discrete random variable** is one that can take on only countable values — usually whole numbers. Think of it as something you can list or count. The number of heads in three flips ($0, 1, 2, 3$) is discrete. The number of defects on a circuit board is discrete. The number of patients arriving at an emergency room in one hour is discrete.

A **continuous random variable** takes on any value in some interval — including decimals and fractional parts. The height of an adult male is continuous (you can be 5.7234... feet tall). The time it takes for a radioactive atom to decay is continuous. We defer continuous random variables to Chapter 5; this chapter focuses on discrete.

### The probability mass function

For a discrete random variable $X$, we want to know the probability of each possible value. The **probability mass function** (PMF), written $P(X = x)$ or $P(x)$ for short, gives us that.

A valid PMF for a discrete random variable $X$ must satisfy two properties:

1. **Each probability is between 0 and 1 (inclusive).** $0 \leq P(x) \leq 1$ for all $x$.
2. **The probabilities sum to exactly 1.** $\sum P(x) = 1$ — because some outcome must occur.

Example: A quality engineer inspects light bulbs off an assembly line. The probability that a bulb is defective is 0.05; the probability that it works is 0.95. Define $X$ as the outcome: $X = 0$ if the bulb works, $X = 1$ if it's defective.

$$P(X = 0) = 0.95, \quad P(X = 1) = 0.05$$

Check: $0.95 + 0.05 = 1.00$. The PMF is valid.

### Named random variables and parametric families

When a random variable follows a recognized pattern, we give it a name and note its parameters. For instance, $X \sim \text{Binomial}(n, p)$ means "$X$ has a binomial distribution with $n$ trials and probability of success $p$." The tilde $\sim$ reads as "is distributed as."

The parameter notation matters. In binomial distributions, once you know $n$ and $p$, you know everything about the distribution—every probability, the mean, the standard deviation. We'll see this pattern again with Poisson and geometric distributions.

### Worked example — constructing a PMF from observation

A bakery tracks daily croissant sales. Over the past month, the baker sold exactly 1 batch (4 dozen) on 15 days, 2 batches on 22 days, 3 batches on 10 days, and 4 batches on 3 days.

**Define the random variable:** Let $X =$ the number of batches sold on a randomly selected day.

**Calculate probabilities from the data:** Total days in sample: $15 + 22 + 10 + 3 = 50$.

$$P(X = 1) = \frac{15}{50} = 0.30$$
$$P(X = 2) = \frac{22}{50} = 0.44$$
$$P(X = 3) = \frac{10}{50} = 0.20$$
$$P(X = 4) = \frac{3}{50} = 0.06$$

**Verify the PMF:** $0.30 + 0.44 + 0.20 + 0.06 = 1.00$. ✓

**Interpret:** On a randomly selected day, the baker is most likely to sell 2 batches (probability 0.44) and least likely to sell 4 (probability 0.06).

This PMF summarizes the observed distribution. If the baker's demand is stable, this distribution forecasts future sales.

### Common misconceptions

**A random variable is not an unknown in algebra.** In algebra, $x$ is a placeholder you solve for. In probability, $X$ is a random variable—a rule connecting outcomes to numbers—and $x$ is a specific value it can take. The randomness is not because you don't know the answer; it's because the outcome of the experiment is genuinely uncertain.

**Not all probability functions are valid.** A collection of numbers $p_1, p_2, \ldots$ is a valid PMF only if each is between 0 and 1, and they sum exactly to 1. If a proposed PMF has a probability greater than 1 or if the probabilities sum to 0.95, it's not valid; you have to revise.

**The sample space and the random variable are different things.** The sample space is the set of all possible outcomes (e.g., the eight outcomes of three coin flips). The random variable is the rule that assigns numbers to those outcomes (e.g., "count the heads"). Don't confuse them.

---

## Concept 2 — Expected value and variance: What to expect on average

**Cold open: The decision you make with one number**

A pharmaceutical company is deciding whether to buy the rights to a drug candidate. The drug will cost $10 million to bring to market. If it succeeds, it will generate $80 million in revenue. If it fails, $0. The company estimates success at 60% based on Phase II trials. Should they buy?

A naive answer is "yes, because 60% is more than 50%." The right answer requires Expected Value. You take a weighted average: $0.6 \cdot 80 + 0.4 \cdot 0 = 48$ million. Subtract the $10 million cost: net $38 million expected profit. That calculation — averaging outcomes weighted by their probability — is the foundation of rational decision-making under uncertainty.

### Definition of expected value

The **expected value** of a discrete random variable $X$, written $E(X)$ or $\mu$ (mu, the Greek letter for population mean), is the long-run average of $X$ across many repetitions of the experiment. It's computed as:

$$E(X) = \mu = \sum x \cdot P(x)$$

where the sum is over all possible values $x$.

Etymology: "Expected" comes from *expectare*, Latin for "to look out for" or "to anticipate." It's what you expect, on average, when you repeat the experiment many times.

### Interpreting expected value

Expected value is not necessarily a value the random variable actually takes. If you flip a coin and bet $1 that it's heads (win) or lose $1 (tails), the expected value of your payoff is:

$$E(\text{payoff}) = 1 \cdot 0.5 + (-1) \cdot 0.5 = 0$$

But you never actually win or lose $0 on a single flip — you win or lose $1. Expected value is the balance point: if you play this game 1,000 times, you'll break even.

### Definition of variance and standard deviation

The **variance** of $X$, written $\text{Var}(X)$ or $\sigma^2$ (sigma-squared), measures how spread out the distribution is around the mean. Large variance means outcomes are far from $\mu$; small variance means they cluster near $\mu$.

$$\text{Var}(X) = \sigma^2 = \sum (x - \mu)^2 \cdot P(x)$$

The **standard deviation**, $\sigma$, is the square root of variance:

$$\sigma = \sqrt{\sigma^2}$$

Standard deviation is easier to interpret because it's in the same units as $X$. If $X$ is measured in defects, $\sigma$ is also in defects; if $X$ is measured in patients, $\sigma$ is in patients.

### Worked example — computing expected value and variance

A nurse estimates the number of patients arriving at the emergency room on a Saturday night. Data from the past month gives the PMF:

| $x$ | 10 | 15 | 20 | 25 |
|-----|----|----|----|----|
| $P(x)$ | 0.20 | 0.35 | 0.30 | 0.15 |

**Expected value:**

$$E(X) = 10 \cdot 0.20 + 15 \cdot 0.35 + 20 \cdot 0.30 + 25 \cdot 0.15$$
$$= 2 + 5.25 + 6 + 3.75 = 17$$

On average, the ER sees 17 patients on a Saturday night.

**Variance:** First, compute $(x - \mu)^2$ for each value:

| $x$ | 10 | 15 | 20 | 25 |
|-----|----|----|----|----|
| $(x - 17)^2$ | 49 | 4 | 9 | 64 |
| $P(x)$ | 0.20 | 0.35 | 0.30 | 0.15 |

$$\text{Var}(X) = 49 \cdot 0.20 + 4 \cdot 0.35 + 9 \cdot 0.30 + 64 \cdot 0.15$$
$$= 9.8 + 1.4 + 2.7 + 9.6 = 23.5$$

**Standard deviation:**

$$\sigma = \sqrt{23.5} \approx 4.85$$

**Interpretation:** The expected arrival count is 17 patients. Typically, arrivals deviate from this by about 4.85 patients. The nurse knows that some nights will bring 12–13 patients (around $17 - 4.85$) and others 22–23 ($17 + 4.85$). This variation is what she needs to staff for.

### Common misconceptions

**Expected value is not the "most likely" outcome.** If $X$ can take values 1, 5, 10 with probabilities 0.4, 0.4, 0.2, the expected value is $E(X) = 1 \cdot 0.4 + 5 \cdot 0.4 + 10 \cdot 0.2 = 4.4$. The value 5 is most likely (probability 0.4), but the expected value is 4.4, which is not even one of the possible values.

**Variance is not the same as standard deviation.** Variance is in squared units; standard deviation is in the original units. If you're counting defects, report standard deviation (defects), not variance (defects-squared).

**Expected value doesn't guarantee a stable outcome.** If you flip a coin and bet $1 that it's heads (win) or lose $1 (tails), the expected payoff is $0, but each flip pays either $+1$ or $-1$, never $0. Over many flips, the average approaches $0, but any single flip is uncertain.

---

## Concept 3 — The binomial distribution: The workhorse for independent trials

**Cold open: The moment of decision in the vaccine trial**

A vaccine trial has enrolled 100 health-care workers. The researchers give 50 the vaccine and 50 a placebo. After three months, they count infections. The vaccine group had 2 infections; the placebo group had 8. Is this evidence that the vaccine works? Or is it just random luck?

To answer that question, the researchers need to know: if the vaccine offered no protection at all (same infection rate for both groups), what's the probability of seeing results this different or more extreme? That calculation rests on the binomial distribution. It tells you the probability of a specific number of successes when you repeat a binary experiment (success/failure) a fixed number of times, with a constant probability of success on each trial.

### Conditions for a binomial experiment

An experiment is **binomial** if it satisfies four conditions:

1. **Fixed number of trials.** You perform the experiment exactly $n$ times. No more, no fewer.
2. **Two outcomes per trial.** Each trial results in "success" or "failure" — or more generally, "outcome A" or "outcome B." Binary means exactly two categories.
3. **Constant probability.** The probability of success, $p$, is the same on every trial. This is what "independent" means: the outcome of one trial doesn't change the probability on the next trial.
4. **Independent trials.** The result of one trial does not influence the result of another. (This is a consequence of condition 3, but it's important to state explicitly.)

**Not binomial:** Rolling a die until you see a 6 (no fixed number of trials). Drawing cards from a deck without replacement (probabilities change with each draw). A survey of customer satisfaction with ordered categories: highly satisfied, satisfied, neutral, dissatisfied, highly dissatisfied (more than two outcomes).

**Binomial:** Flipping a coin 10 times (heads/tails, $p = 0.5$, $n = 10$). Testing 50 circuit boards and counting defects (defective/working, $p = 0.05$, $n = 50$). Surveying 200 voters on a yes/no ballot proposition (yes/no, $p = $ historical turnout rate, $n = 200$).

### The binomial formula

If $X$ is the number of successes in $n$ independent trials, each with probability $p$, then $X$ has a binomial distribution, written $X \sim \text{Binomial}(n, p)$. The probability that $X = k$ (exactly $k$ successes) is:

$$P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$$

where $\binom{n}{k} = \frac{n!}{k!(n-k)!}$ is the number of ways to choose $k$ successes from $n$ trials.

The formula has three parts:
- $\binom{n}{k}$: the number of orderings (sequences) that have exactly $k$ successes.
- $p^k$: the probability of getting $k$ successes in a row.
- $(1-p)^{n-k}$: the probability of getting $n-k$ failures in a row.

The three parts multiply because the events are independent.

### Mean and variance of the binomial

If $X \sim \text{Binomial}(n, p)$, then:

$$\mu = E(X) = np$$

$$\sigma^2 = \text{Var}(X) = np(1-p)$$

$$\sigma = \sqrt{np(1-p)}$$

These formulas are not just convenient—they tell you something important. The expected number of successes grows linearly with $n$ (more trials, more successes expected). The variance also grows with $n$, but the standard deviation grows with $\sqrt{n}$ (the relative variability decreases as $n$ increases — this is the law of large numbers at work).

### Worked example — calculating binomial probabilities

A public health officer is preparing for flu season. Historical data shows that the flu vaccine is 70% effective — that is, it prevents infection in 70% of vaccinated people. A clinic vaccinated 20 people. What is the probability that at least 15 of them avoid the flu?

**Setup:**
- $n = 20$ trials (patients vaccinated)
- $p = 0.70$ probability of success (vaccine prevents infection)
- $q = 1 - p = 0.30$ probability of failure
- Question: $P(X \geq 15)$ where $X =$ number who avoid the flu

**Approach:** $P(X \geq 15) = P(X = 15) + P(X = 16) + \cdots + P(X = 20)$.

**Calculate $P(X = 15)$:**

$$P(X = 15) = \binom{20}{15} (0.70)^{15} (0.30)^5$$

$\binom{20}{15} = \binom{20}{5} = \frac{20!}{5! \cdot 15!} = 15{,}504$

$(0.70)^{15} \approx 0.0047$

$(0.30)^5 \approx 0.00243$

$$P(X = 15) \approx 15{,}504 \cdot 0.0047 \cdot 0.00243 \approx 0.1789$$

(In practice, you'd use a calculator or software for these computations; the exact values are $P(X = 15) \approx 0.1789$.)

Similarly, $P(X = 16) \approx 0.1304$, $P(X = 17) \approx 0.0716$, $P(X = 18) \approx 0.0278$, $P(X = 19) \approx 0.0068$, $P(X = 20) \approx 0.0008$.

$$P(X \geq 15) \approx 0.1789 + 0.1304 + 0.0716 + 0.0278 + 0.0068 + 0.0008 \approx 0.4163$$

**Interpretation:** There's about a 42% chance that at least 15 of the 20 vaccinated people avoid the flu. This is a fairly high probability, but not a certainty—about 3 out of 5 times, we'd expect at least 15 to avoid infection.

**Expected value and standard deviation:**

$$\mu = np = 20 \cdot 0.70 = 14$$

$$\sigma = \sqrt{np(1-p)} = \sqrt{20 \cdot 0.70 \cdot 0.30} = \sqrt{4.2} \approx 2.05$$

The clinic expects 14 people to avoid the flu, with a standard deviation of about 2 people. Most outcomes will fall between 12 and 16 people protected.

### Recognizing the binomial in context

The binomial distribution shows up wherever you have:
- A fixed number of independent trials ($n$).
- Two possible outcomes per trial (success/failure, yes/no, defective/working).
- A constant probability of success ($p$) from trial to trial.

Examples in real applications:
- **Clinical trials:** $n =$ number of patients, success $=$ patient recovers, $p =$ historical recovery rate for the control group.
- **Quality control:** $n =$ number of items sampled, success $=$ item is defect-free, $p =$ historical defect rate (inverted).
- **Polling:** $n =$ number of voters surveyed, success $=$ voter favors candidate, $p =$ true proportion of voters who favor the candidate.
- **Customer satisfaction:** $n =$ number of transactions, success $=$ customer reports being satisfied, $p =$ true satisfaction rate.

### Common misconceptions

**The binomial requires independence, not just "randomness."** Flipping a coin is random and independent; drawing cards from a deck without replacement is random but not independent (the second draw's probabilities depend on the first). The binomial formula fails for the card example.

**Probability of success must be constant.** If you're learning (your skill improves with each trial), the probability changes, and the binomial doesn't apply. In the baseball example, if the batter's skill increases as they warm up, $p$ is not constant across trials.

**"At least" means $\geq$, not $>$.** "$P(\text{at least 15})$" includes 15. "$P(\text{more than 15})$" would be $P(X > 15) = P(X = 16) + P(X = 17) + \cdots$.

---

## Concept 4 — The Poisson distribution: When events occur at a constant average rate

**Cold open: How many calls will arrive in the next hour?**

A telecommunications company operates a customer service line. Data from the past six months shows that calls arrive at an average rate of 12 per hour, and the arrival times are essentially unpredictable — no pattern, no clustering. The manager is deciding how many operators to have on duty during night shifts. To do that, she needs to know: what's the probability that more than 20 calls arrive in a one-hour period? How many operators should she schedule to handle 95% of likely call volumes?

This situation is different from the binomial. There's no fixed number of "trials." Instead, we have a fixed interval (one hour) and a known average rate (12 calls per hour). The right tool is the Poisson distribution.

### When the Poisson applies

The **Poisson distribution** models the number of events occurring in a fixed interval of time or space, given:

1. **Events occur at a constant average rate.** Over long periods, the rate is $\mu$ events per interval (e.g., 12 calls per hour, 2 defects per 100 meters of fabric, 0.5 typos per page).
2. **Events are independent.** The occurrence of one event does not make another event more or less likely in the immediate future. (Call arrivals are independent; customers arriving independently of each other.)
3. **Events are rare relative to the interval.** You're asking for the number of occurrences, not the fraction of time nothing happens. (Defects on a 1000-meter roll are rare compared to the roll's length.)

The Poisson is invaluable in operations: call centers, emergency rooms, web server load, manufacturing defects, network traffic, even the number of goals scored in a soccer match.

### The Poisson formula

If $X$ is the number of events in a fixed interval, and the average rate is $\mu$ (mu, the expected number per interval), then $X$ has a Poisson distribution, written $X \sim \text{Poisson}(\mu)$. The probability that $X = k$ is:

$$P(X = k) = \frac{\mu^k e^{-\mu}}{k!}$$

where $e \approx 2.71828$ is Euler's number (the base of the natural logarithm) and $k! = k \cdot (k-1) \cdot (k-2) \cdots 1$ is the factorial.

Notice: the Poisson has only one parameter, $\mu$. Once you know the average rate, you know the entire distribution.

### Mean and variance of the Poisson

If $X \sim \text{Poisson}(\mu)$, then:

$$E(X) = \mu$$

$$\text{Var}(X) = \mu$$

$$\sigma = \sqrt{\mu}$$

Watch this: the mean and variance are equal. A Poisson distribution with mean 6 has variance 6 and standard deviation $\sqrt{6} \approx 2.45$. This relationship is a hallmark of the Poisson and distinguishes it from the binomial (where variance is $np(1-p)$, not $np$).

### Worked example — applying the Poisson to ER arrivals

An emergency room tracks patient arrivals. On average, 5 patients arrive per hour during the day shift. The manager wants to know two things: (1) What's the probability that exactly 8 patients arrive in the next hour? (2) What's the probability that 5 or fewer patients arrive?

**Setup:**
- $\mu = 5$ (average arrivals per hour)
- Question 1: $P(X = 8)$
- Question 2: $P(X \leq 5)$

**Question 1: $P(X = 8)$**

$$P(X = 8) = \frac{5^8 e^{-5}}{8!}$$

Compute the pieces:
- $5^8 = 390{,}625$
- $e^{-5} \approx 0.00674$
- $8! = 40{,}320$

$$P(X = 8) = \frac{390{,}625 \cdot 0.00674}{40{,}320} \approx \frac{2{,}633}{40{,}320} \approx 0.0653$$

There's about a 6.5% chance that exactly 8 patients arrive in the next hour.

**Question 2: $P(X \leq 5)$**

$$P(X \leq 5) = P(X = 0) + P(X = 1) + P(X = 2) + P(X = 3) + P(X = 4) + P(X = 5)$$

Compute each:
- $P(X = 0) = \frac{5^0 e^{-5}}{0!} = \frac{1 \cdot 0.00674}{1} \approx 0.0067$
- $P(X = 1) = \frac{5^1 e^{-5}}{1!} = \frac{5 \cdot 0.00674}{1} \approx 0.0337$
- $P(X = 2) = \frac{5^2 e^{-5}}{2!} = \frac{25 \cdot 0.00674}{2} \approx 0.0842$
- $P(X = 3) = \frac{5^3 e^{-5}}{3!} = \frac{125 \cdot 0.00674}{6} \approx 0.1404$
- $P(X = 4) = \frac{5^4 e^{-5}}{4!} = \frac{625 \cdot 0.00674}{24} \approx 0.1755$
- $P(X = 5) = \frac{5^5 e^{-5}}{5!} = \frac{3{,}125 \cdot 0.00674}{120} \approx 0.1755$

$$P(X \leq 5) \approx 0.0067 + 0.0337 + 0.0842 + 0.1404 + 0.1755 + 0.1755 \approx 0.616$$

There's about a 62% chance that 5 or fewer patients arrive in the next hour.

**Interpretation:** The mean is 5; the standard deviation is $\sqrt{5} \approx 2.24$. Most hours will see between 3 and 7 arrivals (roughly within one standard deviation of the mean). Hours with 8+ arrivals are less common but definitely possible. The manager might staff for a peak of around 8–9 patients to handle 95% of hours comfortably.

### The Poisson as a limit of the binomial

The Poisson distribution has a deep mathematical relationship to the binomial. If $n$ is large, $p$ is small, and $np = \mu$ is moderate, then:

$$\text{Binomial}(n, p) \approx \text{Poisson}(\mu)$$

Why does this matter? Suppose you're interested in the number of defective items in a batch of 10,000, where the defect rate is 0.001% (1 in 100,000). The binomial setup is $n = 10{,}000$, $p = 0.00001$, $\mu = np = 0.1$. Computing the binomial directly is tedious; using the Poisson with $\mu = 0.1$ is easy and accurate.

The intuition: when $p$ is very small, each trial has almost no chance of success. But with enough trials, some successes will occur. The randomness of when those successes happen is Poisson-like.

### Common misconceptions

**The Poisson doesn't require a fixed number of trials—that's the point.** The binomial fixes $n$. The Poisson fixes the interval (time or space) and the rate. Arrivals at a store: Poisson (we're interested in the count in a fixed hour). Flipping a coin 10 times: binomial (fixed number of flips).

**The Poisson is not the "default" for all count data.** It applies when events are independent and occur at a constant average rate. Defects on a circuit board (Poisson). Customer complaints per day (Poisson, if the rate is stable). But a medical condition that clusters in families (not Poisson—arrivals are not independent). A phenomenon that waxes and wanes seasonally (not Poisson—the rate is not constant).

**Mean and variance being equal is a feature, not a bug.** If your data says the variance is much larger than the mean, the Poisson is the wrong model. This is called "overdispersion" and signals that something is going on beyond simple random arrivals.

---

## Integration: From theory to decision

Return to the quality-control engineer from the opening. The plant produces 50 circuit boards per hour. The defect rate is 3%. The engineer samples 50 boards each shift.

**Question 1: What's the probability that exactly two boards are defective?**

This is binomial with $n = 50$, $p = 0.03$.

$$P(X = 2) = \binom{50}{2} (0.03)^2 (0.97)^{48}$$

Using a calculator: $P(X = 2) \approx 0.2611$. About 26% of the time, the engineer sees exactly two defects.

**Question 2: On average, how many defects should the engineer expect?**

$$\mu = np = 50 \cdot 0.03 = 1.5$$

On average, 1.5 boards per sample are defective.

**Question 3: What's the standard deviation?**

$$\sigma = \sqrt{np(1-p)} = \sqrt{50 \cdot 0.03 \cdot 0.97} = \sqrt{1.455} \approx 1.21$$

Most samples will have between $1.5 - 1.21 = 0.29$ and $1.5 + 1.21 = 2.71$ defects. So typically 0–3 defects per sample of 50.

**The decision:** If the engineer observes 6 defects in a sample of 50, that's about 4 standard deviations above the mean—highly unusual. It signals that something on the line has changed (temperature, humidity, contamination, operator error). The engineer would shut down the line for inspection. If she observes 2 defects, that's within normal variation; production continues.

This is how statistics becomes actionable: you set a baseline (expected value and standard deviation), you collect data, and you decide based on how far the data deviates from the baseline.

---

## Exercises

### Warm-up

**Exercise 4.1** *(LO: construct and interpret a PMF).* A small medical clinic sees 100 patients per week. The clinic tracks the number of patients in each of five age groups: 0–17 (12 patients), 18–34 (28 patients), 35–49 (30 patients), 50–64 (22 patients), 65+ (8 patients).

(a) Define a discrete random variable $X$ for this situation.
(b) Construct the probability mass function (list all probabilities).
(c) Verify that your PMF is valid.

**Exercise 4.2** *(LO: calculate expected value).* A nurse supervisor tracks unplanned absences on a floor. The probability distribution is:

| $x$ (absences) | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| $P(x)$ | 0.40 | 0.35 | 0.20 | 0.05 |

Calculate the expected number of unplanned absences per shift.

**Exercise 4.3** *(LO: identify binomial vs. non-binomial).* For each scenario, state whether it is a binomial experiment. If not, explain why.

(a) A teacher administers a 20-question multiple-choice quiz (four choices per question). A student guesses randomly on all questions. Let $X =$ number of correct answers.

(b) A researcher surveys 100 customers about their satisfaction (on a 5-point scale from "very dissatisfied" to "very satisfied"). Let $X =$ number of satisfied or very satisfied customers.

(c) A quality engineer draws bolts from a production line one at a time, inspecting each, until she finds a defective one. Let $X =$ the number of bolts she inspects.

### Application

**Exercise 4.4** *(LO: calculate binomial probabilities).* A clinic offers flu vaccines. The vaccine is 85% effective. A medical team vaccinated 8 health-care workers. What is the probability that at least 7 of them are protected from the flu?

**Exercise 4.5** *(LO: apply Poisson distribution).* A help desk receives customer calls at an average rate of 3 per hour. 

(a) What is the probability of receiving exactly 2 calls in the next hour?
(b) What is the probability of receiving 5 or more calls in the next hour?

**Exercise 4.6** *(LO: interpret variance and standard deviation).* A quality-control engineer samples 100 light bulbs and records the number with a usable lifespan of at least 1000 hours. The sample mean is 85 with standard deviation 6.

(a) Interpret the standard deviation in context.
(b) Approximately what range of values would you expect to see if you repeated this sampling procedure?

### Synthesis

**Exercise 4.7** *(LO: choose an appropriate distribution).* A pharmaceutical company is running a Phase II trial of a new cancer drug. They enroll 50 patients with late-stage disease. Historical data shows the standard therapy has a 30% response rate (tumor shrinks by at least 25%). 

(a) If the new drug is equally effective, what is the expected number of responders out of 50?
(b) What is the standard deviation?
(c) The new drug shows 22 responders out of 50. Is this evidence that the new drug is better than standard therapy? (Hint: compute $P(X \geq 22)$ under the null hypothesis that the drug is no better than the standard. If this probability is small, say less than 5%, the result is statistically significant.)

**Exercise 4.8** *(LO: apply multiple concepts).* A call center operates 24 hours a day. Call volume follows a Poisson distribution with a rate of 15 calls per hour during day shifts (8 a.m.–6 p.m., 10 hours) and 6 calls per hour during night shifts (6 p.m.–8 a.m., 14 hours). 

(a) What is the expected number of calls during a day shift? During a night shift? Over a full 24-hour period?
(b) What is the standard deviation for each period?
(c) The center wants to staff enough operators to handle 95% of typical call volumes. For the day shift, approximately how many calls should the center expect with 95% confidence?

### Challenge

**Exercise 4.9** *(LO: open-ended, synthesize and extend).* A vaccine is 95% effective. A clinic vaccinated 200 patients. 

(a) Calculate the expected number of protected patients and the standard deviation.
(b) Using the 68-95-99.7 rule (covered in Chapter 6), approximately what range of protection would you expect to see?
(c) Suppose the clinic observed 180 protected patients. Is this consistent with the expected distribution? Justify your answer.

**Exercise 4.10** *(LO: reason with distributions under uncertainty).* A manufacturer's claim is that only 2% of items have manufacturing defects. A consumer group inspects 500 items and finds 14 defects.

(a) Under the manufacturer's claim, what is the expected number of defects in 500 items? The standard deviation?
(b) How many standard deviations away from the mean is 14 defects?
(c) Does the consumer group's finding challenge the manufacturer's claim? Why or why not?

---

## Chapter summary

You can now do five things you probably could not do an hour ago.

You can **define a random variable and construct its probability mass function.** You understand that a random variable is a rule assigning numbers to outcomes, that a valid PMF requires probabilities between 0 and 1 summing to 1, and that the PMF encodes all the information about the distribution.

You can **calculate expected value and variance**, understanding that expected value is the long-run average (not necessarily a value the variable actually takes), and that variance and standard deviation measure the spread around that average.

You can **recognize a binomial situation** and **apply the binomial formula.** You understand that binomial requires a fixed number of independent trials, two outcomes per trial, and a constant probability of success. You can compute probabilities, expected value, and standard deviation.

You can **apply the Poisson distribution** to count rare events in fixed intervals. You understand that the Poisson has one parameter ($\mu$) and that mean and variance are equal. You can recognize when the Poisson approximates the binomial.

You can **choose the right distribution** for a practical problem. You understand the boundary between binomial (fixed $n$) and Poisson (fixed interval, variable count). You can calculate probabilities and parameters, then use them to inform decisions in quality control, clinical trials, operations planning, and public health.

The thread forward is this: distributions emerge from structure. If you recognize the structure (independent trials with fixed $p$, rare events at constant rate), you can predict what the data will look like before you collect it. Chapter 5 extends this idea to continuous random variables, where outcomes can land on any value in an interval. Chapter 6 introduces the normal distribution, which is both continuous and fundamental to all of statistical inference.

---

## Connections forward

In Chapters 1–3, you learned probability—the mathematics of what should happen if a process is fair and random. This chapter translates that language into distributions you can actually use: binomial for experiments with trials, Poisson for arrivals and counts. Both are discrete — they live on whole numbers.

In Chapter 5, you'll meet continuous random variables and distributions that live on intervals. The normal distribution (Chapter 6) is the most important of these. The mean and variance you've learned to calculate here will reappear in every chapter that follows. Confidence intervals (Chapter 8) use expected value and standard deviation. Hypothesis testing (Chapters 9–11) relies on understanding how far a real observation can be from what a distribution predicts. Regression (Chapter 13) fits a normal distribution to the residuals—the leftover variation after accounting for the relationship between two variables.

For now, the skill is this: when you encounter count data (successes, arrivals, defects, infections), pause and ask: Do I know the number of trials? Is the rate constant? Are the outcomes independent? Answer those questions and you know which distribution to reach for.

---

## What would change my mind

If a dataset of counts showed variance much larger than the mean (when the Poisson predicts they should be equal), I would conclude that the Poisson is the wrong model and would look for a process that introduces clustering or non-independence (e.g., contagion, burnout effects, batch phenomena).

---

## Still puzzling

I don't yet have a deep intuition for why the Poisson formula is $\frac{\mu^k e^{-\mu}}{k!}$. I can compute with it and derive its properties, but the formula itself feels like it came from thin air. Some day I'll work through the derivation from the binomial limit and understand where each piece comes from.

---

## Tags

discrete-random-variables, probability-mass-function, expected-value, binomial-distribution, poisson-distribution, quality-control, clinical-trials, applied-statistics

---

## LLM Exercise — Chapter 4: Discrete Random Variables (Analyze One Dataset Project)

**Project:** Analyze One Real Dataset.
**What you're building this chapter:** discrete-distribution analysis of a count variable in your dataset.
**Tool:** **Claude Code** for fitting; **Claude Project** for the section.

---

**The Prompt:**

```
Chapter 4 of my Analyze-One-Dataset project. Chapter 4 covered:
discrete random variables; pmf; expected value E(X) = Σ x·P(X=x);
variance Var(X) = E[(X−μ)²]; SD = √Var; binomial (n fixed trials,
probability p of "success"); geometric (number of trials to first
success); hypergeometric (sampling without replacement);
Poisson (rare-event count over a fixed interval; mean = variance =
λ).

Write the brief's "Discrete Variable Analysis" section in 400-700
words.

1. **Pick a discrete variable.** From your variable inventory,
   identify one quantitative variable that's discrete (integer
   counts of something — number of goals scored, number of
   children, count of patients, defects per batch, etc.).

2. **Build the empirical pmf.** From your data, compute the
   relative frequency P(X = x) for each observed value of X.
   Plot it as a bar chart.

3. **Compute E(X) and SD(X) from the data.**
   - E(X) = Σ x · P(X=x) — should match the sample mean from
     Chapter 2.
   - Var(X) = Σ (x − E(X))² · P(X=x) — should match the sample
     variance.

4. **Try fitting a named distribution.** Two plausible candidates:
   - **Binomial(n, p)**: if your variable is the count of
     successes in n fixed trials. Estimate p̂ = sample mean / n.
     Compute the binomial pmf P(X=k) = C(n,k) p^k (1-p)^(n-k) for
     each k and compare to the empirical pmf.
   - **Poisson(λ)**: if your variable is count of rare events.
     Estimate λ̂ = sample mean. Compute Poisson pmf P(X=k) =
     e^(-λ) λ^k / k!. Compare to empirical.

   Which fits better? (Often: rare events with no fixed n → Poisson;
   number of successes in n trials → binomial.) Justify.

5. **The check.** For your fitted distribution, does the
   distribution's mean match the sample mean? Does its variance
   match the sample variance? For Poisson specifically, mean
   should equal variance — is that true in your data, or is your
   variable over-dispersed (variance > mean)?

End with a "How well does the named distribution describe my
data" verdict. Honest answer: real data is messier than textbook
distributions. The textbook distribution is a model — useful but
imperfect.
```

---

**What this produces:** A 400-700 word section with empirical pmf + fitted theoretical distribution + a fit-quality assessment. The "honest fit" verdict is the discipline this chapter trains.

**How to adapt this prompt:**

- *For your own project:* If your dataset has no obvious discrete variable, find one — counts often hide in continuous-looking columns (number of customers per day, etc.).
- *For ChatGPT / Gemini:* Works as written.
- *For Claude Code:* `scipy.stats.binom`, `scipy.stats.poisson` for theoretical pmfs.
- *For a Claude Project:* Append.

**Connection to previous chapters:** Ch 2's mean and SD computations get reinterpreted as E(X) and SD(X) here.

**Preview of next chapter:** Chapter 5 covers continuous random variables. You'll identify a continuous variable and try fitting uniform or exponential.


---

## 🕰️ AI Wayback Machine

**Siméon Denis Poisson** was French mathematician whose 1837 work on the distribution bearing his name underlies modern modeling of rare events.

**Run this:**

```
Who is Siméon Denis Poisson, and how does their work connect to discrete random variables we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Siméon Denis Poisson"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Siméon Denis Poisson's framework to a small dataset you actually have.
- Add a constraint: "Answer including criticisms or limits of Siméon Denis Poisson's framework."

What changes? What gets better? What gets worse?
