# Bookmap: Chapter 11 — The Chi-Square Distribution

## Source and context

This chapter converts the OpenStax *Introductory Statistics* module on chi-square distribution (modules m55691–m55700 in the OpenStax collection) into the Attenborough × Feynman v1.1 voice. The source is clinical, comprehensive, and exercise-heavy; the conversion emphasizes intuition, mechanism, and the honest limits of the test.

---

## What the OpenStax modules actually teach

The source material covers:
1. **Introduction and uses of chi-square** (m55691): Motivates three applications—goodness-of-fit, independence, single variance—without much machinery.
2. **Chi-square distribution itself** (m55693): Properties, notation, mean, standard deviation, shape, degrees of freedom, normal approximation for large df.
3. **Test of single variance** (m55694): Using chi-square to test whether a population variance matches a hypothesized value. Uses formula $\chi_c^2 = \frac{(n-1)s^2}{\sigma_0^2}$. Worked examples with donuts, post office, broadband speeds.
4. **Goodness-of-fit test** (m55696): The core formula $\sum \frac{(O-E)^2}{E}$. Worked examples with college absences, dice, streaming services, coin flips, literacy rates. Heavy on the mechanics, light on interpretation.
5. **Test of independence** (m55697): Contingency tables, expected frequency formula $E = \frac{\text{row} \times \text{col}}{\text{total}}$, degrees of freedom $(r-1)(c-1)$. Worked examples with volunteers, railroads, smoking/ethnicity, jobs over time, anxiety/achievement.

---

## What was selected for the chapter

This chapter focuses on **three concepts** (not four):
1. **Chi-square distribution** (where it comes from, shape, degrees of freedom)
2. **Goodness-of-fit test** (the core procedure and worked example)
3. **Test of independence** (using contingency tables)

**Deliberately deferred:** The test of single variance. It's important in quality control and manufacturing, but less central to the undergraduate inference curriculum and could obscure the main chi-square ideas. It's mentioned in the prerequisites/connections but not developed here. This keeps the chapter to ~6,500 words and focuses on counts, which is chi-square's natural domain.

---

## Ideas harvest

### Structural moves from OpenStax

- **Cold open with a concrete problem** (the source material does this, but weakly—just says "you could answer questions about lottery numbers"). The conversion grounds it in Mendel's garden, a specific historical moment with actual data (750 vs. 882 yellow peas). This makes the puzzle personal before any machinery appears.

- **Three applications all using the same statistic** (goodness-of-fit, independence, variance). The source material presents these as separate sections. The conversion unifies them around the core idea: $(O - E)^2 / E$, summed. This is a compression that clarifies.

