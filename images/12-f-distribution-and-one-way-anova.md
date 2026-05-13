# Images and Figures: Chapter 12 — F-Distribution and One-Way ANOVA

Reference for figure descriptions. Figures are embedded in the chapter or referenced for external sources.

---

## Suggested Figures (for illustration)

### Figure 1: The F-Distribution at Different Degrees of Freedom

**Description:** Three overlaid F-distribution curves showing how shape changes with degrees of freedom.
- Curve 1: $F_{2,5}$ (low df; highly right-skewed, peaked)
- Curve 2: $F_{5,20}$ (medium df; moderate skew)
- Curve 3: $F_{20,100}$ (high df; approaching normal but still slightly right-skewed)

**Purpose:** Illustrate that F curves are always right-skewed and become more symmetric as df increase.

**Source:** Standard statistics textbook figures; can be generated via R, Python, Excel.

---

### Figure 2: ANOVA Interpretation—Hypothesis Visualization

**Description:** Three side-by-side boxplot panels.

**Panel A (null hypothesis true):** Three groups with overlapping distributions, similar means and spreads. All distributions roughly centered.

**Panel B (alternative hypothesis true, moderate effect):** Three groups with clearly separated means but overlapping ranges. Between-group variation apparent.

**Panel C (alternative hypothesis true, large effect):** Three groups with well-separated means and little overlap. Between-group variation dominates.

**Purpose:** Visualize what the null and alternative hypotheses represent in terms of observable group distributions.

---

### Figure 3: Partitioning Variation in ANOVA

**Description:** A single-axis number line or bar diagram showing the composition of total variation.

- Total variation (full bar) = Between-group variation (colored segment) + Within-group variation (colored segment).
- Under $H_0$, within-group dominates.
- Under $H_a$ (groups truly different), between-group is substantial.

**Purpose:** Make the partition tangible and show why $F = \frac{\text{Between}}{\text{Within}}$ is large when groups differ.

---

### Figure 4: F-Distribution with Critical Value and p-value Region

**Description:** A single F-curve (e.g., $F_{3,16}$) with shaded right tail.

- Vertical line at observed test statistic $F = 4.2$.
- Shaded region to the right of the line (p-value region).
- Vertical dashed line at critical value (e.g., $F_{0.05, 3, 16} = 3.24$).

**Purpose:** Show that we reject when F is large (right tail) and illustrate the relationship between critical value and p-value.

---

### Figure 5: Grading Variance Example—Histograms

**Description:** Two side-by-side histograms of grades.
- Left: Instructor 1's grades (more concentrated around mean, lower variance).
- Right: Instructor 2's grades (more spread out, higher variance).

**Purpose:** Illustrate the idea of comparing variances visually; show why variance matters in contexts like grading consistency.

---

### Figure 6: Rothamsted Wheat Field (Cold Open Context)

**Description:** Historical photograph or illustration of Rothamsted Experimental Station, circa 1920s.

**Purpose:** Ground the cold open in historical context; show Fisher's real-world environment.

**Source:** Rothamsted Research historical archives (public domain).

---

## Data Visualizations Referenced in Chapter

### Worked Example 1: Grading Variance
No figure needed; small numeric example.

### Worked Example 2: Three Diet Plans
No figure needed; small numeric example.

### Worked Example 3: Three Teaching Methods (Pantry)
Could add: boxplot of test scores by method, showing overlapping distributions and supporting the conclusion of no significant difference.

---

## Notes on Interpretation Aids

### ANOVA Table Diagram
The chapter explains the ANOVA table structure verbally. A visual aid might show:
- Column headers and what each represents.
- Example values filled in.
- Arrows or highlights showing the F ratio calculation.

### Post-Hoc Testing Decision Tree
A flowchart (not in this chapter but useful context):
1. Run ANOVA.
2. If p-value < α, reject H₀.
3. If rejected, run post-hoc test (Tukey, Bonferroni, etc.).
4. If not rejected, stop; no post-hoc test needed.

---

## Data Sources for Examples

### Grading Variance Example
Hypothetical data created for pedagogical clarity.

### Diet Plans Example
Hypothetical data created for pedagogical clarity.

### Wheat Field / Rothamsted Context
Historical reference: Fisher's work at Rothamsted Experimental Station, 1920s. Details from:
- Fisher, R. A. (1925). *Statistical Methods for Research Workers*.
- Rothamsted Research historical records.

---

## Figure Production Notes

All figures in this chapter should:
- Use clear, high-contrast colors.
- Include axis labels with units where applicable.
- Include descriptive captions (in the chapter text).
- Be generated at sufficient resolution for both screen and print viewing.

Software recommendations:
- R (ggplot2): For distributions and boxplots.
- Python (matplotlib, seaborn): For distributions, boxplots, histograms.
- Excel or similar: For ANOVA tables and simple bar charts.
- Inkscape or similar: For conceptual diagrams (partitioning variation, decision trees).
