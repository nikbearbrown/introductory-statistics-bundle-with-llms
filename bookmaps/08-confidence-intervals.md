# Bookmap: Chapter 8 (Confidence Intervals) — Source Analysis

This bookmap analyzes the five OpenStax source modules and extracts structural patterns, examples, and pedagogical moves for the rewritten chapter.

---

## Module 1 (m55460): Introduction to confidence intervals

**What it teaches:** The foundational concept that a point estimate is insufficient; a confidence interval acknowledges uncertainty and provides a range. Introduces the Apple Music example (mean number of downloads per month) and sketches the logic: if the sample mean is within 0.2 of the true mean 95% of the time, then the true mean is within 0.2 of the sample mean 95% of the time. Uses the empirical rule (68-95-99.7) as the intuitive foundation before moving to exact z-values.

**Structural moves:**
1. Contrast a point estimate (single number) with a confidence interval (range).
2. Use a concrete business scenario (Apple Music user behavior) to ground the problem.
3. Invoke the Central Limit Theorem and the empirical rule to justify the approach.
4. Name the parts: confidence level, margin of error, point estimate.
5. Emphasize the critical misconception: the confidence is in the procedure, not the interval.

**Pedagogical strength:** The module carefully distinguishes between "the interval contains the true mean" (logically impossible once the interval is built) and "the procedure produces intervals that contain the true mean 95% of the time" (what 95% confidence actually means). This is the hardest conceptual barrier.

**Limitations in source:** The source material jumps quickly from intuition to formulas without building the machinery step by step. It uses the 68-95-99.7 rule as an approximation, then mentions the exact z-value (1.96 vs. 2), but doesn't explain why you'd bother with the exact value.

**How rewrite handles it:** The rewrite (Concept 1) opens with a polling scenario (more vivid than Apple Music), walks through the z-value logic from the Central Limit Theorem, derives the formula from first principles, and then dedicates a section to the critical misunderstanding with specific language ("There is no sense to say...").

---

## Module 2 (m55461): Confidence intervals for the mean, σ known; changing confidence and sample size

**What it teaches:** The complete mechanics of building a CI when the population standard deviation is known. Works through the formula $\bar{x} \pm z^* \sigma/\sqrt{n}$ step by step. Demonstrates how changing the confidence level widens the interval; how increasing sample size narrows it. Uses an exam-score example (mean 68, σ = 3, n = 36, find 90% and 95% CIs).

**Structural moves:**
1. Rearrange the z-formula to solve for the CI directly.
2. Introduce the notation $z_\alpha$ and explain that $\alpha$ is the probability the interval misses (so confidence level is $1 - \alpha$).
3. Show side-by-side examples with different confidence levels, comparing interval widths.
4. Derive the effect of changing sample size with a concrete example (compare n = 36, n = 100, n = 25).
5. Name the trade-off explicitly: "There is a trade off between the level of confidence and the width of the interval. Our desire is to have a narrow confidence interval... But we would also like to have a high level of confidence. This demonstrates that we cannot have both."

**Pedagogical strength:** The explicit statement of the trade-off is gold. The side-by-side numerical comparisons (90% vs. 95%, n = 36 vs. n = 100) make the effects tangible.

**Limitations in source:** The source assumes σ is known, which is rare in practice. It addresses this limitation briefly at the end ("In reality, we can set... sample standard deviation, *s*, as an estimate for σ...") but defers the full treatment to the next module.

**How rewrite handles it:** The rewrite (Concept 1) uses the σ-known case as the pedagogical entry point, then (Concept 2) immediately pivots to the unknown-σ case with the t-distribution, making clear why the detour was necessary. This structure respects the source's pedagogical order but doesn't pretend the σ-known case is practically important.

---

## Module 3 (m55462): Confidence intervals for the mean, σ unknown; the t-distribution

**What it teaches:** When σ is unknown and the sample is small, substituting $s$ into the z-formula produces intervals that are too narrow. The t-distribution, with its heavier tails, corrects this. Explains degrees of freedom (n - 1) and why. Shows how to use a t-table. Walks through the stock EPS example (n = 10, x̄ = 1.85, s = 0.395, find 99% CI, get 1.444 to 2.256).

**Structural moves:**
1. Open with Gossett's historical story: small experiments at Guinness; the normal approximation failed; he discovered the t-distribution.
2. Define the t-distribution by its degrees of freedom.
3. Explain degrees of freedom conceptually: n deviations from the sample mean, but their sum is zero by definition, so only n-1 are free to vary.
4. Show the property that t converges to z as df increases (at df = ∞, the t-values match z-values).
5. Demonstrate the t-table: find row (df), find column (confidence level or α), read the critical value.
6. Work through the EPS example completely.

