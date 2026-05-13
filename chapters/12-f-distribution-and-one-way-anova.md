# The F-Distribution and One-Way ANOVA

## TL;DR

When you want to compare means across three or more groups, you could run multiple t-tests, but each test carries a risk of a false positive. ANOVA — *AN*alysis *O*f *VA*riance — solves this by partitioning variation into what's explained by group differences versus what's leftover noise, then builds a single F-test that controls the family-wise error rate and reveals whether at least one group mean differs from the others.

---

## Cold Open: The Agricultural Experiment

It's the 1920s at Rothamsted Experimental Station in Hertfordshire, England. Ronald Fisher, the head statistician, is standing in a wheat field with a research team. They've planted five plots of wheat under identical conditions, except for the fertilizer. Each plot will receive a different nitrogen application. At harvest, they'll measure yield. The question is plain: does fertilizer choice matter?

This seems simple—measure five means, compare them. But Fisher knows something the team will discover when they calculate. If you run four separate t-tests comparing pairs of fertilizers (plot 1 vs 2, 1 vs 3, 1 vs 4, etc.), each test controls the false positive rate (Type I error) at, say, 5%. But run four tests, and the chance that *at least one* gives a false positive climbs to roughly 18%. Run ten comparisons, and you're past 40%. The more tests you run, the more likely you'll find a spurious difference just by noise.

Fisher's insight: don't test pairs. Test all the groups at once by comparing how much of the total variation is *between* the groups versus how much is *within* groups. If the groups are truly identical, most variation should be within groups—just random fluctuation. But if the fertilizers really differ, the between-groups variation will be large. You build a single test statistic from that comparison. That statistic follows what we now call the *F* distribution. The result: one test, one family-wise error rate controlled, one decision.

---

## Concept 1: The F-Distribution and Why It Shows Up

### The Shape and Its Origin

The *F* distribution is named for Ronald Fisher, who developed it. (George Snedecor later popularized it and honored Fisher by the name.) It's the distribution of the ratio of two independent variance estimates, each drawn from a normally distributed population.

This ratio is always non-negative—you can't have a negative variance. The curve skews right: it has a long tail toward the right and a hard left boundary at zero. The shape changes depending on two degrees of freedom: one for the numerator (the variance in the top of the fraction) and one for the denominator (the variance in the bottom). As both degrees of freedom grow, the F curve becomes more symmetric and approaches a normal distribution, though it never quite loses its right skew.

If you find yourself wondering *why* a ratio of two independent variance estimates has this particular distribution, you're asking the right question. The answer lives in mathematical statistics and relies on properties of the chi-squared distribution (which you met in the last chapter). For our purposes, the machinery is: when you have two samples from normal populations with equal variances, the ratio of their sample variances follows an F distribution with degrees of freedom $(n_1 - 1, n_2 - 1)$. When populations have equal means *and* equal variances, the F ratio should hover near 1, with most values between 0.5 and 2. When the numerator population has a larger variance, the F ratio climbs.

### A Simple Example: Testing Consistency in Grading

Imagine two professors at your college each grade the same 10 student exams. One instructor's grades have a variance of $s_1^2 = 52.3$. The other's have $s_2^2 = 89.9$. The college wants to know: is one grader more inconsistent than the other? (Consistent grading—low variance—is valued.)

We ask: do these two samples come from populations with equal variance?

$$H_0: \sigma_1^2 = \sigma_2^2$$
$$H_a: \sigma_1^2 \neq \sigma_2^2$$

The test statistic is the ratio of the sample variances. By convention, put the larger sample variance in the numerator:

$$F_c = \frac{s_{\text{larger}}^2}{s_{\text{smaller}}^2} = \frac{89.9}{52.3} = 1.719$$

The degrees of freedom are $n_1 - 1 = 9$ for the numerator and $n_2 - 1 = 9$ for the denominator. We write: $F \sim F_{9,9}$.

At the 1% significance level, the critical value (looking at an F-table or software) is $F_{0.01, 9, 9} = 5.35$. Our test statistic is $F_c = 1.719$. Since $1.719 < 5.35$, we do not reject $H_0$.

**Conclusion:** At the 1% level, the data do not show that the two graders have different variance. Both are grading with similar inconsistency.

### Trade-Off: Sensitivity to Normality

