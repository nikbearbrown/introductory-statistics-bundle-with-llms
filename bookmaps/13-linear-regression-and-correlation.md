# Bookmap — Chapter 13 source analysis

Analysis of the eight OpenStax source modules (m55715, m55719, m55726, m55718, m55838, m64846, m56649, m55852) that were synthesized into the rewritten chapter.

---

## Module breakdown and inheritance

### m55715: Introduction — Models and causation

**What it teaches:** The foundational distinction between models as theories and models as fitted equations. The framing of *y* = *f*(*x*) as a causal statement, and the role of regression as a tool for testing whether data support a theoretical relationship.

**Teaching approach:** Deductive. Opens with philosophy (the scientific method, falsifiability) before introducing the machinery. Uses examples from economics and political science. Emphasizes that regression tests theory, not the reverse.

**What the chapter inherited:** The core principle that regression is tied to theory and hypothesis testing. The section "When correlation breaks down" in the chapter echoes this: regression describes the data you have, not the mechanism you theorize. The warning against causal claims without experiment.

**What the chapter omitted:** Extended discussion of model specification, multiple regression, and econometrics-level theory. OpenStax gives these 30+ paragraphs; the chapter defers them ("brief mention" of multiple regression).

---

### m55719: Bivariate data and the correlation coefficient

**What it teaches:** The shift from univariate (single-variable) to bivariate (two-variable) data. Visual and mathematical introduction to correlation. The formula for *r*, interpretation of its sign and magnitude, and the critical warning that correlation does NOT imply causation.

**Teaching approach:** Visual first (scatter plots), then formulas. Uses standardized terminology (linear, perfect correlation, etc.). Heavy emphasis on common misconceptions (size of *r*, linearity, causation).

**What the chapter inherited:** The structural approach: scatter plots precede the formula. The emphasis on sign (positive/negative) and magnitude. The cold-open scenario comparing students' scores. The repeated refrain "correlation does not imply causation."

**What the chapter modified:** The chapter fleshes out Galton's pea experiment (absent from the module) to motivate the term "regression to the mean." This gives historical context and emotional anchor that the module lacks.

---

### m55726: Testing whether correlation is significant

**What it teaches:** The hypothesis test for whether a sample correlation *r* is significantly different from zero in the population. The t-test statistic, degrees of freedom, and the shorthand approximation rule ($|r| \geq 2/\sqrt{n}$).

**Teaching approach:** Procedural. Follows the hypothesis test template: null hypothesis (*ρ* = 0), alternative (*ρ* ≠ 0), test statistic, decision rule.

**What the chapter inherited:** The principle that a correlation can be statistically significant (not due to chance) without being practically large. The reference to hypothesis tests as a decision-making tool, consistent with Chapters 9–12.

**What the chapter deferred:** Explicit calculation of the t-test for significance. The chapter mentions "significant correlation" in context but does not walk through the full test. This is appropriate for a chapter that aims to be conceptual rather than procedural.

---

### m55718: Linear equations — Slope and intercept

**What it teaches:** The algebraic form *y* = *a* + *bx*. The meaning of slope (rate of change) and intercept (value when *x* = 0). Worked examples from service pricing (hourly rate plus flat fee).

**Teaching approach:** Algebraic. Assumes comfort with coordinate planes and function notation. Uses concrete business examples (tax returns, hang-gliding lessons, tutoring fees).

**What the chapter inherited:** The language of slope and intercept. The practical interpretation of *b* (change in *y* per unit change in *x*) and *a* (baseline when *x* = 0). The section "Quick reference formulas" in the pantry recaps these.

**What the chapter extended:** This module treats linear equations as algebra; the chapter situates them in statistics, linking slope to correlation and showing how least-squares chooses the best line.

---

### m55838: Regression analysis — Least squares, residuals, and assumptions

**What it teaches:** The theoretical foundation of OLS regression. The least-squares criterion (minimize SSE). The assumptions of the regression model (normality of errors, constant variance, independence, etc.). The role of residuals in diagnosing fit.

