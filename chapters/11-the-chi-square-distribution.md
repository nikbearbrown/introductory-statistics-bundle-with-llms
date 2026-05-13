# Chapter 11 — The Chi-Square Distribution

## Three title options

1. **Counting Categories: When Data Don't Come in Bell Curves**
2. **Do Patterns Match Reality? The Chi-Square Test for Counts**
3. **Measuring Fit: From Mendel's Peas to A/B Test Results**

---

## TL;DR

The chi-square distribution measures how far observed data stray from what theory predicts. Unlike z or t tests (which work with measurements), chi-square tests work with counts in categories. Three applications: goodness-of-fit (do my data fit this distribution?), independence (are these two factors really unrelated?), and single-variance tests. All three ask the same core question: observed minus expected, squared and summed—how large does that sum have to be before we stop believing the null?

---

## Cold open: Mendel's pea colors

Gregor Mendel, in his Brno monastery garden in the 1860s, was cross-breeding pea plants and tracking the colors of the offspring. His theory said that when you cross heterozygous yellow with heterozygous yellow plants, the offspring should appear in a 3:1 ratio—three yellow for every one green. Theory said ratio 3:1. The math said that in 1,000 offspring you'd expect roughly 750 yellow and 250 green.

He planted. He counted. He got 882 yellow and 118 green out of 1,000. That's not 3:1. Does that mean his theory was wrong?

Or is 882 yellow close *enough* to 750, given the noise of real plants and real gardens?

You need a way to ask: *How far from expectation can the data be before I stop believing the theory?* That tool is the chi-square test.

### Learning objectives

By the end of this chapter you will be able to:

- **Calculate** the chi-square test statistic from a table of observed and expected counts.
- **Determine degrees of freedom** for goodness-of-fit, independence, and variance tests.
- **Conduct a goodness-of-fit test** to ask whether data fit a proposed distribution.
- **Conduct a test of independence** to ask whether two categorical variables are truly unrelated.
- **Understand the mechanics** of why chi-square is always right-tailed and always nonnegative.
- **Recognize when chi-square breaks down** (expected counts too small, confusing correlation with causation).

### Prerequisites

Comfort with hypothesis testing (null, alternative, test statistic, p-value). Knowledge of contingency tables (two-way tables with row and column totals). The normal distribution, just for context. You've seen the t-distribution and z-distribution; this is the third major distribution you'll work with.

### Why this chapter matters

Until now, every test you've used assumed you were measuring something: heights, test scores, salaries. Those measurements form distributions. The t-test asked whether two means differ. The z-test asked whether a proportion differs from expectation.

But many real questions don't fit that mold. Does lottery-ticket frequency match a uniform distribution? Does movie preference differ by age group? Does the variance of a manufacturing process stay within tolerance? None of these start with measurements. They start with counts: how many people in this category, how many in that one.

Chi-square is the test for counts.

---

## Concept 1 — The chi-square distribution: Where it comes from

A distribution is always the sum of something. The normal distribution—bell curve—is what you get when you add up many small, independent, random contributions. The t-distribution is the ratio of a sample mean to its estimated standard error. The chi-square distribution is the sum of *squared, standardized* deviations.

Here's the formal statement. If you have $k$ independent standard normal random variables—each following $N(0,1)$, each squared—and you add them up, the sum follows a chi-square distribution with $k$ degrees of freedom.

$$\chi^2 = Z_1^2 + Z_2^2 + \cdots + Z_k^2$$

where each $Z_i \sim N(0,1)$ independently.

You don't need to generate $k$ normal variables to use chi-square. The formula is machinery. The point is this: chi-square measures accumulated squared deviations. When observed data fall far from expected, those deviations get large, their squares get larger, and the sum grows.

### The shape of chi-square

The chi-square curve looks nothing like a bell. It's **skewed to the right**—it starts near zero, rises to a peak, then has a long tail reaching toward infinity. The shape depends on the degrees of freedom.

- When $df = 1$, the curve is most skewed, bunched near zero.
- When $df = 2$, it looks almost exponential.
- As $df$ increases, the curve becomes more symmetric and spreads out.
- When $df > 90$, it approximates the normal distribution. At $df = 1000$, you can barely tell the difference from a bell curve.

**Key property:** The chi-square distribution is always nonnegative. The test statistic can never be negative because it's a sum of squared terms. This means chi-square tests are *always right-tailed*. You reject the null when the test statistic is unusually *large*, not unusually small.

### Degrees of freedom in chi-square

