# Images — Chapter 2 (Descriptive Statistics)

Figure descriptions and generation notes for all diagrams in the chapter.

---

## Figure 1: Histogram Example

**Concept:** Concept 1 — Getting the shape  
**Context:** Introduction to histograms as a way to see where data cluster

**Description:**
A histogram with:
- Horizontal axis labeled "Continuous Variable (e.g., Salary in dollars)" with tick marks at intervals (e.g., $40K, $60K, $80K, $100K)
- Vertical axis labeled "Frequency (Count)" with tick marks 0, 5, 10, 15, 20, 25
- Six adjacent bars (touching, no gaps) with heights approximately 8, 14, 16, 9, 3, 2
- Title: "Histogram: Where data cluster"
- Annotation pointing to the tallest bar: "Peak here — most observations in this interval"
- Annotation pointing to right tail: "Fewer observations at high end"

**Data source:** Sociology students' social media use (from Concept 1 worked example)  
**Purpose:** Teach students to read and interpret histogram height as frequency.

---

## Figure 2: Three Distribution Shapes

**Concept:** Concept 3 — Measuring spread (and Concept 1)  
**Context:** Relating distribution shape to the relationship between mean, median, and mode

**Description:**
Three side-by-side histograms:

**Left panel: Symmetrical distribution**
- Bell-shaped, centered
- Mean, median, and mode all at the center
- Annotations: "Mean = Median = Mode"
- Labels: "Symmetrical"

**Center panel: Right-skewed (positive skew)**
- Taller bars on left side, long tail extending right
- Vertical lines showing positions of Mode < Median < Mean (from left to right)
- Annotations: "Mean pulled right by high values"
- Labels: "Right-skewed (Positive skew)"

**Right panel: Left-skewed (negative skew)**
- Taller bars on right side, long tail extending left
- Vertical lines showing positions of Mean < Median < Mode (from left to right)
- Annotations: "Mean pulled left by low values"
- Labels: "Left-skewed (Negative skew)"

**Purpose:** Visually anchor the relationship between skewness and the relative positions of center measures.

---

## Figure 3: Box Plot Anatomy

**Concept:** Concept 1 — Box plots and the five-number summary  
**Context:** Detailed explanation of what each component represents

**Description:**
A single box plot (horizontal orientation, as in a summary display) with:

- A horizontal axis labeled "Variable (e.g., Age, Salary)" with tick marks
- A box drawn from Q1 to Q3
- A vertical line inside the box at the median
- Whiskers (thin horizontal lines) extending from the box to the minimum and maximum (or to the outlier boundaries if outliers exist)
- Individual points plotted beyond the upper whisker representing outliers

**Annotations:**
- Curved bracket from axis to left whisker: "Minimum"
- Curved bracket from left whisker to box edge: "Q1 (25th percentile)"
- Vertical line inside box: "Median (Q2, 50th percentile)"
- Curved bracket from right box edge to right whisker: "Q3 (75th percentile)"
- Arrow to individual points beyond whisker: "Suspected outliers (beyond 1.5×IQR)"
- Vertical bracket inside box: "IQR = Q3 − Q1"

**Purpose:** Teach students to read all five-number summary information from a single visual.

---

## Figure 4: Histogram with Interval Details

**Concept:** Concept 1 — Constructing a histogram  
**Context:** Worked example (ER patient ages)

**Description:**
A histogram showing the frequency distribution of patient ages (from the ER worked example in Concept 2):
- X-axis: Age (years), intervals 0–10, 10–20, 20–30, 30–40, 40–50
- Y-axis: Frequency (count), 0 to 10
- Bars showing frequencies: 2, 8, 15, 12, 3
- Tallest bar at 20–30 age range
- Title: "ER Patient Ages (One Week, N=40)"
- Annotation: "Most patients between 10–35 years old"

**Purpose:** Show students a real histogram shape and where to read frequency information.

---

## Figure 5: Comparing Two Datasets with Identical Means

**Concept:** Concept 3 — Measures of spread  
**Context:** Why SD matters even when means are the same

**Description:**
Two histograms side by side:

**Left histogram (Supermarket A):**
- X-axis: Wait time (minutes), 0 to 12
- Narrow, concentrated distribution centered at 5 minutes
- Bars: most frequencies between 3–7 minutes
- Title: "Supermarket A: Mean = 5 min, SD = 2 min"
- Annotation: "Predictable wait times"

**Right histogram (Supermarket B):**
- X-axis: Wait time (minutes), 0 to 12
- Wide, spread-out distribution centered at 5 minutes
- Bars: frequencies spread across 1–9 minutes
- Title: "Supermarket B: Mean = 5 min, SD = 4 min"
- Annotation: "Unpredictable wait times"

**Purpose:** Visually demonstrate that standard deviation captures spread, not just center.

---

## Figure 6: Standard Deviation as Distance from Mean

**Concept:** Concept 3 — Understanding standard deviation  
**Context:** Interpreting what "average distance" means