Here's the catch. The F-test for comparing two variances is *very* sensitive to departures from normality. If your data are even slightly skewed or have outliers, the test can give a biased result—falsely rejecting or falsely failing to reject. Other hypothesis tests in this book are more forgiving of non-normality. Not this one. Before running an F-test for variances, look at your data. Draw a histogram or a normal quantile plot. If the data aren't close to normal, consider a different test or be cautious in interpreting results.

---

## Concept 2: Variance as Explanation—Between and Within Groups

### Partitioning the Variation

Now we leave variance testing behind and move to the central move of ANOVA: **partitioning total variation into parts explained by group membership and parts left unexplained**.

Suppose you measure the heights of people in three cities: New York, Denver, and Seattle. You record 10 people in each city. When you plot all 30 heights, you see variation. Some of that variation might be because Denver is at elevation and people there grow taller on average. Some variation is just individual differences within each city. ANOVA asks: how much of the total variation is explained by city (between-groups variation) versus how much is within each city (within-groups variation)?

This is where ANOVA earns its name: it analyzes variance by breaking it into pieces.

Let's define notation:
- $k$ = number of groups (3 cities)
- $n_j$ = sample size in group $j$
- $n$ = total sample size ($n_1 + n_2 + n_3 = 30$)
- $\bar{x}_j$ = mean of group $j$
- $\bar{x}_{\text{grand}}$ = grand mean (mean of all 30 observations)
- $s_j^2$ = variance within group $j$

**Sum of Squares Total** captures all variation:

$$SS_{\text{total}} = \sum_{i=1}^{n} (x_i - \bar{x}_{\text{grand}})^2$$

This is the sum of squared deviations from the grand mean. A large value means people's heights vary a lot.

**Sum of Squares Between** captures variation explained by group differences:

$$SS_{\text{between}} = \sum_{j=1}^{k} n_j (\bar{x}_j - \bar{x}_{\text{grand}})^2$$

For each city, we ask: how far is that city's mean from the grand mean, and how many people are in that city? Multiply, square, and sum. If all city means were identical to the grand mean, this would be zero. The farther city means spread out, the larger $SS_{\text{between}}$.

**Sum of Squares Within** is what's left—the variation not explained by group membership:

$$SS_{\text{within}} = SS_{\text{total}} - SS_{\text{between}}$$

Or equivalently, it's the sum of squared deviations from each observation to its group mean:

$$SS_{\text{within}} = \sum_{j=1}^{k} \sum_{i \in \text{group } j} (x_i - \bar{x}_j)^2$$

This is "error"—the noise, the random fluctuation around each city's mean. It's what ANOVA can't explain.

### Mean Squares: Variance Estimates

Raw sums of squares depend on sample size, so we divide by degrees of freedom to get *mean squares*—which are variance estimates.

$$MS_{\text{between}} = \frac{SS_{\text{between}}}{k - 1}$$

$$MS_{\text{within}} = \frac{SS_{\text{within}}}{n - k}$$

The degrees of freedom make sense: for between-groups, you have $k$ group means but they're constrained to average to the grand mean, so $k - 1$ free choices. For within-groups, you have $n$ total observations but $k$ group means constrain them, leaving $n - k$ free choices.

### Trade-Off: Sensitivity to Assumptions

ANOVA assumes:
1. Each group is normally distributed.
2. All groups have equal variances (this is called *homogeneity of variance*).
3. Observations are independent.

In practice, ANOVA is robust—it tolerates modest violations of normality and unequal variances, especially if sample sizes are large and equal across groups. But *don't* ignore these assumptions. Before analyzing, plot your data. Use a Levene test or Bartlett test to check for equal variances. If violations are severe, consider a non-parametric alternative (Kruskal-Wallis test) or a transformation of the data (e.g., log scale for skewed data).

---

## Concept 3: The F-Statistic and the Omnibus Test

### Building the Test Statistic

The *F* statistic in ANOVA is the ratio of the two mean squares:

$$F = \frac{MS_{\text{between}}}{MS_{\text{within}}}$$

Here's the intuition. Under the null hypothesis (all group means are equal), both the numerator and denominator estimate the same population variance. Sampling error alone contributes to variation in both. So $F$ should be close to 1.