**Pedagogical strength:** The historical anecdote (Gossett at Guinness) is memorable and motivates why the t-distribution exists. The degree-of-freedom explanation (n deviations summing to zero) is concrete. The table of t-values at various df, showing convergence to z, is excellent intuition-building.

**Limitations in source:** The source jumps to the t-formula without fully explaining why $s$ is random and why that randomness requires a new distribution. The derivation (t = z / sqrt(χ²/df)) is shown but not explained intuitively.

**How rewrite handles it:** The rewrite (Concept 2) leads with "Gossett's problem" as a cold open: small sample + unknown σ = falsely narrow intervals. It then explains that $s$ itself is random, which adds uncertainty. The heavier tails of the t-distribution are described as the "honest price of not knowing σ." The source's derivation (t as a ratio) is deferred to a "Still puzzling" note at the chapter's end, since the rewrite prioritizes intuition over proof.

---

## Module 4 (m55463): Confidence intervals for a proportion

**What it teaches:** The proportion case uses a binomial distribution (binary success/failure outcomes) approximated by the normal when np ≥ 5 and n(1-p) ≥ 5. The sample proportion p̂ = x/n serves as the point estimate. The CI formula is p̂ ± z* sqrt(p̂(1-p̂)/n). Uses polling and smartphone-ownership examples.

**Structural moves:**
1. Introduce the context: election polls, stock market interest proportions, household technology adoption.
2. Define the sample proportion (p̂, "p-hat") clearly.
3. Name the condition for normal approximation (np ≥ 5, n(1-p) ≥ 5).
4. Derive the formula by analogy to the mean case: point estimate ± z* × standard error.
5. Walk through the smartphone example: 421 own out of 500 surveyed, build 95% CI, get (0.810, 0.874).
6. Work another example showing how to find the confidence level when given the interval (reverse problem).

**Pedagogical strength:** The analogy to the mean case ("formulas are different but conceptually identical") helps students see the underlying unity. The condition check (np ≥ 5, n(1-p) ≥ 5) is stated clearly and practiced in examples.

**Limitations in source:** The source doesn't explain why you use p̂ in the standard error formula when you don't know p. It just says "The estimated proportions p′ and q′ are used because *p* and *q* are not known." A deeper treatment would explore the trade-off: using p̂ introduces bias, but it's the best we have. For large n, the bias is negligible.

**How rewrite handles it:** The rewrite (Concept 3) uses the proportion case as the third type of interval to illustrate the unified structure. It checks the condition explicitly in the worked example and names the subtle point: "We substitute $\hat{p}$ for the unknown $p$ in the standard deviation formula, because we don't know $p$." This acknowledges the substitution without getting bogged in bias theory.

---

## Module 5 (m56644): Not explicitly provided in the read, but source content likely includes sample-size formulas

**Inferred content:** This module likely covers how to compute sample size given a desired margin of error and confidence level. The formula $n = \frac{(z^*)^2 \sigma^2}{e^2}$ (for means) and $n = \frac{(z^*)^2 p(1-p)}{e^2}$ (for proportions) relate the four quantities. When p is unknown, use p = 0.5 as the conservative estimate.

**Structural moves:**
1. Motivate with a practical question: "How many people do I need to survey to achieve a margin of error of ±3%?"
2. Rearrange the margin-of-error formula to solve for n.
3. Explain the conservative choice p = 0.5 when p is unknown.
4. Demonstrate the relationship: halving the margin of error quadruples the sample size.
5. Show a table of sample sizes for various margins of error.

**Pedagogical strength:** The sample-size formula is eminently practical. The insight that "halving precision requires four times the effort" is a real-world constraint students should internalize.

**Limitations in inferred source:** Without seeing the full module, hard to critique, but a common gap is not explaining why (z*)² appears in the numerator (because you square when rearranging) rather than just z*.

**How rewrite handles it:** The rewrite (Integration section) includes a brief derivation of the sample-size formula and demonstrates the quadratic relationship between n and margin of error. It presents this in the context of a polling scenario: "How many people must they survey to achieve a margin of ±2.5%, at 95% confidence?"

---

## Cross-cutting ideas worth preserving

1. **The trade-off theme:** Confidence level vs. interval width; precision vs. sample size. The sources emphasize this repeatedly and the rewrite echoes it throughout.

2. **The analogical structure:** Mean CIs, then proportion CIs. Different formulas, same logic (point estimate ± z* × SE). The rewrite uses this explicitly.

3. **Worked examples with realistic scenarios:** Apple Music, exams, stocks, polling, smartphones, hiring decisions. These ground the math in recognizable contexts.

4. **The table-based critical values:** t-tables and z-tables are tools students must learn to use. The rewrite includes snippets of critical values but emphasizes the conceptual meaning (the z* or t value marks the boundary of the confidence region).