The degrees of freedom in chi-square tell you how many constraints the data face. Suppose you're sorting 100 people into three categories: Red, Blue, Green. You have 100 - 1 = 99 pieces of information. But once you know how many are Red and how many are Blue, the Green count is determined (100 minus the other two). So you have only 2 degrees of freedom.

More generally: if you have $k$ categories, $df = k - 1$.

For two-way tables (contingency tables), the formula is different: $df = (\text{rows} - 1) \times (\text{columns} - 1)$. You lose one degree of freedom for each row total and each column total that's fixed.

### The mean and standard deviation of chi-square

A chi-square distribution with $k$ degrees of freedom has population mean $\mu = k$ and standard deviation $\sigma = \sqrt{2k}$.

This gives you intuition. If you're testing whether data fit a distribution and you have 20 categories, the mean of the chi-square distribution is 20. If you calculate a test statistic of 22, you're only slightly above the mean—probably not evidence against the null. If you calculate 50, you're well into the tail.

### Etymology and notation

The name *chi-square* comes from the Greek letter $\chi$ (chi, pronounced "kye"), which looks vaguely like a squared variable. The notation is $X^2 \sim \chi_{df}^2$, read "X squared follows chi-square with $df$ degrees of freedom." The square in the name and notation refers both to the fact that you're squaring deviations and to the shape of the curve.

### Worked example — Recognizing when chi-square applies

A lottery claims its drawing machine is fair: each of six numbers should come up equally often. You run the machine 6,000 times. You expect each number to appear 1,000 times. You observe: 980, 1,010, 1,020, 995, 990, 1,005. Are these results consistent with a fair machine?

**What distribution do you need?** Chi-square. You have counts (observed) and expected counts. You want to know whether the observed counts deviate too far from expected.

**How many degrees of freedom?** Six categories (the six numbers), so $df = 6 - 1 = 5$.

**What would you calculate?** The chi-square test statistic using the formula in Concept 2.

### Common misconceptions

**"Chi-square is the same as t-test, just for categories."** Not quite. The t-test assumes the underlying population is normal and tests means. Chi-square tests counts against expectation. They're answering different questions.

**"If my chi-square statistic is close to the degrees of freedom, the null is true."** No. A statistic close to $df$ is not strong evidence either way—it's in the middle of the distribution. You need a p-value to decide.

**"Chi-square is always right-tailed."** Yes, because of the squared deviations. But you should still check the p-value. Some software lets you set left-tailed options; those are always wrong for chi-square.

---

## Concept 2 — The goodness-of-fit test

A goodness-of-fit test asks: *Do my data fit this proposed distribution?* You have a theory about what should happen. You have actual data about what did happen. The test measures whether the difference is noise or genuine disagreement.

### The recipe

The test statistic is:

$$\chi^2 = \sum \frac{(O - E)^2}{E}$$

where $O$ is the observed count in each category, $E$ is the expected count, and you sum over all categories.

The formula is intuitive. $(O - E)$ is the deviation from expectation. You square it so big deviations get penalized hard. You divide by $E$ to standardize—a deviation of 10 from an expected count of 100 is noise, but a deviation of 10 from an expected count of 5 is glaring. Sum across all categories and you have a single number measuring total misfit.

### The hypotheses

The null hypothesis is always: *The data fit the proposed distribution* (or in words, the frequencies match expectation, or the categorical distribution matches the theory).

The alternative is: *The data do not fit the proposed distribution.*

Write these in words unless the problem specifically asks for equations.

### The procedure, step by step

1. **Set the significance level** ($\alpha$).
2. **State the hypotheses** in words.
3. **Verify assumptions**: Each expected count must be at least 5. If some are below 5, combine categories until they're all at least 5. This is not optional—the test breaks down otherwise.
4. **Calculate expected counts** from the proposed distribution.
5. **Build a calculation table** with columns: category, $O$, $E$, $(O - E)$, $(O - E)^2$, $\frac{(O - E)^2}{E}$.
6. **Sum the last column** to get the test statistic.
7. **Find degrees of freedom**: $df = (\text{number of categories}) - 1$.
8. **Look up the critical value** in the chi-square table or use software to find the p-value.
9. **Make a decision** and write a conclusion.

### Worked example — Are the days equally absent?

Managers want to know whether employees call in sick equally throughout the week, or whether certain days are more popular for absence. They survey 60 managers: which day of the week saw the most absences at their workplace?

Results: Monday 15, Tuesday 12, Wednesday 9, Thursday 9, Friday 15. (Total: 60.)

