# Revision Notes

Track what you've added, removed, or rewritten here.

## 2026-05-07 — book.md created

Drafted `book.md` for the bundle from scratch (book had no metadata). Audience: undergraduates in psych/bio/business/nursing/education taking their first college statistics course. Higher math density than contemporary-mathematics' liberal-arts treatment — distributions calculated on the page, Greek letters introduced explicitly, hypothesis test machinery built rather than invoked. No pilot run; voice anchored on `books/contemporary-mathematics/chapters/01-sets.md` (canonical) and `books/contemporary-mathematics/chapters/08-statistics.md` (closest topical match, recently approved).

## 2026-05-07 — Attenborough × Feynman v1.1 conversion run: Chapters 1–13

13 chapters dispatched in parallel to subagents; each read book.md plus the two contemporary-mathematics voice anchors before drafting. Source folders deleted after Combined Test passed and ≥ 3,500-word floor cleared. `_toc.md` rewritten to flat structure.

| Chapter | Slug | Words | Status | Notes |
|---|---|---:|---|---|
| 01 | sampling-and-data | 4,863 | OK | 5 source modules → 3 concepts (population/sample/parameter/statistic; data types & measurement levels; observational vs. experimental). Cold open: Literary Digest 1936. Sampling-method taxonomy compressed; ethics deferred. |
| 02 | descriptive-statistics | 5,018 | OK | 8 source modules → 3 concepts (visualization; measures of center; measures of spread). SD computed step by step. Greek-vs-Roman notation distinguished explicitly. |
| 03 | probability-topics | 4,969 | OK | 6 source modules → 3 concepts (sample space & events; independence vs. mutual exclusivity & multiplication rule; addition, conditional, Bayes). Cold opens: mammogram, strep test, drug test. Base-rate neglect named. |
| 04 | discrete-random-variables | 6,161 | OK | 5 source modules → 4 concepts (RV/PMF; expected value & variance; binomial; Poisson). Geometric and hypergeometric deferred. |
| 05 | continuous-random-variables | 4,515 | OK | 4 source modules → 3 concepts (continuous RV & density; uniform; exponential). Memoryless property covered. |
| 06 | the-normal-distribution | 4,322 | OK | 4 source modules → 3 concepts (the normal density; z-scores; using normal probabilities). Galton's quincunx as cold open. Empirical 68-95-99.7 trade-off named. |
| 07 | the-central-limit-theorem | 4,982 | OK | 5 source modules → 3 concepts (sampling distribution of $\bar{X}$; CLT statement & conditions; CLT applications). The keystone — confidence intervals (Ch 8) and hypothesis testing (Ch 9) rest on it. Standard error derivation shown. |
| 08 | confidence-intervals | 4,885 | OK | 5 source modules → 3 concepts (CI for one mean σ known z; CI for one mean σ unknown t; CI for one proportion). Gosset's Guinness pseudonym in cold open. Common misconception ("95% confidence" = procedure, not parameter) named explicitly. |
| 09 | hypothesis-testing-with-one-sample | 5,946 | OK | 5 source modules → 3 concepts (testing logic — H0/H1/α/β/p-value; one-sample mean tests z and t; one-sample proportion test). Replication crisis and p-hacking integrated. Forbidden-phrase fixes: 2 "clearly" hits removed. |
| 10 | hypothesis-testing-with-two-samples | 4,218 | OK | 7 source modules → 3 concepts (independent two-sample t; paired t reduces to one-sample t on differences; two-proportion z). Welch correction for unequal variances. Cohen's d for effect size. F-test for variances deferred to Ch 11/12. |
| 11 | the-chi-square-distribution | 4,143 | OK | 8 source modules → 3 concepts (chi-square distribution; goodness-of-fit; test for independence). Mendel's peas as cold open. Single-variance test deferred for scope. |
| 12 | f-distribution-and-one-way-anova | 3,584 | OK | 6 source modules → 3 concepts (F-distribution; ratio of two variances test; one-way ANOVA). Rothamsted wheat field as cold open. Family-wise Type I error inflation as the why. Two-way ANOVA deferred. |
| 13 | linear-regression-and-correlation | 5,402 | OK | 8 source modules → 3 concepts (correlation r; least-squares regression line; residuals & r²). Galton's pea-size regression as cold open. Closing summary reflects on the book's full arc — sampling → description → distributions → CLT → CIs → tests → ANOVA → regression. |

**Totals.** 13 chapters, 63,008 words. 39 companion files (13 each in `pantry/`, `images/`, `bookmaps/`). All 13 chapters above the 3,500-word floor. Forbidden-phrase audit: zero hits across all 13 after fix to Chapter 9.

