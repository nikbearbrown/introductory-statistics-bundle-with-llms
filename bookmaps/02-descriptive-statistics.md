# Bookmap — Chapter 2 Descriptive Statistics

**Source:** OpenStax *Introductory Statistics*, Chapters on Descriptive Statistics (8 modules)  
**Voice:** Attenborough × Feynman v1.1  
**Date:** 2026-05-07

---

## Summary of source modules

The eight OpenStax modules on descriptive statistics cover:

1. **m53786** — Introduction to descriptive statistics; the role of graphs and numerical summaries
2. **m53791** — Stem-and-leaf plots, line graphs, bar graphs, stemplots, and frequency polygons
3. **m53795** — Quartiles, percentiles, and the interquartile range (IQR)
4. **m53802** — Measures of center: mean, median, mode; calculating mean from frequency tables
5. **m53799** — Sigma notation and the arithmetic mean
6. **m62299** — Geometric mean and its applications in growth rates
7. **m53804** — Shape of distributions: symmetry, skewness, coefficient of variation
8. **m53806** — Measures of spread: range, variance, standard deviation; types of variability

---

## Concepts selected for the chapter

The rewrite synthesizes these eight modules into three core concepts:

### Concept 1: Getting the shape (Visualization before you measure)
**Source modules:** m53786, m53791, m53804 (partial)

This concept uses stemplots, histograms, and box plots to help students *see* where data cluster before applying any formula. The OpenStax modules introduce many graph types (frequency polygons, time-series, line graphs); the rewrite prioritizes histogram and box plot as the most general-purpose visuals. Stem-and-leaf is included as an alternative for small datasets. The "lying with statistics" section (how axis choice distorts perception) is deferred to keep the chapter focused on core measures.

**Teaching moves:**
- Cold open with a histogram, not an abstract definition
- Box plot introduced as a compact summary of five-number information
- Outlier detection (1.5 × IQR rule) appears here, not buried in a later section
- Emphasis: shape reveals which center measure to trust

### Concept 2: Measuring the center (Mean, median, mode)
**Source modules:** m53802, m53799, m62299 (partial)

The three center measures are presented in order of conceptual difficulty and real-world impact: mean (easiest, most sensitive to outliers), median (robust, the honest choice when outliers exist), mode (useful for categorical data and describing frequency peaks).

Geometric mean is deferred. OpenStax introduces it in m62299 with applications to growth rates and compound returns; the rewrite treats it as an optional extension (it appears in the pantry but not in the main narrative). For an introductory course, arithmetic mean sufficient; geometric mean belongs in a finance or economics context.

**Teaching moves:**
- Mean introduced as a balance point (physical intuition)
- Immediately followed by a salary example showing mean's failure when outliers exist
- Median as the robust alternative, with the DMV and salary examples side by side
- Mode for categorical data and frequency peaks
- Relationship between center measures and distribution shape (skewness) previewed

### Concept 3: Measuring spread (Range, IQR, variance, standard deviation)
**Source modules:** m53795, m53804, m53806

Range is presented as the crude version (max − min). IQR is positioned as the robust version (ignoring extremes). Variance and standard deviation are calculated step-by-step, with emphasis on what the squared deviations achieve (all positive, amplifies outliers) and why we take the square root (return to original units, interpretability).

Percentiles and quartiles are included here because they are tools for measuring position and spread; the chapter uses them to set outlier boundaries (1.5 × IQR) and to answer location questions ("what score puts you in the top 10%?").

**Teaching moves:**
- Range: one sentence, noting its limitations
- IQR: robust to outliers, used for box plot and outlier detection
- Variance: the "average squared distance from the mean," not just a formula
- Standard deviation: square root returns to intuitive units; worked example shown step by step
- Percentiles: calculated using the interpolation formula, with two worked examples

---

## Ideas harvest for authors