**Hypotheses:**
- $H_0$: Absences are equally distributed across the five weekdays.
- $H_a$: Absences are not equally distributed.

**Expected counts:** If absences are uniform, we'd expect $60 / 5 = 12$ on each day.

**Calculation table:**

| Day | $O$ | $E$ | $O - E$ | $(O - E)^2$ | $\frac{(O - E)^2}{E}$ |
|---|---|---|---|---|---|
| Monday | 15 | 12 | 3 | 9 | 0.75 |
| Tuesday | 12 | 12 | 0 | 0 | 0.00 |
| Wednesday | 9 | 12 | −3 | 9 | 0.75 |
| Thursday | 9 | 12 | −3 | 9 | 0.75 |
| Friday | 15 | 12 | 3 | 9 | 0.75 |
| | | | | | **3.00** |

$\chi^2 = 3.00$, $df = 5 - 1 = 4$.

**Critical value** at $\alpha = 0.05$ with $df = 4$: 9.488.

**Decision:** $3.00 < 9.488$, so we do not reject $H_0$.

**Conclusion:** At the 5% significance level, there is insufficient evidence to conclude that absences are unequally distributed across days. The observed pattern is consistent with a uniform distribution. Monday and Friday happened to see more absences by chance.

### A scale shift: From one test to many

A single goodness-of-fit test compares one sample to one theoretical distribution. But the same statistic, summed across many studies, tells a bigger story.

Imagine ten researchers each conduct a drug trial. Each tests whether the drug is better than placebo using a chi-square goodness-of-fit for adverse events: observed frequencies match the known rate (the distribution from prior trials).

Researcher 1 gets $\chi^2 = 4.1$, p-value 0.25. Not significant.
Researcher 2 gets $\chi^2 = 3.8$, p-value 0.28. Not significant.
... and so on.

But when you aggregate those results—when you ask, "Across all ten studies, is the pattern of adverse events consistent?"—the individual chi-squares combine, the degrees of freedom add, and the aggregate tells you whether a subtle effect is real across many replications.

### Common misconceptions

**"If expected count is below 5, I can still run the test."** No. The test relies on the normal approximation to the multinomial distribution, which breaks down when counts are small. Combine categories, don't ignore it.

**"High chi-square always means the null is false."** High chi-square means observed deviates from expected. But if your expected distribution was wrong to begin with, high chi-square just means the world didn't cooperate. Always sanity-check your hypothesis.

**"I can use goodness-of-fit to test any distribution."** You can, but it only tests the distribution you specified. You need the right expected distribution. If you're testing normality, use normal expected values, not uniform. Get the theory right.

---

## Concept 3 — The test of independence

Independence in statistics means: knowing the value of one variable tells you nothing about the other. A test of independence asks whether two categorical factors are truly unrelated or whether they're associated.

### The setup

You have data in a contingency table (two-way table). Rows represent one categorical variable (e.g., age group), columns represent another (e.g., favorite movie genre). Each cell contains a count.

The null hypothesis is: *The two factors are independent.* If they're independent, you can calculate expected frequencies using the law of probability: $P(A \text{ and } B) = P(A) \times P(B)$.

### The expected frequencies

If factors are independent, the expected count in cell $(i, j)$ is:

$$E_{ij} = \frac{(\text{row total}_i) \times (\text{column total}_j)}{\text{grand total}}$$

This formula says: the proportion of the grand total that goes in this cell equals the row proportion times the column proportion.

### The test statistic and degrees of freedom

The test statistic is the same formula as goodness-of-fit:

$$\chi^2 = \sum \sum \frac{(O_{ij} - E_{ij})^2}{E_{ij}}$$

You sum over all rows and columns.

The degrees of freedom: $df = (\text{rows} - 1) \times (\text{columns} - 1)$.

For a 2×3 table (two rows, three columns): $df = (2 - 1) \times (3 - 1) = 2$.

### A worked example — Movie preference by age

A survey of 400 moviegoers asked their age group and favorite genre. Is preference independent of age, or do older and younger viewers like different things?

**Observed data:**

| Age | Action | Comedy | Drama | **Row total** |
|---|---|---|---|---|
| 18–30 | 40 | 50 | 35 | **125** |
| 31–50 | 45 | 60 | 70 | **175** |
| 50+ | 30 | 40 | 30 | **100** |
| **Col total** | **115** | **150** | **135** | **400** |

**Hypotheses:**
- $H_0$: Movie preference is independent of age group.
- $H_a$: Movie preference and age group are dependent.