**Source folders.** All 13 source subfolders deleted after verification.

**Voice consistency.** No book pilot — voice anchored from contemporary-mathematics' approved Chapter 1 (Sets) and Chapter 8 (Statistics). Worked: each subagent read both anchors before drafting. Light variation across chapters (Ch 7 leans into the keystone weight of CLT; Ch 9 names the replication crisis explicitly; Ch 13 reflects on the book's whole argument). The four voice rules — cold open mid-scene, concept-section cold opens, every term glossed on first use with etymology, named trade-offs — hold across all 13.

**Math density.** Higher than contemporary-mathematics' gen-ed treatment. Distributions calculated on the page (binomial PMF, Poisson, normal density, t, F, chi-square). Greek letters introduced explicitly with Roman counterparts ($\mu$ vs $\bar{x}$, $\sigma$ vs $s$, $p$ vs $\hat{p}$). Standard error derived from CLT in Ch 7, then reused in Ch 8 and Ch 9.

**Civic and methodological stakes named.** Sampling bias (Literary Digest), base-rate neglect (medical screening), p-hacking and replication crisis (Ch 9), procedural vs parameter interpretation of confidence (Ch 8), correlation ≠ causation (Ch 13).

**TOC.** Rewritten to flat structure pointing at the 13 chapter files.

**Known follow-ups.**
- Chapter 12 (F-distribution and ANOVA) came in at 3,584 words — just above floor. Source covered six modules but agent compressed aggressively to keep the chapter focused on three concepts. If you want it fuller, two-way ANOVA and post-hoc tests (Tukey, Bonferroni) are the natural additions; bookmap names them as deferred.
- Chapter 10 (HT two-sample) at 4,218 — also lean. Levene's test and pooled-vs-unpooled detail deferred to pantry.
- All deferred topics are catalogued in their respective bookmap files.


## 2026-05-12 — Running Project added: "Analyze One Real Dataset End-to-End"

Generated 13 end-of-chapter LLM Exercise blocks via the Running Project Exercise Generator. Project selected: **Analyze One Real Dataset End-to-End** — student picks one publicly-available dataset in Ch 1 and applies each chapter's techniques to it. Final deliverable: 5,000-8,000 word portfolio-quality statistical analysis report.

The architecture mirrors the book's content arc directly. Each chapter's prompt specifies what section of the report it adds:
- Ch 1: Foundation (dataset, sampling story, variable inventory, big question)
- Ch 2: Descriptive analysis (visualizations, summary statistics, outliers)
- Ch 3: Probability analysis (contingency tables, conditional probabilities, Bayes thinking)
- Ch 4: Discrete-variable analysis (binomial/Poisson fit)
- Ch 5: Continuous-variable analysis (uniform/exponential fit)
- Ch 6: Normality assessment (Q-Q plot, empirical rule)
- Ch 7: CLT verification via bootstrap simulation
- Ch 8: Confidence intervals + sample-size calculation
- Ch 9: One-sample hypothesis test (one specific claim tested)
- Ch 10: Two-sample comparison test + effect size
- Ch 11: Chi-square test of independence + Cramér's V
- Ch 12: One-way ANOVA + Tukey post-hoc
- Ch 13: Linear regression + final compiled report (with executive summary, conclusions, coda)

Methodological commitments baked in across all 13: every test must include effect size (not just p-value); Ch 6's normality-assessment is honest about non-Normal data; Ch 7's CLT demonstration is empirical (not just stated); Ch 8 enforces the correct CI interpretation discipline; Ch 9 forbids "accept H₀" language; Ch 10 requires effect-size discussion; Ch 13 requires a "what I'd refine" coda about limitations.

Tool recommendations: Claude Project for the building report; Claude Code essential for actual computation (Python with pandas, numpy, scipy.stats, matplotlib, seaborn); Cowork for Ch 13 final compilation. Several chapters (4, 5, 6, 7, 11, 12) are computationally intensive enough that hand-calculation isn't feasible — students need scipy/numpy.

Each block appended to the bottom of its chapter file. Total addition: ~12,000 words of new content across 13 chapters.

**Known follow-up:** Ch 4-5's discrete/continuous fitting work can be skimped if the student's dataset doesn't have obvious discrete count or continuous variables. The prompts handle this gracefully — note the situation, move on. But for datasets where these chapters apply richly (count-based — sports stats, manufacturing defects), they're some of the most pedagogically valuable.

**Cross-book note:** this is the first running project where Claude Code is genuinely essential (not just optional sidecar). The chapters from Ch 4 onward involve real numerical computation that's impractical by hand. Students without Claude Code access would need a Jupyter notebook + Python, but the project doesn't work as a pure-conversation exercise.
