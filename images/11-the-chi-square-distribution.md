# Images and Figures: Chapter 11 — The Chi-Square Distribution

This file catalogs the figures needed for Chapter 11. Use this checklist when finalizing the chapter for publication.

---

## Core figures (essential)

### Figure 1: The chi-square distribution curves (multiple df)

**Location in chapter:** Concept 1, "The shape of chi-square" section.

**Content:** Three overlaid chi-square curves showing $df = 1, 5, 10$.

**Key features:**
- Horizontal axis: $\chi^2$ values, from 0 to about 25.
- Vertical axis: probability density.
- $df = 1$: heavily skewed right, bunched near 0, long tail.
- $df = 5$: more spread, still right-skewed, peak around 3–4.
- $df = 10$: approaching symmetry, peak around 8–10.
- All curves shown in different colors or line styles for distinction.
- Labels for each curve showing the df value.

**Pedagogical notes:** Students should see that as df increases, the shape changes from heavily skewed to nearly symmetric. This teaches the fundamental insight that chi-square is a family of distributions, not a single curve.

---

### Figure 2: Chi-square curve with shaded rejection region (goodness-of-fit example)

**Location in chapter:** Concept 2, "Worked example — Are the days equally absent?" section.

**Content:** A single chi-square curve ($df = 4$) with the critical value marked and the rejection region shaded.

**Key features:**
- Horizontal axis: $\chi^2$ values, 0 to about 20.
- Vertical axis: probability density.
- Curve for $df = 4$ (mean = 4, not at the peak due to skewness).
- Vertical line at $\chi^2 = 9.488$ (critical value for $\alpha = 0.05$).
- Shaded (red/darker) region to the right of the line, labeled "Reject $H_0$" or "Rejection region."
- Unshaded region to the left, labeled "Fail to reject $H_0$."
- Mark the observed test statistic ($\chi^2 = 3.00$) on the curve with a dot or arrow, showing it's in the non-rejection region.

**Pedagogical notes:** This figure anchors the worked example. Students see where the rejection region lives (always the right tail, never the left) and where their calculated statistic falls.

---

### Figure 3: Contingency table with observed and expected frequencies side by side

**Location in chapter:** Concept 3, "A worked example — Movie preference by age" section.

**Content:** Two 3×3 tables, one labeled "Observed" and one labeled "Expected."

**Observed table:**
| Age | Action | Comedy | Drama | Row total |
|---|---|---|---|---|
| 18–30 | 40 | 50 | 35 | 125 |
| 31–50 | 45 | 60 | 70 | 175 |
| 50+ | 30 | 40 | 30 | 100 |
| Col total | 115 | 150 | 135 | 400 |

**Expected table:**
| Age | Action | Comedy | Drama |
|---|---|---|---|
| 18–30 | 35.94 | 46.88 | 42.19 |
| 31–50 | 50.31 | 65.63 | 59.06 |
| 50+ | 28.75 | 37.50 | 33.75 |

**Key features:**
- Tables side by side or one above the other, clearly labeled.
- Observed counts are whole numbers.
- Expected counts are decimals (to two places).
- Cell values in both tables use the same font/layout for easy comparison.
- Optional: color gradient showing which cells deviate most from expectation (darker = larger deviation).

**Pedagogical notes:** Seeing observed and expected side by side helps students internalize that the test measures mismatch. The visual comparison is more powerful than the numbers alone.

---

## Supporting figures (helpful but not essential)

### Figure 4: How expected frequencies are calculated (diagram)

**Location in chapter:** Concept 3, explaining the formula $E = \frac{\text{row} \times \text{col}}{\text{total}}$.

**Content:** A small 2×2 contingency table with:
- Row totals labeled (e.g., 100, 200).
- Column totals labeled (e.g., 150, 150).
- Grand total labeled (e.g., 300).
- One cell highlighted, with an arrow and the calculation shown: $E = \frac{100 \times 150}{300} = 50$.
- Annotation: "The expected cell frequency is the proportion of the row times the proportion of the column."

**Pedagogical notes:** A visual step-by-step makes the formula less abstract. Students who struggle with the algebra benefit from seeing the logic pictorially.

---

### Figure 5: Example of combining categories to meet the expected count rule

**Location in chapter:** Concept 2 or 3, in the discussion of assumptions.

**Content:** Two tables:

**Before (original categories):**
| Category | A | B | C | D | E |
|---|---|---|---|---|---|
| Observed | 12 | 8 | 5 | 3 | 2 |
| Expected | 10 | 10 | 10 | 10 | 10 |

With a note: "Category D and E have expected < 5. Cannot use this directly."

**After (combined):**
| Category | A | B | C | D+E |
|---|---|---|---|---|
| Observed | 12 | 8 | 5 | 5 |
| Expected | 10 | 10 | 10 | 20 |

With a note: "Combined D and E. Now all expected ≥ 5. This is allowed."

**Pedagogical notes:** This concrete example shows that combining is an acceptable and necessary response to sparse cells. It prevents students from proceeding with invalid tests.

---

### Figure 6: Mendel's pea garden (cold open visual)

**Location in chapter:** Cold open section at the beginning.

**Content:** A historical or schematic illustration of Mendel's garden or pea plants, with annotations showing:
- Two plants being crossed.
- Pollen traveling from one flower to another.
- Offspring generations with colors labeled (yellow, green).
- Numbers: "Expected 3:1 ratio" and "Observed 882:118 out of 1000."

**Pedagogical notes:** A visual that grounds the abstract problem in history and biology. Students see that Mendel's question—are these counts what I expected?—is the same question chi-square answers today.

---

## Data visualization (less critical, optional enhancements)

### Stacked bar chart comparing observed to expected (goodness-of-fit)

For the "Are the days equally absent?" example, a stacked or grouped bar chart showing:
- Each day (Monday–Friday) on the x-axis.
- Two bars per day: one for observed (e.g., height 15 for Monday), one for expected (height 12).
- Colors distinguish observed from expected.
- Y-axis: frequency.

This makes the mismatch visual and memorable.

---

### Heatmap for contingency table

For the movie preference example, a heatmap where:
- Rows: age groups.
- Columns: genres.
- Cell color intensity: the size of the cell count (darker = higher count).
- Labels: the actual counts.

Heatmaps make large tables easier to scan for patterns.

---

## Figure checklist

For publication, ensure:

- [ ] **Figure 1 (chi-square curves):** Three curves, clearly labeled by df. Legend or annotations identifying each.
- [ ] **Figure 2 (goodness-of-fit curve with rejection region):** Shaded right tail, critical value marked, test statistic marked, df labeled.
- [ ] **Figure 3 (observed vs. expected tables):** Two tables, side by side or stacked, clear labels, matching cell layouts.
- [ ] **Figure 4 (expected frequency calculation):** Diagram or small table showing the formula applied to one cell.
- [ ] **Figure 5 (combining categories):** Before/after tables showing that combining small-count categories is valid.
- [ ] **Figure 6 (Mendel's garden):** Illustration or schematic linking the cold open to a real historical question.

---

## Accessibility notes

- Use high-contrast colors (avoid red-green combinations that colorblind readers struggle with).
- Provide alt text for all figures describing the key data and pattern (e.g., "Chi-square curve with df=4, showing rejection region (shaded, right of vertical line at x=9.488) and observed test statistic at x=3.00, which falls in the non-rejection region").
- Provide data tables for all figures so readers using screen readers or text-to-speech can access the information.
- Avoid using color alone to convey information; supplement with patterns, labels, or line styles.

---
