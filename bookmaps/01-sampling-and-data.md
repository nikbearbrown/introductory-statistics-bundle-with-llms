# Source map — Chapter 1: Sampling and Data

## Source files

The chapter integrates material from five OpenStax Introductory Statistics modules:

1. **01-m54035.md**: Introduction; the question of where statistics lives in everyday life; overview of probability and statistics.
2. **02-m54033.md**: Definitions and key terms (population, sample, parameter, statistic, variable, data); probability introduction; sampling terminology.
3. **03-m54036.md**: Data types and qualitative/categorical vs. quantitative data; discrete vs. continuous; examples with worked exercises.
4. **04-m54038.md**: Levels of measurement (nominal, ordinal, interval, ratio); frequency tables; relative and cumulative relative frequency.
5. **05-m54056.md**: Experimental design; explanatory and response variables; randomized experiments; control groups; placebo; blinding; lurking variables.

Total source material: ~17,000 words across 5 modules.

## Concept coverage

### **Concept 1: Populations, samples, parameters, statistics**
- **Primary source:** 02-m54033.md (Key Terms section)
- **Secondary sources:** 01-m54035.md (framing), 03-m54036.md (sampling section)
- **Coverage:** Definitions of population, sample, parameter, statistic, variable, data; why sampling is necessary (cost, time); relationship between sample and population; accuracy depends on how well sample represents population.
- **Added from voice:** The Literary Digest 1936 failure (from Chapter 8 voice anchor) as primary scene; cold-open narrative around the polling firm on election night; explicit naming of bias and its consequences.
- **Worked example added:** Chronic pain medication trial (population of chronic pain patients, sample of 500 enrolled, parameter = true proportion who experience relief, statistic = 72% in treatment group).

### **Concept 2: Types of variables and data**
- **Primary source:** 03-m54036.md (Data types and classification)
- **Secondary sources:** 02-m54033.md (definition of variable), 04-m54038.md (levels of measurement)
- **Coverage:** Categorical (qualitative) vs. quantitative data; quantitative discrete (counting) vs. quantitative continuous (measuring); nominal, ordinal, interval, and ratio measurement scales; what operations are valid for each type.
- **Added from voice:** Hospital intake questions as cold open; clear naming of the boundary ("You cannot meaningfully compute the mean of categorical data"); worked example with college student variables (major, sleep hours, exam score, housing satisfaction).
- **Restructuring:** Merged the data types (Concept 2.1 in source) with levels of measurement (Concept 2.4 in source) into one concept. The source separates them; the chapter unifies them around the principle: *what calculations does each allow?*

### **Concept 3: Observational studies vs. randomized experiments**
- **Primary source:** 05-m54056.md (Experimental design section)
- **Secondary sources:** 03-m54036.md (sampling methods and bias), 02-m54033.md (variables)
- **Coverage:** Explanatory vs. response variables; treatments and experimental units; the role of randomization in isolating the explanatory variable; control groups and placebos; blinding; the difference between observational data (show association) and experimental data (can show causation); confounding variables and lurking variables.
- **Added from voice:** Meditation app anxiety trial as primary worked example; wellness program observational vs. experimental comparison; explicit naming of confounding and why randomization solves it.
- **Restructuring:** The source (module 05-m54056) is entirely about experimental design. The chapter moves confounding and bias concepts (scattered across modules 03 and 05 in the source) into one coherent concept about why method matters for causal claims.

## Deferred material (with reasons)

### **Sampling methods** (simple random, systematic, stratified, cluster, convenience)
- **Reason deferred:** Module 03-m54036 devotes ~1,800 words to sampling methods. The chapter names the methods and their trade-offs (Table in Concept 1, footnote in Concept 3) but does not walk through each one with examples and exercises.
- **Why deferred:** This chapter's focus is on *what is a sample* and *why method matters*. The detailed taxonomy of sampling methods is a secondary concern. A follow-up chapter on data collection could expand this. The chapter flags that bias exists and comes from method choice; students should know the names but not master the distinctions yet.
- **Recovery:** Exercises 1.1c and 1.4a ask students to identify sampling methods, ensuring they recognize the concepts even though coverage is shallow.

### **Frequency tables, relative frequency, cumulative relative frequency**
- **Reason deferred:** Module 04-m54038 contains ~2,500 words on frequency distributions, with worked examples. The chapter does not include any frequency tables.
- **Why deferred:** Frequency tables are a tool for *organizing and displaying data once you have it*. This chapter is about *where data come from and why method matters*. Frequency tables belong in Chapter 2 (descriptive statistics). Including them here would dilute the focus.