But if the null hypothesis is false—if at least one group mean differs—then $MS_{\text{between}}$ is inflated. It now contains both the population variance plus an extra component from the genuine differences between groups. Meanwhile, $MS_{\text{within}}$ still estimates just the population variance. So the ratio $F$ climbs above 1.

The larger $F$, the stronger the evidence against $H_0$.

### Worked Example: Three Diet Plans

Three different diet plans are tested for mean weight loss. Four people follow Plan 1, three follow Plan 2, three follow Plan 3. Here are the weight losses (in pounds):

| Plan 1 | Plan 2 | Plan 3 |
|--------|--------|--------|
| 5      | 3.5    | 8      |
| 4.5    | 7      | 4      |
| 4      | 4.5    | 3.5    |
| 3      |        |        |

First, calculate group sums and means:
- Plan 1: sum = 16.5, mean = 4.125
- Plan 2: sum = 15, mean = 5
- Plan 3: sum = 15.5, mean = 5.167
- Grand total = 47, grand mean = 4.7

Calculate $SS_{\text{total}}$:
$$SS_{\text{total}} = (5 - 4.7)^2 + (4.5 - 4.7)^2 + \cdots = 23.1$$

Calculate $SS_{\text{between}}$:
$$SS_{\text{between}} = 4(4.125 - 4.7)^2 + 3(5 - 4.7)^2 + 3(5.167 - 4.7)^2 = 2.246$$

Calculate $SS_{\text{within}}$:
$$SS_{\text{within}} = 23.1 - 2.246 = 20.854$$

Degrees of freedom:
- $df_{\text{between}} = 3 - 1 = 2$
- $df_{\text{within}} = 10 - 3 = 7$

Mean squares:
- $MS_{\text{between}} = 2.246 / 2 = 1.123$
- $MS_{\text{within}} = 20.854 / 7 = 2.979$

Test statistic:
$$F = 1.123 / 2.979 = 0.377$$

The ANOVA table summarizes:

| Source | Sum of Squares | df | Mean Square | F     |
|--------|----------------|----|-------------|-------|
| Between | 2.246         | 2  | 1.123       | 0.377 |
| Within  | 20.854        | 7  | 2.979       |       |
| Total   | 23.1          | 9  |             |       |

The $F$ statistic is 0.377, which is *below* 1. This suggests that between-group variation is actually *smaller* than within-group variation—the opposite of what we'd see if the diets were different. At any reasonable significance level (e.g., 5%), we would not reject $H_0$. The data do not show that the three diets lead to different weight losses.

---

## Concept 4: Interpreting the ANOVA Table and Making a Decision

### The ANOVA Table as Scaffold

The ANOVA table is a standard way to organize results. Software (R, Python, Excel, most statistics packages) produces one automatically. Understanding each column helps you interpret results.

| Source | SS | df | MS | F | p-value |
|--------|----|----|----|----|---------|
| Between | $SS_B$ | $k-1$ | $MS_B = SS_B/(k-1)$ | $F = MS_B/MS_W$ | $P(F > F_{\text{obs}})$ |
| Within | $SS_W$ | $n-k$ | $MS_W = SS_W/(n-k)$ | | |
| Total | $SS_T$ | $n-1$ | | | |

- **Source:** identifies what variation you're looking at
- **SS:** the sum of squares
- **df:** degrees of freedom
- **MS:** the variance estimate (sum of squares ÷ degrees of freedom)
- **F:** the test statistic
- **p-value:** the probability of observing an F at least as large as yours, *if* $H_0$ is true

### Running a Full Hypothesis Test

Let's say you're comparing yields from four farming methods. You randomly assign fields and collect data. Your null hypothesis is:

$$H_0: \mu_1 = \mu_2 = \mu_3 = \mu_4$$

Your alternative hypothesis is:

$$H_a: \text{At least two of the means are not equal}$$

You compute the ANOVA table and get $F = 4.2$ with $df_{\text{numerator}} = 3$ and $df_{\text{denominator}} = 16$. Software tells you $p\text{-value} = 0.0207$.

At the 5% significance level, since $p\text{-value} = 0.0207 < 0.05$, you reject $H_0$.

**Conclusion:** There is sufficient evidence at the 5% level that at least one farming method produces a different mean yield than the others.

### An Important Caveat: The Omnibus Test Only Tells You *That* a Difference Exists, Not *Which* Groups Differ