### Cold opens (scenes anchoring the abstract)
- **Salary negotiation at tech company:** mean vs median pulled straight from OpenStax m53802's "small town with one billionaire" example, but relocated to a high-stakes interview (more memorable for undergraduates). This is the chapter cold open.
- **ER waiting room:** patient ages from OpenStax example, but reframed: "You're a hospital administrator. You look at the distribution. What story does it tell?" This could anchor a clinical-context chapter in health sciences.
- **Portfolio performance:** the chapter integration section uses investment returns. Possible cold open: "You're a wealth manager pitching to a retiree. Mean return is 6.2%. But that number alone would be misleading. Here's why..."

### Specification moves (what do these words actually mean?)
- **"Average" vs "mean" vs "arithmetic mean":** OpenStax notes this; the rewrite emphasizes that the colloquial "average" is the arithmetic mean, not the geometric mean or the weighted average. Etymology helps (Latin *medianus*, *variare*).
- **"Outlier" vs "extreme value":** An outlier is an observation that doesn't fit the pattern. An extreme value is simply at the tail end of a normal distribution. The 1.5 × IQR rule formalizes the distinction.
- **"Spread" vs "variation" vs "variability":** OpenStax uses these interchangeably; the rewrite treats them as synonyms and uses "spread" as primary (more intuitive for beginners).

### Trade-offs named explicitly
- **Mean vs median:** Mean is easy to compute, used in formulas throughout the book (central limit theorem, confidence intervals). Median is robust to outliers. When do you choose which? The rewrite answers: if data are symmetrical, either works; if outliers exist, median; if building inferential statistics (Chapters 7–13), mean (because it has known sampling properties).
- **Range vs IQR vs SD:** Range is quick; IQR is robust; SD is precise and connects to the normal distribution. Choose based on purpose: communicating to a general audience? Use range + one center measure. Detecting outliers? Use IQR. Probabilistic reasoning? Use SD.
- **Grouped vs ungrouped data:** OpenStax's m53802 covers mean calculation from frequency tables (grouped data). The rewrite includes this as a worked example in Pantry, noting: when you have only grouped data (intervals), you cannot recover the exact mean, only estimate using midpoints.

### Counterintuits and common errors
- **"A histogram always starts at zero":** No. The x-axis (the variable being measured) can start anywhere sensible. The y-axis (frequency) should start at zero to avoid lying.
- **"Standard deviation is always positive."** True. But variance can be zero (no spread). And the formula for outlier detection uses ± 1.5 × IQR (signed distances), not always positive.
- **"The median is the 50th percentile, always at position (*n* + 1) / 2."** True, but the calculation differs slightly depending on convention (some textbooks use *n* / 2, some use (*n* + 1) / 2). OpenStax uses (*n* + 1) / 2; the rewrite preserves this.

### Analogies and metaphors that work
- **The seesaw:** Mean as a balance point. If you load one side with an outlier (billionaire), the balance tips. The median is unmoved—it's just the middle position, indifferent to how far away the values are. (Used in the rewrite.)
- **The five-number summary as a snapshot:** Min, Q1, Median, Q3, Max are like a photograph of the data's skeleton—where it starts, where it clusters, where it ends. The box plot is that skeleton drawn on the page. (Used in the rewrite.)
- **Standard deviation as distance:** On average, how far are values from the mean? That's the standard deviation. If SD = 3, most values fall within about ±3 of the mean. (Used in the rewrite.)

