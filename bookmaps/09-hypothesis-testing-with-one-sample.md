# Bookmap: Chapter 9 — Hypothesis Testing with One Sample

Source: OpenStax *Introductory Statistics* (modules m55603, m55606, m55607, m55608, m55610)

Converted to Attenborough × Feynman v1.1 register (narrative-explanatory, scene-anchored, moral arrival at end).

---

## What this chapter actually teaches

**Module m55603 (Introduction):** The scientific method demands rigorous hypothesis testing to admit claims into the accepted body of knowledge. Statistics' role is not to develop theories but to test them. A hypothesis must come before data collection. Data do not create hypotheses; they test them. The stakes are real: a drug company's claim about efficacy, an engineer's assertion that a process is stable. Hypothesis testing provides the discipline to say "not yet proven" rather than accepting noise as signal.

**Module m55606 (Null and Alternative Hypotheses):** Hypotheses come in pairs: H₀ (null, status quo) and Hₐ (alternative, what we're testing). The null always contains equality. The alternative contains ≠, <, or >. The choice of symbols determines the test type and the nature of the claim we're making. If the alternative is μ ≠ 100, we reject H₀ if the sample mean is too far away in either direction. If the alternative is μ > 100, we only care about being too high. This is not just symbolic; it reflects different real-world questions.

**Module m55607 (Type I and Type II Errors):** You can make two mistakes: reject a true null (Type I, probability α) or fail to reject a false null (Type II, probability β). You can control α by setting the significance level. You cannot directly control β because there are infinitely many false alternative hypotheses. This asymmetry—the advantage given to the null—mirrors the burden-of-proof logic in courts. The defendant (null hypothesis) is presumed innocent until proven guilty beyond reasonable doubt.

**Module m55608 (Test Statistics and Critical Values):** Under H₀, the test statistic follows a known distribution (normal or t). The critical value is determined by α and the test type. If the calculated test statistic is more extreme than the critical value, you reject H₀. If not, you fail to reject. The p-value approach is equivalent: compute the probability of a test statistic this extreme under H₀. If p-value < α, reject. The critical value method and p-value method always agree, but p-values have become standard because they quantify the rarity of the data, not just whether they cross a threshold.

**Module m55610 (Worked Examples):** Tests on means (z when σ known and n large, or t when σ unknown or n small) and tests on proportions (z when np > 5 and nq > 5) follow the same five-step template. The examples show Jeffrey's swimming goggles, a salesperson's contract values, a filling machine's accuracy, and a bank's lending proportions. Each grounds the abstract machinery in a decision that matters. Each follows: set hypotheses, set α, calculate test statistic, compare to critical value, conclude.

---

## Angles and structure this chapter uses

1. **Asymmetry of the burden of proof:** The null is presumed true. The alternative must overcome this default with strong evidence. This reflects rational skepticism and historical wisdom (courts, scientific review), not mathematical necessity. It's a policy choice that makes false approval rare.

2. **Conditional probability and the p-value interpretation:** The most common error is interpreting p-value as P(H₀ | data) when it's actually P(data | H₀). The chapter clarifies this repeatedly because it's the linchpin of understanding what the test does and doesn't tell you.

3. **The machinery as protection against wishful thinking:** Without the test, you might notice your sample mean is slightly higher than the hypothesized value and declare victory. The test asks: is this difference large enough to be rare under the assumption that nothing changed? It's a discipline that protects against the human tendency to see what you want to see.

4. **Replication crisis as cautionary tale:** The chapter acknowledges that the misuse of hypothesis testing (p-hacking, multiple comparisons, failure to pre-register) has produced false findings in psychology, medicine, and other fields. This is not a flaw of the method; it's a flaw of its misapplication. The fix: pre-registration, adjustment for multiple comparisons, replication.

5. **Trade-offs and consequences:** Type I vs. Type II error. α = 0.05 (standard) vs. α = 0.01 (more conservative, in medical contexts) vs. α = 0.10 (more exploratory). Each choice reflects different consequences of being wrong.

---

## Ideas harvest for a textbook author

### Puzzles and scene openings
- FDA advisory committee voting on drug approval (sets up: what counts as "evidence"?)
- Court trial analogy (presumption of innocence → presumption of no effect)
- Manufacturing plant: is the machine broken or is this normal variation? (Why measure in standard deviations?)
- Goggles improve swimming speed: does the data prove it? (Real stakes, personal narrative)

### Specification moves
- "Hypothesis, from Greek hypothesis—a thing placed under, a foundation of an argument. Here it's the claim we test against data."
- "P-value: probability of data this extreme or more extreme if H₀ is true. It's not probability that H₀ is true given the data. The conditional direction matters."
- "Significance level α: a choice you make before the test. It's not a property of the data; it's a policy decision about how much false-rejection risk you'll accept."
- "Type I error (false positive): you reject a true null. Type II error (false negative): you let a false null stand. You can control α. β follows where it will."

### Mechanism-first explanations
- Central Limit Theorem → sampling distribution of X̄ is normal under H₀ → test statistic is how many standard errors away is your sample mean → critical values mark the rare region → if your test statistic lands there, reject H₀.
- For proportions: binomial distribution → normal approximation (with conditions) → test statistic in units of standard errors → same decision logic.

### Named trade-offs
- α small (0.01) makes false rejection rare but Type II error large (miss real effects). α large (0.10) makes false rejection more common but Type II error smaller (easier to detect effects).
- Pre-registration commits you to one test, so p-value is meaningful. Without pre-registration, you've implicitly run many tests; the p-value alone can't account for that.
- Sample size: larger → narrower confidence interval, more power to detect effects, but more expensive and time-consuming.

### Counterintuitive points
- A larger sample doesn't make you more likely to reject a true null; it makes you more likely to find data very close to the true parameter (if the null is true) or far from it (if the null is false).
- A p-value of 0.049 vs. 0.0001 are both < 0.05, but they're very different. The first is "barely significant"; the second is "wildly unlikely under the null."
- "Statistically significant" and "practically significant" are different. A coin might come up heads 501 times in 1000 flips (p < 0.05 with huge sample), but that's not a practically significant bias.

### Scale shifts (narrative payoff)
- One test on one drug trial in one lab. → Thousands of tests run in academic papers each year worldwide. → Most of those effects can't be replicated. → Realization: p-hacking and multiple comparisons are real. → New standards: pre-registration, correction for multiple comparisons, replication. (This is the story of the replication crisis.)

### Common misconceptions to name and correct
1. P-value = probability the null is true.
2. A p-value of 0.05 means there's a 5% chance you made an error.
3. "Accepting the null" (you don't; you fail to reject).
4. Large sample → easier to reject null. (No; large sample → more power to detect real effects AND more likely to show true null is true.)
5. The test proves your hypothesis is true. (No; it shows the data are consistent or inconsistent with the null.)

### Worked example scaffolding
1. **Jeffrey's goggles:** One-sample z-test for mean (σ known). Left-tailed test. Compute z, find p-value, interpret. Real scenario, high school context, easy numbers.
2. **Salesperson (Jasmine) meets standard:** One-sample t-test for mean (σ unknown, n < 30). One-tailed test. Compare to critical value. Workplace context.
3. **Filling machine malfunction:** One-sample z-test for mean (σ unknown, n > 30). Two-tailed test. Show why such a tiny difference (7.91 vs. 8 ounces) is statistically significant (3 standard deviations away). Manufacturing context, high stakes (shutting down production).
4. **Bank lending proportions:** One-sample z-test for proportion. Two-tailed test. Check conditions (np, nq > 5). Interpret non-significant result (proportions are close enough to 50% that we can't rule out the bank's claim).

---

## Gaps and adjacent ideas in the source

**Gaps:**
- No discussion of effect size or the distinction between statistical and practical significance (though the chapter hints at this).
- No coverage of confidence intervals for the difference between two population means or proportions (that's Chapter 10).
- No Bayesian perspective (treated as out of scope for the book).

**Adjacent ideas worth mentioning:**
- Sample size calculation: "How big a sample do I need to have adequate power?" (Mentioned but not fully worked.)
- Nonparametric alternatives: When the normal/t assumption fails, what do you do? (Out of scope but worth knowing exists.)
- Multiple comparisons correction: Bonferroni, FDR. (Mentioned in the integration section; worth more depth in a sequel.)

---

## Conversion notes (source to chapter)

- **Module 1** (introduction on scientific method) became the cold open (FDA committee) and the "Why this chapter matters" section. The emphasis on hypothesis-first (not data-first) reasoning is preserved.
- **Module 2** (null and alternative hypotheses) became Concept 1, with the addition of the court trial analogy (not in OpenStax) to ground the asymmetry of the logic.
- **Module 3** (Type I and Type II errors) remained Concept 1, merged with hypotheses because they're inseparable. The sleeping bag example is from OpenStax.
- **Module 4** (test statistics, critical values, p-values) became Concept 2, with the addition of the manufacturing analogy (not in OpenStax) to motivate the need to measure in standard deviations.
- **Module 5** (worked examples, one-sample tests for means and proportions) became Concept 3. Examples are simplified versions of OpenStax's worked problems, with more narrative framing.
- **Integration section** is new, addressing the replication crisis and p-hacking. This reflects recent developments (2010s onward) in statistics and research methodology, not covered in the 2014 OpenStax source.

The chapter is approximately 6,800 words, exceeding the 5,000–8,000 target slightly to accommodate the depth required by a notoriously difficult topic. The voice prioritizes clarity and narrative grounding over brevity.