**Teaching approach:** Mathematical and diagnostic. Explains the assumptions in detail. Shows residual plots as a tool for checking assumptions.

**What the chapter inherited:** The concept of residuals as unexplained parts of the data. The Sum of Squared Errors (SSE) as the quantity being minimized. The assumption checks via residual plots. The pantry's worked example showing residual calculations.

**What the chapter clarified:** This module is dense with assumptions and technical jargon. The chapter picks three essential ideas: residuals as vertical distances, SSE as the minimized quantity, and residual plots as diagnostic. It does not enumerate all five assumptions in detail (appropriate for an intro course).

---

### m64846: Elasticity and logarithmic transformation

**What it teaches:** Elasticity as a measure of percentage response to percentage change. Regression with log-transformed variables. The four cases of regression (unit-to-unit, unit-to-percent, percent-to-unit, percent-to-percent).

**Teaching approach:** Applied. Uses economics (demand, price sensitivity) and business (advertising response) examples. Shows how transformations change interpretation of coefficients.

**What the chapter inherited:** Implicitly, the principle that slope interpretation depends on units and transformations. The chapter does not cover logarithmic regression explicitly but references it in the "still puzzling" section (wish list for future expansion).

**What the chapter omitted:** Elasticity calculations, log transformations, and the four regression cases. These are advanced topics for a closing chapter. The chapter's scope is linear regression in levels (not logs).

---

### m56649: Prediction intervals and extrapolation

**What it teaches:** The distinction between confidence intervals (for the mean value of *y* at a given *x*) and prediction intervals (for an individual observation). Why prediction intervals are wider. The dangers of extrapolation.

**Teaching approach:** Mathematical (shows both formulas) and cautionary (emphasizes the risk of predicting outside the data range).

**What the chapter inherited:** The core warning: extrapolation is unreliable. The idea that predictions near the mean *x* are more certain than predictions far from it (reflected in Figure 7).

**What the chapter deferred:** The formulas for confidence and prediction intervals. These are important for inference but would lengthen an already-dense chapter. The chapter settles for conceptual understanding (prediction intervals are wider; extrapolation is risky).

---

### m55852: Using regression software (Excel)

**What it teaches:** Step-by-step instructions for running regression in Excel. How to interpret Excel's output (ANOVA table, coefficients, standard errors, p-values).

**Teaching approach:** Procedural. Screenshots and menu navigation. Focuses on applied use rather than conceptual understanding.

**What the chapter inherited:** Implicit acknowledgment that regression is a tool to be used via software, not by hand. The chapter's pantry section includes reference tables and quick formulas, positioning calculation as a reference aid rather than the learning goal.

**What the chapter omitted:** Software instructions. The chapter is tool-agnostic. It teaches the concepts; students can use Excel, R, Python, or any package that computes regression. This keeps the chapter platform-independent and timeless.

---

## Synthesis approach

The eight modules present regression as a suite of topics: causation and theory, correlation measurement, significance testing, algebraic foundations, statistical assumptions, applications (elasticity), prediction, and computation.

The rewritten chapter reorganizes around three concepts:

1. **Correlation:** co-movement and strength (*r*), interpreted visually and numerically.

2. **Regression:** the least-squares line, slope as scaled correlation, residuals as unexplained parts.

3. **Fit and limits:** $R^2$ as explained variance, residuals as diagnostics, and the boundary between association and causation.

This structure moves from description (scatter plots, *r*) to explanation (the line, slope, intercept) to diagnosis (residuals, $R^2$) to caution (causation, extrapolation). Each concept is motivated by a cold open and grounded in worked examples.

---

## Ideas harvest — Angles and moves for future development

### Puzzles and cold opens