### Mechanistic insights
- **Why divide by (*n* − 1) in sample variance, not *n*?** Bessel's correction: when you divide by *n*, you underestimate the population variance (because the sample mean is always closer to the data than the true population mean is). Dividing by *n* − 1 corrects this bias. Full explanation deferred to Pantry; intuition: "We're estimating a population parameter from a sample, so we use *n* − 1 to be conservative."
- **Why square the deviations?** Squaring makes them all positive (so they don't cancel out when summed). Squaring also amplifies large deviations, giving weight to outliers. This is a feature, not a bug—if you have an outlier, the SD will be large, alerting you to the spread. (Used in the rewrite.)
- **Why the 1.5 × IQR rule for outliers?** This is a convention, not a law. It comes from the assumption that if data are normally distributed, values beyond ±1.5 × IQR are rare. The rule is practical: it catches most anomalies without flagging too many false positives. (Noted in Pantry as "a convention that works well in practice.")

### Gaps and deferred topics
- **Geometric mean:** OpenStax m62299 explains geometric mean and its use in growth rates (investment returns, population growth, compound interest). Valuable for finance contexts, but not central to the introductory statistics course. The rewrite defers it; students studying applied financial statistics would encounter it in a dedicated chapter.
- **Median absolute deviation (MAD):** An alternative to standard deviation that is more robust to outliers (median of absolute deviations from the median). Not in OpenStax; not in the rewrite. Would be a useful alternative mentioned in an advanced course.
- **Coefficient of variation:** OpenStax m53804 mentions it; it's the ratio of SD to mean, useful for comparing spread across datasets with different scales. Not in the rewrite (too specialized for an introduction), but noted in Pantry as an advanced topic.
- **Time-series graphs, frequency polygons, pie charts:** OpenStax m53791 covers these. The rewrite omits them (focus on histogram and box plot as primary visuals). A companion chapter on "misleading graphics" or a section in Ch. 12 (regression) would address pie charts and frequency polygons.

### Connections forward
- **Chapter 3 (Probability):** Percentiles are used to answer "What is the probability that a value falls below the 75th percentile?" Box plots illustrate the symmetry or skewness that predict whether probability is uniform, binomial, or normal.
- **Chapter 6 (Normal Distribution):** Standard deviation becomes a unit of measurement. The empirical rule (68–95–99.7) uses SD to mark regions of probability. Z-scores are deviations from the mean, measured in SD units.
- **Chapter 7 (Central Limit Theorem):** The standard error (SD of a sample mean) is calculated using the population SD. The CLT connects population SD to the shape of the sampling distribution.
- **Chapter 9 (Hypothesis Testing):** The test statistic is (sample mean − null hypothesis mean) / standard error. SD is in the denominator. Outliers can inflate SD and weaken the test.
- **Chapter 13 (Linear Regression):** Residuals (observed − predicted) are analyzed using the same measures: mean, variance, outlier detection. Box plots of residuals check whether the model's assumptions hold.

---

## Pedagogical choices and rationales

### Why three concepts, not eight modules?
OpenStax's modular design treats each topic (histograms, stem plots, mean, median, quartiles, etc.) as a separate unit. The rewrite reorganizes around three questions: (1) What does the data *look like*? (2) Where is the *center*? (3) How *spread out* is it? This organization mirrors how a data analyst actually works: visualize first, measure center, measure spread, then summarize.

### Why include standard deviation so early?
Chapter 2 is the natural place to introduce SD. By Chapter 6 (Normal Distribution), students need to understand what σ means and how to interpret it. Deferring SD to later chapters risks students reaching Chapter 6 without intuition for the concept. The step-by-step calculation (in Pantry and worked examples) grounds the formula in real numbers.

### Why the 1.5 × IQR rule for outliers?
It's practical, widely used, and doesn't require students to assume a particular distribution shape (unlike rules based on the normal distribution, which we don't cover until Chapter 6). It's a convention, and we name it as such.

### Why "median, then mean" in Concept 2, not "mean first"?
Pedagogically, mean is easier to compute (just add and divide). But contextually, median is more intuitive for beginners: it's the middle value, which anyone understands without algebra. Presenting median first, then explaining why mean breaks with outliers, motivates the distinction. The chapter then builds the "use mean" argument for later chapters (sampling distributions, hypothesis tests).

---

## Materials referenced from source

All worked examples, data tables, and numerical problems are sourced from OpenStax modules and verified against the primary source. No fictional data sets. Where OpenStax provides a vague example ("customer wait times"), the rewrite adds a specific context (two supermarkets with different SDs) to make it memorable.

Formulas ($\mu$, $\overline{x}$, $s$, $s^2$, $\sigma$, $\sigma^2$, IQR, percentile rank) are standard and match OpenStax notation.

All exercises are rewritten in the Feynman style (clear, specific, grounded in context) but preserve the conceptual learning objectives from OpenStax's learning outcome tags.