### **Levels of measurement in detail**
- **Reason partially deferred:** The chapter introduces nominal, ordinal, interval, ratio but does not provide the full taxonomy of examples from the source.
- **Why:** The core insight is captured: ordinal and categorical data cannot be averaged; interval and ratio data can. The source has ~800 words on levels; the chapter has ~400. The principle is clear; the examples are spare.
- **Recovery:** Worked example 1.3 (class year, GPA, satisfaction) ensures students can classify at least one example of each level.

### **Research ethics, IRB approval, ethical violations**
- **Reason deferred:** The source includes a section on ethics. The chapter does not.
- **Why deferred:** Ethics is important but secondary to the statistical concepts. This chapter is about sampling and experimental design; ethics is a constraint on those designs. A dedicated ethics section belongs later or in a research methods companion.

## Source-level notes

### **Module 01-m54035**
- **Content:** General introduction; statistics in newspapers, research, everyday life.
- **Used:** Framing and context for cold open. Not used extensively.

### **Module 02-m54033**
- **Content:** Key terms; population, sample, parameter, statistic, variable, data; probability definition; example worked problems (ABC College, university athletes, crash test dummies, malpractice lawsuits).
- **Used:** Core vocabulary. Definitions of parameter, statistic, variable, sample. Worked examples adapted (medical scenario replaces generic examples).
- **Not used:** The three "Try It" examples are replaced with chapter-specific problems (Exercises 1.1–1.10).

### **Module 03-m54036**
- **Content:** Data types (qualitative, quantitative discrete, continuous); examples (backpack weights, house colors, quiz scores); sampling methods (simple random, systematic, stratified, cluster, convenience); sampling bias; non-response bias; variation in data and variation in samples; critical evaluation of studies (common problems: biased samples, self-selected samples, sample size issues, undue influence, non-response, causality, confounding, misleading graphs).
- **Used heavily:** Data types and classification. Sampling methods named (but not deeply explored). Bias and confounding concepts. Critical evaluation checklist adapted into voice.
- **Not used:** Detailed walk-through of each sampling method (reserved for future chapter). Variation in data section (too technical for this chapter's scope).
- **Restructured:** Critical evaluation section (final part of module 3) is integrated into Concept 3 as motivation for randomized experiments.

### **Module 04-m54038**
- **Content:** Levels of measurement (nominal, ordinal, interval, ratio); frequency tables; relative and cumulative relative frequency; worked examples with grouped data (soccer player heights, rainfall); homework (50 exercises, mostly frequency table exercises).
- **Used:** Levels of measurement definitions and examples (temperature, exam scores, blood type).
- **Not used:** Frequency tables, relative frequency, cumulative relative frequency (belong in Chapter 2). Rounding conventions. Homework (exercises replaced with chapter-specific exercises).

### **Module 05-m54056**
- **Content:** Experimental design; explanatory and response variables; treatments; control groups and placebos; blinding and double-blind experiments; lurking variables; placebo effects (with citations); worked examples (smell and maze, placebo headache study); references (McClung & Collins on performance drugs, etc.).
- **Used heavily:** Concepts of explanatory variable, response variable, randomization, control group, lurking variable, confounding. Worked examples adapted (meditation app, wellness program).
- **Not used:** Detailed discussion of placebo effects and the neuroscience behind them (beyond what is necessary to motivate control groups). Ethics section. Most original worked examples replaced with chapter-specific scenarios.

## Historical accuracy notes

The Literary Digest 1936 failure is accurately represented: the Digest sent 10 million cards, received ~2.3 million responses, predicted Landon 57%–Roosevelt 43%, outcome was Roosevelt 61%–Landon 39% (~18-point error). The sample was drawn from subscription lists, telephone directories, and auto registration—all skewed toward the wealthy. This is documented in the historical sources cited in the source modules.

The Gallup counter-example (mentioned in Chapter summary, pushed to Exercise 1.10) is also historically accurate: Gallup polled ~50,000 people using quota sampling (a stratified approach) and predicted Roosevelt's win correctly. This is referenced in source module 03-m54036.

John Kerrich's coin-flip experiment (Kerrich flipped a coin 10,000 times, recorded the results in groups of 100) is not used in the chapter, though it appears in the voice anchor (Chapter 8, Concept 3). The chapter focuses on Digest/Gallup instead because it more directly illustrates sampling bias.

## Concept coherence and flow

The three concepts form an argument:
1. **Concept 1** answers "Where does data come from?" (populations and samples) and "Why does method matter?" (bias, shown through Literary Digest).
2. **Concept 2** answers "What kinds of data exist?" (categorical, quantitative discrete, quantitative continuous) and "What can you do with each?" (levels of measurement).
3. **Concept 3** answers "What evidence can prove causation?" (randomized experiments, not observational studies) and restates the lesson from Concept 1: method is everything.

The chapter integrates all three through the worked examples and exercises, which require students to apply concepts in concert (e.g., Exercise 1.7 asks for population/sample/parameter/statistic in the context of a randomized experiment, tying Concepts 1 and 3).