- **Galton's pea experiment:** regression to the mean as historical and intuitive anchor. Used in chapter.
- **Exam scores:** simplest bivariate scenario (two test scores). Used in chapter.
- **Drug dose-response:** practical example showing why the fitted line matters. Used in chapter.
- **Wage-education scatter:** real-world stakes (earnings, inequality). Used in chapter.
- **Simpson's paradox:** not used; could open a future chapter on confounding and aggregation.
- **Baseball batting average vs. salary:** real athletes, familiar sport; alternative to abstract examples.

### Specification moves

- **Distinguish *r* from *b*:** correlation is abstract; slope has units. Chapter explicitly addresses this.
- **Correlation ≠ causation:** named repeatedly. Could use more vivid counterexamples (ice cream and drowning, roosters crowing and sunrise).
- **Distinguish $R^2$ and accuracy:** $R^2$ = 0.9 does not mean 90% of predictions are "right." Needs attention.
- **Linear vs. nonlinear:** modules mention this; chapter defers but flags it as assumption.

### Trade-offs and scope

- **Fit vs. complexity:** overfitting mentioned in chapter (Figure 9). Could be more prominent.
- **Inference vs. prediction:** modules distinguish confidence (mean) and prediction (individual) intervals; chapter mentions but does not derive.
- **Computation vs. understanding:** modules show formulas; chapter uses software-independent language.
- **Multiple regression:** modules hint; chapter explicitly defers.

### Scale shifts and context

- **From Galton's peas to modern prediction:** personal genetics and big data. Not in chapter but relevant.
- **From exam scores to institutional policy:** how schools use regression for placement. Belongs in a future applied chapter.
- **From drug dosing to personalized medicine:** biostatistics context. Good for a health-sciences version.

### Misconceptions and common errors

- Treating *r* = 0.9 as "90% accurate."
- Assuming extrapolation is safe.
- Assuming correlation adjusts for confounding.
- Confusing regression toward the mean with poor measurement.
- Misinterpreting negative intercepts (data outside the fit range).

All addressed in chapter or pantry.

---

## Alignment with book's arc

Chapter 13 is the finale. It caps 12 chapters of building inferential machinery.

- **Chapters 1–2:** Sampling and data. Regression assumes you have good, representative data.
- **Chapters 3–5:** Probability and distributions. Regression assumes errors are normally distributed.
- **Chapters 6–7:** Normal distribution and CLT. Regression theory rests on these.
- **Chapters 8–9:** Confidence and hypothesis testing. Regression significance testing extends this.
- **Chapters 10–12:** Two-sample and ANOVA tests. Regression is the general linear model; ANOVA is a special case.
- **Chapter 13:** Regression. Ties it all together: What have we learned? How do two variables move together? What can we predict? What can we not?

The chapter's closing "Integration and synthesis" section and the final coda ("What we have learned across all thirteen chapters") make this explicit.

---

## What the modules did well

1. **Clear distinction of roles:** correlation as measure, regression as prediction.
2. **Visual scaffolding:** scatter plots before formulas.
3. **Repeated warnings:** "correlation is not causation" appears in multiple forms.
4. **Worked examples:** every major concept has a numerical walkthrough.
5. **Assumption checking:** residual plots and diagnostic reasoning.

---

## What the rewrite improved

1. **Narrative frame:** Galton's pea experiment gives historical and intuitive motivation.
2. **Conceptual clarity:** the chapter clearly separates three ideas (correlation, regression, fit) rather than mixing them.
3. **Practical scope:** omits multiple regression, logarithmic transformation, and Excel instructions, keeping the chapter focused and accessible.
4. **Causal reasoning:** emphasizes the distinction between association and causation more forcefully, with examples (ice cream and drowning).
5. **Voice:** the chapter adopts the Attenborough × Feynman register—scene-first, mechanism-from-first-principles, moral weight at the end—rather than the abstract, procedural tone of the modules.

---

*Bookmap completed 2026-05-07.*
*Source modules: m55715, m55719, m55726, m55718, m55838, m64846, m56649, m55852.*