5. **The critical misconception about confidence:** Repeatedly named in the sources; the rewrite makes it a section of its own in Concept 1.

---

## Ideas NOT from source; added in rewrite

1. **Gossett's story as a cold open** (rather than as a historical aside): The rewrite makes the motivation vivid by opening Concept 2 with "Tuesday, 1908, Dublin..." and building to why the t-distribution was necessary.

2. **Etymology and gloss:** The rewrite defines *confidence interval*, *margin of error*, *standard error*, etc. with etymologies and clear contrasts. The sources define terms inline but don't linger on language.

3. **A "still puzzling" note on the t-distribution derivation:** The rewrite admits that the t = z/sqrt(χ²/df) construction makes mathematical sense but doesn't provide deep intuition about *why* that particular form captures the added uncertainty.

4. **The scale-shift interpretation:** In Integration, the rewrite describes repeating the study 100 times and observing that ~95 intervals contain the true parameter. This "procedure interpretation" is crucial to fighting the common misconception.

5. **Explicit focus on the three-way trade-off table:** Confidence level, margin of error, sample size. You can control two; the third follows from math. The rewrite foregrounds this as a design principle.

---

## Verdict on source materials

**Strengths:**
- Well-structured progression: point estimate → interval (σ known) → interval (σ unknown) → proportion → sample size.
- Abundant worked examples with realistic contexts.
- Explicit statement of the trade-offs and misconceptions.
- Clear, step-by-step derivations and table-reading instructions.

**Gaps addressed in rewrite:**
- The σ-known case, while pedagogically useful, is rare. The rewrite uses it as an entry point but quickly emphasizes the σ-unknown case (t-distribution) as the practical one.
- The historical motivation for the t-distribution is scattered; the rewrite brings Gossett's story to the foreground.
- The "confidence in the procedure" distinction is stated but not deeply explored in the source. The rewrite dedicates a full section and a scale-shift diagram.
- Sample-size formulas appear late and briefly in the source. The rewrite elevates them to the Integration section and gives them conceptual weight.
- Etymologies and precise definitions are minimal in the source. The rewrite adds a glossary and uses language pedagogically.

---

## Specific source passages re-used or paraphrased in rewrite

1. **Concept 1, "The critical misunderstanding"**: Paraphrases the source statement: "The 95% confidence interval implies two possibilities... The first possibility happens for 95% of well-chosen samples."

2. **Concept 2, "Gossett's story"**: Synthesizes the source's historical note about Gossett at Guinness; emphasizes the problem he faced (small samples, unknown σ) and the solution (t-distribution).

3. **Concept 2, "Why $n-1$"**: Borrows the source's explanation of degrees of freedom: "when you calculate a sample standard deviation, you compute $n$ deviations from the sample mean... so only $n-1$ are free to vary."

4. **Concept 3, "The condition for validity"**: Directly uses the source's condition: np ≥ 5 and n(1-p) ≥ 5.

5. **Worked examples**: The rewrite adapts the Apple Music (m55460), exam scores (m55461), EPS (m55462), and smartphone (m55463) examples from the sources, sometimes streamlining, sometimes elaborating.

---

## Notes for future revisors

If revising this chapter:

- Check whether student performance on the "confidence in the procedure" misconception improves with the rewrite's foregrounding and scale-shift interpretation. If not, consider adding interactive elements (e.g., a simulator showing 100 repeated CIs, with toggle to highlight which contain the true parameter).

- The t-distribution's heavy tails are justified as "the honest price of not knowing σ," but some students may want a deeper mechanism. Consider supplementing with a video or interactive that shows how different sample standard deviations produce different intervals, motivating why a single t-value (rather than a z-value) captures the variability.

- Sample-size calculations assume you can estimate p (for proportions) or σ (for means) before collecting data. In practice, this is hard. A section on "When you have no prior information" (use p = 0.5 for proportions; literature or small pilot study for σ) would deepen realism.

- The chapter treats z- and t-intervals for means separately, but a unified approach (t for all, with the understanding that t approaches z at large n) might reduce the cognitive load. This is a structural choice worth revisiting.

---

## Summary

The source modules provide a solid scaffold: clear progression, realistic examples, explicit trade-offs, and honest naming of misconceptions. The rewrite preserves all of these while:

- Reordering and reframing concepts for clarity (σ-known → σ-unknown → proportions → sample size).
- Leading with narrative (cold opens, Gossett's story) rather than abstraction.
- Foregrounding the "procedure interpretation" of confidence.
- Adding etymologies and precise definitions.
- Elevating sample-size formulas from appendix to integration.
- Admitting what remains puzzling (the t distribution's mechanical form) rather than pretending all questions are settled.

The result is a chapter that respects the source material while adopting the Attenborough × Feynman voice: scene-first, mechanism-clear, honest about limits, and written for someone figuring it out in real time.