- **Degrees of freedom explained intuitively** (the source material states the formulas but doesn't explain why: $k - 1$ for goodness-of-fit, $(r-1)(c-1)$ for independence). The conversion explains: "Once you fix the row and column totals, the remaining cells are determined." This connects to constraint.

- **Right-tailed always** (the source material mentions this but doesn't emphasize it). The conversion makes it a key property: chi-square is a sum of *squared* deviations, so it's never negative, and large values signal mismatch.

### Scale shifts worth emphasizing

- **From one test to meta-analysis**: The source doesn't explicitly discuss how individual chi-square tests combine across studies. The conversion includes a "scale shift" idea: when you aggregate chi-squares from independent studies, the test statistics and degrees of freedom add. This shows replication at work and is pedagogically powerful for upper-level students.

- **From table to numbers to story**: The source provides many worked examples but often leaves the interpretation thin ("reject the null, therefore..."). The conversion emphasizes what each result means in context. A significant test of independence means association, not causation. This is the hard part students miss.

### Pitfalls the source gets right

- **Expected counts ≥ 5 is non-negotiable** (source is emphatic; conversion preserves this).
- **The test measures association, not causation** (source hints; conversion makes it explicit and central).
- **Combining categories when needed** (source explains; conversion includes a visual in the images guide).

### What the source misses (added in conversion)

1. **Etymology of "chi-square"** (where the Greek letter and the notation come from). This isn't pedantic—it helps students remember which letter goes with which distribution.

2. **Intuition for mean and standard deviation of chi-square** ($\mu = df$, $\sigma = \sqrt{2 \cdot df}$). The source states these facts. The conversion shows why they matter: "If your test statistic is 22 and df is 20, you're not far above the mean. You might not reject. If it's 50, you're well into the tail."

3. **Explicit naming of what a significant test does and doesn't show** (source is scattered; conversion collects this into the integration section and conclusion).

4. **The red flag on small expected counts as a statement about test validity, not just procedure** (source says "combine categories"; conversion explains that the test breaks down mathematically when counts are too sparse, and why).

---

## Decisions made in the conversion

### Three concepts, not four

The source material has four major topics (goodness-of-fit, independence, variance, and the distribution itself). Keeping all four would expand the chapter to 8,000+ words and dilute focus. The variance test is deferred because:

- Goodness-of-fit and independence both work with counts in categories. Variance tests work with measurements of spread. They're different enough to deserve separate treatment.
- The variance test is less common in introductory curricula than goodness-of-fit and independence.
- The machinery is similar enough that a student who understands goodness-of-fit can pick up variance tests in a specialized course or Chapter 12 (ANOVA).

### Mendel over dice

The source uses a lottery example to open. The conversion uses Mendel. Why?

- Mendel is a story: a monk in a garden with a theory being tested against data. Students remember stories.
- The numbers are real: he got 882 yellow, expected 750. That specific mismatch is more graspable than "lottery numbers."
- The genetic context connects to biology students (a significant audience), increasing relevance.
- Mendel's work is historically cited as the origin of statistical thinking in biology. It's the honest, earned example.

### "Cold open at each concept" (Attenborough style)

The source material jumps into definitions. The conversion opens each of the three main concepts with a brief scene or question:

- Concept 1: "Chi-square is what?" → "A sum of squared deviations. Why squared? Why summed?"
- Concept 2: "Goodness-of-fit tests what?" → "Are the days equally absent?" (a concrete survey)
- Concept 3: "Independence means what?" → "Do older and younger viewers like different movies?"

Each cold open is short (2–3 sentences), but it poses the question before the machinery. This is Feynman's move: show the puzzle before showing the solution.

### "What would change my mind" + "Still puzzling"

The source material doesn't include author reflection. The conversion adds two reflection sentences at the end:

- **"What would change my mind"**: Acknowledges that the minimum expected-count rule (≥ 5) is conventional, not absolute, and would be revised if evidence suggested otherwise. This teaches students to hold even procedural rules loosely, pending evidence.

- **"Still puzzling"**: Names the ambiguity in the literature (some texts use minimum 3, some 5, some 10) and acknowledges that this deserves a careful simulation study to resolve. This teaches intellectual humility: "This field hasn't fully settled this question, and that's okay."

---

## What the source excels at that we preserved

1. **Multiple worked examples** (one for each major test type, plus variations). Each example shows the full procedure from hypotheses through conclusion.

2. **Explicit formula for expected frequencies in contingency tables** ($E = \frac{\text{row} \times \text{col}}{\text{total}}$). This is the hardest step for students, and the source states it clearly. Preserved.

3. **Distinction between $\chi^2$ and $\chi_c^2$ notation** (some texts use the subscript $c$ to denote "calculated"; most don't). The conversion uses just $\chi^2$ for clarity, but acknowledges this variation in the pantry.

4. **Comprehensive exercises** (the source includes 50+, ranging from fill-in-the-blank to synthesis). The conversion includes 10 representative exercises spanning the same range, enough to provide practice without overwhelming.

---

## Areas where the source is weaker (addressed in conversion)

1. **Interpretation over calculation** (source is heavy on "here's the formula, here's the table, here's the answer"; light on "what does this answer mean about the real world?"). Conversion flips the emphasis: the machinery comes after the question.

2. **Contingency table theory** (source assumes students understand conditional probability and independence; doesn't rederive). Conversion supplies a brief recap: "Independence means $P(A \text{ and } B) = P(A) \times P(B)$. In a table, the proportions are the same in every row."

3. **Causation** (source mentions it once, in passing; doesn't develop). Conversion makes it a central caution under Concept 3 and in the chapter summary. A student who reads this chapter will not confuse association with causation.

4. **Notation** (source uses $\chi^2$, $\chi_c^2$, sometimes switches between them; sometimes uses $X^2$). Conversion standardizes on $\chi^2$ and explains the notation once, up front.

---

## Connections to prior and future chapters

**Prior chapters feeding in:**
- Chapter 9 (hypothesis testing, one sample): the four-step procedure (hypotheses, statistic, critical value/p-value, decision).
- Chapter 2 (descriptive statistics, contingency tables): how to read a two-way table.
- Chapter 7 (probability): the multiplication rule ($P(A \text{ and } B) = P(A) \times P(B)$ under independence).

**Future chapters building on this:**
- Chapter 12 (ANOVA): another test comparing observed to expected, but for continuous data and multiple groups.
- Chapter 13 (regression): measuring association between two continuous variables (chi-square measures it for categorical).

---

## Pedagogical bets

1. **Intuition before formula.** The chapter shows why chi-square is a sum of squared, standardized deviations *before* asking students to calculate one. The machinery is clearer once the purpose is clear.

2. **One worked example per major procedure.** Rather than ten variations of "here's a goodness-of-fit test" at increasing difficulty, the chapter provides one clear example with explanation, then trusts exercises to extend.

3. **Honest caution over false precision.** The chapter admits that the expected-count rule is conventional, not absolute; that the threshold varies in the literature; and that chi-square doesn't prove causation. This is more useful than pretending the field has settled on all answers.

4. **Etymology and notation teaching memory.** By explaining that chi-square is named for the Greek letter $\chi$ (which looks like a squared variable), and that the squared deviations are the core idea, the chapter helps students anchor the concept to something memorable.

---
