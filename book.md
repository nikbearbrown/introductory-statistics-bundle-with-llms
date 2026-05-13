# Introductory Statistics

## Title
Introductory Statistics — A Working Course

## Subtitle
Sampling, distributions, inference, and the everyday statistics that decide votes, drugs, and hiring decisions — with the math shown on the page.

## Author
Nik Bear Brown.

## Audience

This book is written for the undergraduate taking their first college statistics course, typically in their second year. They are not math majors. They are studying psychology, biology, business, education, nursing, sociology, criminal justice, economics, public health, or any of the fields where the math of inference is a working tool, not the subject. They have had at least one college math course (often college algebra or pre-calc); some have had calculus.

Specifically:

- Sophomores in the social and life sciences who need stats for research methods.
- Business and economics students who will read regression output for the rest of their careers.
- Nursing and public-health students who will read randomized trials and meta-analyses.
- Pre-med students who will read p-values in the medical literature.
- Adult learners returning for a working knowledge of inference.

This is not a math statistics course (no measure theory, no proofs of distribution theorems). It is the standard introductory sequence from sampling through linear regression — sampling and data, descriptive statistics, probability, discrete and continuous random variables, the normal distribution, the central limit theorem, confidence intervals, hypothesis testing (one-sample, two-sample, chi-square, ANOVA), and linear regression and correlation.

The math shows up. The Normal density, the t-distribution, z-scores, p-values, F-statistics, residuals — these are all here, calculated on the page, with the geometry of the distributions made visible.

## Scope

The thirteen chapters cover, in order:

1. **Sampling and data** — populations, samples, parameters, statistics, types of variables, sampling methods, experimental design.
2. **Descriptive statistics** — visualization, mean/median/mode, range, standard deviation, percentiles, box plots.
3. **Probability topics** — terminology, independent and mutually exclusive events, conditional probability, Bayes thinking through trees and tables.
4. **Discrete random variables** — pmf, expected value, binomial, geometric, hypergeometric, Poisson.
5. **Continuous random variables** — the uniform and exponential, the idea of a density, areas as probabilities.
6. **The normal distribution** — z-scores, the empirical rule, calculations from the standard normal.
7. **The central limit theorem** — sample means, sample sums, the standard error.
8. **Confidence intervals** — for one mean (z and t), for one proportion, sample size formulas.
9. **Hypothesis testing with one sample** — the four-step procedure, errors, p-values, t-tests for means, z-tests for proportions.
10. **Hypothesis testing with two samples** — independent and paired, two means, two proportions.
11. **The chi-square distribution** — goodness-of-fit, independence, homogeneity, single variance.
12. **The F-distribution and one-way ANOVA** — comparing several means, sums of squares, the ANOVA table.
13. **Linear regression and correlation** — scatter plots, the line of best fit, slope and intercept, residuals, $r$ and $r^2$, prediction.

Out of scope: multiple regression beyond a brief mention, time-series methods, Bayesian inference as a parallel framework, nonparametric methods.

## Voice notes for this book

The Attenborough × Feynman v1.1 voice applies, with adjustments for the working-statistics audience.

**Cold opens earn their place.** A chapter on sampling opens at a polling firm in the days before a tight election. A chapter on the central limit theorem opens with Quincunx beans falling into a Galton board. A chapter on hypothesis testing opens at an FDA advisory committee voting on a drug. The scenes ground the math in decisions students will recognize from their own fields.

**Math density.** Higher than contemporary-mathematics' liberal-arts treatment. Distributions are calculated on the page. Z-scores and t-scores are computed step by step. The Normal density formula gets shown when it earns its place. Confidence interval formulas get derived from the CLT. Hypothesis test machinery is built — null, alternative, statistic, distribution, p-value — not invoked as a checklist.

**Notation taught, not assumed.** Greek letters get introduced ("$\mu$ — mu, the population mean; the lowercase Greek m"). Subscripts get explained. Distinction between population parameter and sample statistic is named on first use and reinforced.

**Grounded examples in students' fields.** Not "let X be a random variable from some distribution." Instead: drug trial outcomes, polling samples, lab measurements with known variability, salary distributions, batting averages, lab assays. When the source uses an abstract example, replace with a field-specific concrete one and verify the math holds.

**Civic and methodological stakes.** Where the math has consequences for medicine, hiring, criminal justice, polling — name them. P-hacking, sample bias, regression to the mean, base-rate neglect — these are the failure modes that produce bad decisions, and the chapter that introduces the tool also names how it gets misused.

**Connect chapters.** Each chapter builds on the one before. Confidence intervals (Ch 8) require the central limit theorem (Ch 7). Hypothesis testing (Ch 9) reuses the CLT. ANOVA (Ch 12) generalizes the two-sample t-test (Ch 10). The book is a single argument across thirteen chapters; voice should make that argument visible.

## Prerequisites assumed

- Comfort with algebra: solving for $x$, plugging into formulas, manipulating fractions.
- Reading a coordinate plane and a line graph.
- Basic combinatorics (permutations, combinations) — re-introduced when needed.
- Willingness to think probabilistically.

No calculus required. No measure theory. The integration in continuous random variables is treated as "area under the curve" with the calculus left implicit.

## Author byline convention

Author is Nik Bear Brown. First-person voice when taking a position. "I've watched intro-stats students get tangled in p-values for a decade — here is what finally helps them..." rather than "It is often noted that..."

## Style file location

Voice ground truth: workshop-root `style/` and (if it exists) `books/introductory-statistics-bundle/style/`. Where the per-book style is empty, agents should anchor on `books/contemporary-mathematics/chapters/01-sets.md` and `books/contemporary-mathematics/chapters/08-statistics.md` — both are recently approved math chapters in the same Attenborough × Feynman register, and Chapter 8 is the closest topical match.