**Expected counts:** Using the formula.

For Age 18–30, Action: $E = \frac{125 \times 115}{400} = 35.94$
For Age 18–30, Comedy: $E = \frac{125 \times 150}{400} = 46.88$
For Age 18–30, Drama: $E = \frac{125 \times 135}{400} = 42.19$

And so on for each cell. (I'll spare you the full table.)

Once you have all expected counts, calculate $\chi^2$ the same way: sum $(O - E)^2 / E$ across all six cells.

Suppose you get $\chi^2 = 8.7$.

$df = (3 - 1) \times (3 - 1) = 4$.

Critical value at $\alpha = 0.05$: 9.488.

**Decision:** $8.7 < 9.488$, so we do not reject $H_0$.

**Conclusion:** There is insufficient evidence that movie preference depends on age group. The data are consistent with independence.

### A critical scale shift: One table to many studies

A single test of independence answers one question: Are these two factors related in this dataset?

But as replication advances statistics, researchers ask: Across many studies in different countries, with different samples, is the relationship consistent?

When you aggregate chi-squares across independent studies, the individual test statistics add, degrees of freedom add, and the combined result tells you whether the association is robust. One study might find $\chi^2 = 6$ (not significant at $\alpha = 0.05$). Another finds $\chi^2 = 7$. Together, $\chi^2 = 13$ with $df = 2 + 2 = 4$, which *is* significant. Replication strengthens what individual noise obscures.

### The major pitfall: Correlation is not causation

A test of independence tells you whether two variables are *associated*—whether knowing one helps predict the other. It does **not** tell you why they're associated.

If you find that age and movie preference are dependent, that could mean: (1) age actually affects taste, or (2) generation cohorts grew up with different movies and that shaped permanent preference, or (3) health or economics (older people spend less on movies, skewing toward home viewing), or (4) selection bias (respondents of different ages showed up at different times).

The test finds association. It does not prove causation. You must think about the mechanism.

### Common misconceptions

**"Independence means the counts are equal."** No. Independence means the *ratio* of counts in one row matches the ratio in every other row. A 3×3 contingency table can be independent with counts like 10, 20, 30 in one row and 15, 30, 45 in another. They have different marginals, but the same structure.

**"If p-value is large, the variables are independent."** Large p-value means insufficient evidence against independence. That's not the same as proving independence. Maybe your sample is too small.

**"Expected count below 5 is okay if I have a lot of cells."** No. Each cell's expected count must be at least 5. If too many cells fail, combine categories or get more data.

---

## Integration: From categorical tests to inference

Return to the lottery from the cold open. You want to know: Is the machine fair?

Theory says each of six numbers appears equally often—a uniform distribution over the six outcomes.

You run 6,000 trials and observe: 980, 1,010, 1,020, 995, 990, 1,005.

Expected for each: 1,000.

Chi-square test:

$$\chi^2 = \frac{(980-1000)^2}{1000} + \frac{(1010-1000)^2}{1000} + \cdots + \frac{(1005-1000)^2}{1000} = \frac{400 + 100 + 400 + 25 + 100 + 25}{1000} = 1.05$$

$df = 6 - 1 = 5$. Critical value at $\alpha = 0.05$ is 11.07.

$1.05 < 11.07$, so we do not reject the null. The observed counts are consistent with a fair machine. The deviations you see are what you'd expect from random variation.

Now imagine you run a different test: You categorize lottery players by gender and check whether male and female players have the same pattern of number preferences (numbers 1–3 versus 4–6). You get a 2×2 contingency table. Does preference depend on gender?

Chi-square test of independence answers that. Same machinery, different question.

Both tests ask: *How far from expectation can the data be before I stop believing the theory?* The answer is always measured in chi-squares.

---

## Exercises

### Warm-up

**Exercise 11.1** *(LO: degrees of freedom).* A goodness-of-fit test has eight categories. (a) How many degrees of freedom? (b) If the test statistic is $\chi^2 = 14.2$, is it significant at $\alpha = 0.05$?

**Exercise 11.2** *(LO: recognize distribution).* For each scenario, state whether you'd use chi-square goodness-of-fit, chi-square independence, or a different test.

(a) A poll asks 1,000 people whether they support a ballot measure. You want to test whether support differs from 50%.
(b) A survey of 200 college students asks major and whether they have a job. Are major and employment status related?
(c) A die is rolled 120 times. Do the frequencies match a fair die?

**Exercise 11.3** *(LO: expected frequencies).* A survey of 300 people asks about breakfast frequency: daily, weekly, rarely, never. Under the null that all frequencies are equal, what is the expected count for each category? Is it at least 5?

### Application

**Exercise 11.4** *(LO: goodness-of-fit).* A company produces cereal boxes with target weight 400g. A sample of 100 boxes is weighed, and the weights are sorted into four categories: below 395g, 395–399g, 400–404g, 405g and above. The observed frequencies are 18, 24, 40, 18. Suppose you expect (under normality) frequencies of 12, 38, 38, 12. Conduct a chi-square goodness-of-fit test at $\alpha = 0.05$.

**Exercise 11.5** *(LO: test of independence).* A survey of 400 employees classifies them as full-time or part-time (rows) and union or non-union (columns). The contingency table:

|  | Union | Non-union |
|---|---|---|
| Full-time | 60 | 140 |
| Part-time | 40 | 160 |

Are employment status and union membership independent at $\alpha = 0.05$?

**Exercise 11.6** *(LO: expected frequencies in independence).* In Exercise 11.5, calculate the expected frequency for the "full-time, union" cell. Does it meet the minimum of 5?

### Synthesis

**Exercise 11.7** *(LO: goodness-of-fit + interpreting results).* A study of absent days at a hospital follows a Poisson distribution with mean 2. A sample of 100 departments is observed, and the frequency of departments with 0, 1, 2, 3, 4+ absent days is 20, 35, 27, 12, 6. Conduct a goodness-of-fit test. If you reject, what does that tell you about the distribution of absent days?

**Exercise 11.8** *(LO: independence + recognizing causation limits).* A test of independence finds that smoking status and cancer diagnosis are dependent in a dataset of 10,000 people. The p-value is less than 0.001. Does this prove smoking causes cancer? Explain what the test actually tells you and what additional evidence you'd need.

### Challenge

**Exercise 11.9** *(LO: degrees of freedom in a complex table).* A study observes 500 people across three age groups (rows) and four income brackets (columns). How many degrees of freedom for a test of independence? If the chi-square statistic is 21.5, is it significant at $\alpha = 0.05$?

**Exercise 11.10** *(LO: integrating chi-square with prior chapters).* In Chapter 9, you tested whether a single proportion differed from 0.5 using a z-test. Here, you could also use a goodness-of-fit test with two categories (success, failure) and expected counts of 0.5 × $n$ each. Why might chi-square and z give different answers, and when would they agree?

---

## Chapter summary

You can now do four things you could not do an hour ago.

You understand what the chi-square distribution is: a sum of squared, standardized deviations from a known distribution. Its shape depends on degrees of freedom. It is always right-tailed and always nonnegative.

You can conduct a **goodness-of-fit test** to ask whether observed data match a proposed distribution. Build a table, calculate chi-square, compare to critical value, draw a conclusion. The key check: expected counts must all be at least 5.

You can conduct a **test of independence** to ask whether two categorical factors are associated or independent. Use the formula for expected frequencies, build chi-square from the contingency table, and decide whether to reject independence. Same machinery as goodness-of-fit, different question.

You understand the **scale shift** from one test to many: when replication studies accumulate chi-squares across independent samples, the combined result is itself chi-square. This is how we discover robust patterns in noisy data.

Most importantly: you know that chi-square tests for *association*, not causation. A significant test tells you the variables are not independent. It does not tell you why, or which way the causal arrow points.

What you should teach a friend: How to recognize when counts, not measurements, are the data you have. How to set up expected frequencies. Why the test is always right-tailed. And why correlation between two variables does not mean one causes the other.

---

## Connections forward

In Chapter 12 (F-Distribution and ANOVA), you will meet another distribution that tests whether several means differ—the next generalization of the two-sample t-test. Chi-square was categorical; ANOVA is continuous. Both compare observed to expected and ask whether the difference is noise or signal.

In Chapter 13 (Linear Regression and Correlation), you will learn to measure association between two continuous variables. Chi-square tests association in contingency tables. Regression quantifies the strength and direction of a linear relationship. Both touch the same idea—whether one variable helps predict another—but through different machinery.

Finally, if you take a course in Bayesian inference, you will see chi-square again as a tool for model criticism. You will propose a model (the null), generate expected data from it, compare to your actual data, and use chi-square to ask: "How consistent are the data with this model?" The logic is identical. The language is different, but the machinery is the same.

---

## What would change my mind

If I observed chi-square test results where very small or very large expected counts (below 1, above 100,000) were paired with reasonable conclusions, I would reconsider the minimum expected-count rule. I would also reconsider if I saw a case where violating the assumption produced notably different conclusions from a nonparametric alternative.

## Still puzzling

I remain uncertain about the practical boundary between "expected counts are low enough to worry" and "expected counts are so low the test is meaningless." Different statisticians cite different minima (3, 5, 10). The literature on this is scattered. I apply the "expected ≥ 5" rule because it's conventional and conservative, but the exact threshold would benefit from a careful simulation study.

---

**Tags:** chi-square, goodness-of-fit, test of independence, contingency tables, categorical data, degrees of freedom, hypothesis testing, Mendel, observed vs. expected, right-tailed test
---

## LLM Exercise — Chapter 11: The Chi-Square Distribution (Analyze One Dataset Project)

**Project:** Analyze One Real Dataset.
**What you're building this chapter:** chi-square tests for categorical relationships in your data.
**Tool:** **Claude Code** + **Claude Project**.

---

**The Prompt:**

```
Chapter 11 of my Analyze-One-Dataset project. Chapter 11 covered:
the chi-square distribution; three named chi-square tests:
1. Goodness-of-fit: does a single categorical variable's
   distribution match a theoretical or claimed distribution?
2. Independence: are two categorical variables independent (in
   a single sample)?
3. Homogeneity: are the distributions of one categorical variable
   the same across multiple groups?
The test statistic χ² = Σ (Observed − Expected)² / Expected; the
degrees of freedom depend on the test type; rejection when
χ² > critical value (or equivalently p < α).

Write the brief's "Chi-Square Analysis" section in 500-700 words.

1. **Pick TWO categorical variables** (from Ch 3's work; ideally
   the same pair you analyzed there). Build a contingency table.

2. **Compute expected counts** under H₀ (independence):
   Expected[i,j] = (Row_i_total × Column_j_total) / Grand_total.

3. **Check expected-count rule.** Chi-square assumes expected
   counts ≥ 5 for the approximation to work. If some cells have
   expected < 5, consider Fisher's exact test instead.

4. **Run the chi-square test of independence.**
   - State H₀: variables are independent.
   - Compute χ² = Σ (O − E)² / E across all cells.
   - Degrees of freedom = (rows − 1)(columns − 1).
   - Use scipy.stats.chi2_contingency(table) to get χ², p-value,
     df.

5. **Interpret.**
   - If p < α: reject independence; the two variables are
     associated.
   - If p ≥ α: insufficient evidence to reject independence;
     they may be related or may not — we can't conclude
     independence.

6. **Effect size: Cramér's V.** A small p-value tells you the
   variables are related; Cramér's V tells you how strongly.
   - V = √(χ² / (n × (min(r,c) − 1))).
   - V = 0 means no association; V = 1 means perfect association.
   - Rules of thumb: V < 0.1 is weak; 0.1-0.3 is moderate;
     > 0.3 is strong.

7. **Goodness-of-fit (optional).** If you have a "claimed
   distribution" for a single variable (e.g., "the proportion of
   X should be 25%"), test it against the observed.

End with: how do Ch 3's conditional probabilities (which suggested
dependence visually) align with Ch 11's formal test (which
quantifies it)? Did the chi-square reject what your eyes
suspected?
```

---

**What this produces:** A 500-700 word section with chi-square test + Cramér's V + interpretation.

**How to adapt this prompt:**

- *For your own project:* If your dataset has only two categorical variables, chi-square is fully exercised on them. If multiple, pick the pair most relevant to your big question.
- *For ChatGPT / Gemini:* Works as written.
- *For Claude Code:* `scipy.stats.chi2_contingency` is the one-liner.
- *For a Claude Project:* Append.

**Connection to previous chapters:** Ch 3 (conditional probabilities) → Ch 11 (formal test of independence) close the loop.

**Preview of next chapter:** Chapter 12 covers ANOVA — comparing 3+ group means. You'll pick a categorical variable with multiple levels and run ANOVA on a quantitative outcome.


---

## 🕰️ AI Wayback Machine

**Karl Pearson** was introduced the chi-square test in 1900 — and built the foundations of biometric statistics, with a controversial eugenics legacy.

**Run this:**

```
Who is Karl Pearson, and how does their work connect to the chi-square distribution we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Karl Pearson"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Karl Pearson's framework to a small dataset you actually have.
- Add a constraint: "Answer including criticisms or limits of Karl Pearson's framework."

What changes? What gets better? What gets worse?