This is where many students get confused. ANOVA rejects $H_0$ and says "at least one pair of means differs." It does not say *which* pair. If you want to know whether Method 1 differs from Method 2, or whether Method 3 differs from Method 4, you need a *post-hoc test*—a follow-up comparison that controls Type I error across multiple comparisons.

Common post-hoc tests include Tukey's HSD (honestly significant difference), Bonferroni correction, and others. These tests run pairwise comparisons while keeping the family-wise error rate at your chosen $\alpha$ level. For now, know that they exist. Your instructor may cover them or may leave them for a later course.

### Right-Tailed Test

The ANOVA test is *always* right-tailed. We reject $H_0$ when $F$ is large, not when it's small. This is because under $H_0$, $MS_{\text{between}}$ and $MS_{\text{within}}$ estimate the same thing, so $F$ should be near 1. A large $F$ (far out in the right tail) suggests the null hypothesis is false.

---

## Scale Shift: From Classrooms to Multi-Site Clinical Trials

One-way ANOVA handles many designs. In Nik's teaching experience, the simplest is the classroom intervention: does one teaching method produce higher test scores than another? You have maybe 4 groups, 25 students per group, you measure a test score.

Now scale up. A pharmaceutical company is testing a new drug at three dose levels (0 mg, 100 mg, 200 mg) across four hospitals in different regions. Each hospital enrolls 60 patients (20 per dose). You measure a health outcome after 12 weeks. Now you have 12 groups (4 hospitals × 3 doses). The ANOVA table grows, but the logic is the same: partition variation, test whether doses or hospitals (or both, though that's two-way ANOVA) matter.

Scale further. A meta-analysis combines data from 20 studies, each testing the same drug at a different dose in a different population. The analyst wants to ask: across all studies, does dose matter for the outcome? You can run ANOVA, or you can use mixed-effects models that account for between-study variation differently. The fundamental question is the same.

---

## Integration and Synthesis

You've now seen two statistical techniques that use variance in different ways:

1. **F-test for two variances** (Concept 1): Do two populations have equal variance? One specialized use.
2. **One-way ANOVA** (Concepts 2–4): Do three or more group means differ? A much more common tool.

Both rely on the F distribution. Both partition variation—one across two populations' variances, the other across groups' means and residual noise. Both control Type I error, though ANOVA's control is more sophisticated (it corrects for running one test instead of many pairwise t-tests).

The choice of method depends on your question and your data. A few rules of thumb:

- If you have two groups and want to compare means, use a t-test, not ANOVA (though ANOVA and t-test give the same p-value in that case).
- If you have three or more groups and want to compare means, use one-way ANOVA.
- If you're concerned about different variance in your groups, either use Welch's ANOVA (a variant that doesn't assume equal variances) or check for equal variances first.
- If ANOVA rejects $H_0$, run a post-hoc test to find which groups differ.

---

## Graduated Exercises

### Warm-Up: Identifying Components

1. A researcher measures typing speed (words per minute) for people using three keyboard layouts: QWERTY, Dvorak, and AZERTY. She collects data from 10 people per layout.
   - How many groups are there?
   - What is $n$ (total sample size)?
   - What is $k$?
   - What is $df_{\text{between}}$?
   - What is $df_{\text{within}}$?

**Answers:** 3 groups; $n = 30$; $k = 3$; $df_{\text{between}} = 2$; $df_{\text{within}} = 27$.

2. You see an ANOVA table with $df_{\text{total}} = 19$ and $df_{\text{between}} = 3$. How many groups were tested?

**Answer:** $k - 1 = 3 \Rightarrow k = 4$ groups.

### Application: Computing Sums of Squares

3. Three groups have the following data:
   - Group A: 10, 12, 14 (mean = 12)
   - Group B: 8, 10, 12 (mean = 10)
   - Group C: 15, 17, 19 (mean = 17)
   - Grand mean = 13

   Compute $SS_{\text{between}}$, $SS_{\text{within}}$, and $SS_{\text{total}}$.

   Step 1: $SS_{\text{between}} = 3(12-13)^2 + 3(10-13)^2 + 3(17-13)^2 = 3(1) + 3(9) + 3(16) = 78$

   Step 2: $SS_{\text{within}} = [(10-12)^2 + (12-12)^2 + (14-12)^2] + [(8-10)^2 + (10-10)^2 + (12-10)^2] + [(15-17)^2 + (17-17)^2 + (19-17)^2] = 8 + 8 + 8 = 24$

   Step 3: $SS_{\text{total}} = 78 + 24 = 102$

### Synthesis: Full ANOVA and Interpretation

4. A farmer tests four fertilizer blends on identical plots of corn. Eight plots per blend. The ANOVA table is:

   | Source | SS | df | MS | F |
   |--------|----|----|----|----|
   | Between | 240 | 3 | 80 | 2.5 |
   | Within | 960 | 28 | 34.3 | |
   | Total | 1200 | 31 | | |

   At the 5% significance level, is there evidence that the fertilizer blends produce different mean yields?

   The critical value for $F_{3,28}$ at the 5% level is approximately 2.95. Since our observed $F = 2.5 < 2.95$, we do not reject $H_0$. Alternatively, using software, the p-value would be approximately 0.080, which is greater than 0.05. **Conclusion:** There is insufficient evidence at the 5% level that the four fertilizer blends produce different mean corn yields.

### Challenge: Detecting Violations and Choosing Tests

5. You design a study comparing three teaching methods. You have 12 students per method and measure test scores. Before running ANOVA, you check assumptions:
   - Normality: A normal quantile plot shows one outlier in Method A.
   - Equal variances: Variance in Method A is 85, Method B is 92, Method C is 140.

   Should you proceed with standard one-way ANOVA? What concerns do you have?

   **Answer:** Proceed with caution. The outlier in Method A is worth investigating—remove it if it's a data-entry error, or justify keeping it. The variances are not wildly different (Method C is largest at 140 vs Method A at 85), but the ratio is notable. You could use Welch's ANOVA (does not assume equal variances) or perform Levene's test for equal variances to get a p-value. If Levene's test rejects, Welch's ANOVA is safer.

---

## Chapter Summary

The *F* distribution is the distribution of the ratio of two independent variance estimates from normal populations. Named for Ronald Fisher, it's right-skewed and always non-negative. It shows up in two contexts: comparing two population variances, and one-way ANOVA.

*One-way ANOVA* tests whether three or more group means are equal by partitioning total variation into between-groups variation (explained by group membership) and within-groups variation (residual noise). The test statistic is $F = MS_{\text{between}} / MS_{\text{within}}$. Under $H_0$, this ratio should be near 1; large values (far in the right tail) provide evidence against $H_0$.

The method assumes normality and equal variances across groups, though it's fairly robust to modest violations, especially with balanced designs. When ANOVA rejects $H_0$, you know that at least one group mean differs, but you need post-hoc tests to identify which groups.

ANOVA solves a fundamental problem in inference: it lets you compare multiple groups while controlling the family-wise Type I error rate—the probability of making at least one false positive across all comparisons. This is far more efficient than running many separate t-tests.

---

## Connections Forward

Linear regression (Chapter 13) uses many of the same ideas. You'll partition variation into explained (by the regression line) and residual (unexplained), build F-tests, and interpret coefficient tables that look similar to ANOVA tables. The concepts here—sums of squares, degrees of freedom, hypothesis tests using variance ratios—carry forward.

Two-way ANOVA (beyond the scope of this book) extends this to two factors simultaneously: Does fertilizer matter? Does water? Do they interact? The partition of variation becomes more intricate, but the logic remains.

Mixed-effects models and hierarchical regressions generalize ANOVA to settings where data have natural groupings (students within schools within districts) and where you want to estimate random variation at each level. But the foundation is one-way ANOVA.

---

## Questions Addressed

**What would change my mind?** If a large randomized trial showed that ANOVA's assumption of equal variances was more consequential than we currently believe—that even modest violations led to substantial Type I error inflation—I would recommend Welch's ANOVA as the default for all one-way comparisons. For now, I believe standard ANOVA with a preliminary check for equal variances is appropriate for most introductory applications.

**Still puzzling:** Why, under the null hypothesis of equal population means, does $MS_{\text{between}}$ estimate the same population variance as $MS_{\text{within}}$? The answer involves the structure of the sampling distribution of group means and how group size inflates the between-groups variance estimate. It's elegant mathematics, but I find the intuition slippery—I have to re-derive it each time to convince myself.

---

## Tags

#F-distribution #ANOVA #hypothesis-testing #variance-partition #multiple-comparisons #Fisher #omnibus-test #between-within-variation #degrees-of-freedom
---

## LLM Exercise — Chapter 12: F-Distribution and One-Way ANOVA (Analyze One Dataset Project)

**Project:** Analyze One Real Dataset.
**What you're building this chapter:** one-way ANOVA comparing 3+ groups on a quantitative outcome.
**Tool:** **Claude Code** + **Claude Project**.

---

**The Prompt:**

```
Chapter 12 of my Analyze-One-Dataset project. Chapter 12 covered:
the F-distribution (ratio of variances; right-skewed; depends on
two df parameters); one-way ANOVA — compare means across 3+
groups; the ANOVA table:
- SSB (Sum of Squares Between groups) = Σ n_i (x̄_i − x̄)²
- SSW (Sum of Squares Within groups) = Σ Σ (x_ij − x̄_i)²
- MSB = SSB / (k − 1), where k = number of groups
- MSW = SSW / (n − k), where n = total sample size
- F = MSB / MSW
- df₁ = k − 1; df₂ = n − k
Big F means between-group variance dominates within-group variance
(groups are genuinely different). Multiple-comparisons problem:
running many t-tests inflates Type I error; ANOVA is the joint
test that handles this.

Write the brief's "ANOVA Analysis" section in 500-700 words.

1. **Pick a categorical variable with 3+ levels and a quantitative
   outcome.** Examples: comparing exam scores across 4 schools;
   comparing salary across 5 industries; comparing reaction time
   across 3 conditions.

2. **State the hypotheses.**
   - H₀: μ₁ = μ₂ = μ₃ = ... = μ_k (all group means equal)
   - H_a: at least one μ_i differs from another.

3. **Check assumptions.**
   - Independence of observations.
   - Approximate normality within each group (or large group n).
   - Roughly equal variances across groups (Levene's test, or
     visual check via boxplot).
   - If unequal variances and unequal n: consider Welch's ANOVA.

4. **Build the ANOVA table.**
   - Compute group means and overall mean.
   - Compute SSB, SSW, MSB, MSW, F.
   - Show the table.

5. **Test the result.** Compare F to F_α; or report p-value from
   scipy.stats.f_oneway(group1, group2, group3, ...).

6. **Post-hoc tests if significant.** If ANOVA rejects, you know
   AT LEAST ONE pair differs but not which. Run Tukey's HSD
   (`statsmodels.stats.multicomp.pairwise_tukeyhsd`) to identify
   the specific pairs. Tukey's HSD controls family-wise error
   rate (handles multiple-comparisons honestly).

7. **Effect size.** η² (eta-squared) = SSB / SS_Total tells you
   what fraction of variance is between-groups. Small effect:
   ~0.01; moderate: ~0.06; large: ~0.14.

End with: which groups in your data are significantly different
from each other, and which aren't? The ANOVA + Tukey combination
gives the full picture.
```

---

**What this produces:** A 500-700 word section with ANOVA table, F-test result, post-hoc analysis. The "which pairs differ" output from Tukey is the actionable finding.

**How to adapt this prompt:**

- *For your own project:* If your dataset only has 2-level categorical variables, this section becomes a 2-sample t-test (already done in Ch 10). Find a 3+ level variable if possible.
- *For ChatGPT / Gemini:* Works as written.
- *For Claude Code:* `scipy.stats.f_oneway` for ANOVA; `statsmodels.stats.multicomp.pairwise_tukeyhsd` for Tukey.
- *For a Claude Project:* Append.

**Connection to previous chapters:** Ch 10's two-sample t-test generalizes to Ch 12's ANOVA for 3+ groups.

**Preview of next chapter:** Chapter 13 is the closer — linear regression and correlation. You'll fit a regression line to two quantitative variables in your dataset, plus compile the full analysis report.


---

## 🕰️ AI Wayback Machine

**Ronald Fisher** was invented analysis of variance, the F-distribution, and the core machinery of modern experimental statistics — with an entangled eugenics legacy.

**Run this:**

```
Who is Ronald Fisher, and how does their work connect to ANOVA and the F-distribution we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Ronald Fisher"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Ronald Fisher's framework to a small dataset you actually have.
- Add a constraint: "Answer including criticisms or limits of Ronald Fisher's framework."

What changes? What gets better? What gets worse?