**Description:**
A number line with:
- A vertical axis at the center labeled "Mean = 6"
- Tick marks showing distances: ±1 SD, ±2 SD, ±3 SD from the mean
- Labels: "6 ± 3.16" at ±1 SD, "6 ± 6.32" at ±2 SD, etc. (if SD = 3.16)
- Data points (dots) scattered along the line, most falling within ±1 SD
- Annotations: "1 SD", "2 SD", "3 SD" with distance labels

**Purpose:** Make standard deviation concrete—it measures distance from the mean, and the SD value tells you how spread out typical observations are.

---

## Figure 7: Outlier Detection with IQR

**Concept:** Concept 3 — Identifying outliers  
**Context:** Applying the 1.5 × IQR rule

**Description:**
A visual showing:
- A number line representing a dataset
- A box from Q1 to Q3 (the IQR, shown as a thick interval)
- The median (Q2) marked inside the box
- Whiskers extending 1.5 × IQR below Q1 and above Q3 (shown as thin lines)
- The region between the whiskers labeled "Normal range"
- Individual data points plotted on the line, some within the whiskers, some beyond
- Points beyond the whiskers labeled with arrows: "Suspected outliers"

**Purpose:** Show students how the outlier boundaries are calculated geometrically.

---

## Figure 8: Percentiles on a Distribution

**Concept:** Concept 3 — Percentiles and quartiles  
**Context:** Locating a value within the ordered dataset

**Description:**
A histogram with cumulative frequency information overlaid:
- The histogram shows frequency distribution (bars)
- Vertical lines drawn at the 25th, 50th, and 75th percentiles
- Shading or coloring for regions: bottom 25%, next 25%, next 25%, top 25%
- Labels: "Q1 (25th %ile)", "Median (50th %ile)", "Q3 (75th %ile)"
- Example: if the variable is test score, mark where 25% of students scored below, 50% scored below, etc.

**Purpose:** Help students visualize that percentiles divide the dataset into equal-area regions (not equal-value regions).

---

## Figure 9: Stem-and-Leaf Plot Example

**Concept:** Concept 1 — Stem-and-leaf plots  
**Context:** Alternative visualization for small datasets

**Description:**
A stem-and-leaf plot showing test scores (from Concept 1 worked example):

```
Stem | Leaf
-----|----
  4  | 9
  5  | 3 5 5
  6  | 1 3 7 8 8 9 9
  7  | 2 3 4 8
  8  | 0 3 8 8 8
```

**With annotations:**
- Arrow pointing to stem 6, noting "This line represents scores 61–69"
- Arrow to a leaf 9 in stem 6, noting "69 is one score; 68 appears twice"
- Overall annotation: "20 test scores ordered from smallest (49) to largest (88)"

**Purpose:** Teach students to read stem-and-leaf plots and see how they preserve individual data values while showing distribution shape.

---

## Figure 10: Mean vs. Median with Outlier

**Concept:** Concept 2 — Choosing center measures  
**Context:** Why the median is more robust when outliers exist

**Description:**
Two number lines, one below the other:

**Top line: Without outlier**
- Data: $30K, $30K, $30K, $32K, $35K (typical town salaries)
- Mean marked at approximately $31.4K
- Median marked at exactly $30K
- Annotation: "Mean and median are close"

**Bottom line: With outlier**
- Data: $30K, $30K, $30K, $32K, $5,000K (one billionaire)
- Mean marked at $1,018.4K (pulled far right)
- Median marked at $30K (unchanged)
- Annotation: "Mean pulled by outlier; median unaffected"

**Purpose:** Viscerally show students why median is more representative when extreme values exist.

---

## Figure 11: Five-Number Summary and Box Plot Together

**Concept:** Integration section  
**Context:** Connecting five-number summary table to box plot visualization

**Description:**
Two panels:

**Left panel:**
A table showing:
| Statistic | Value |
|---|---|
| Minimum | −15.3% |
| Q1 | 2.8% |
| Median | 6.5% |
| Q3 | 10.5% |
| Maximum | 28.4% |
| IQR | 7.7% |

**Right panel:**
The corresponding box plot drawn on a horizontal axis showing returns (−20% to +30%), with the box, whiskers, and one outlier (28.4%) visible.

**Connecting lines or arrows** from each table row to the corresponding part of the box plot.

**Purpose:** Show students how a data table translates into a visual summary; strengthen fluency moving between representations.

---

## Generation notes

All figures should be:
- Drawn with clear, high-contrast colors (dark text on light background, or white on dark for emphasis)
- Labeled with descriptive titles and axis labels
- Annotated with arrows, brackets, or callout text to highlight key features
- Accessible: use patterns (hatch, dots) in addition to color to distinguish groups
- Sized for readability at 1-column width (~450px) and 2-column width (~700px)

Suggested tools:
- Histograms, box plots, distributions: matplotlib (Python), ggplot2 (R), or Desmos for interactive versions
- Annotated diagrams: Inkscape, Adobe Illustrator, or Figma for vector graphics
- Number lines: TikZ (LaTeX) or simple SVG

All figures should be embedded in the chapter markdown as [FIGURE: ...] tags (to be rendered during book production).
