# Chapter 1 — Sampling and Data

## Three title options

1. **The Listener Problem: How to gather facts without fooling yourself**
2. **From sample to claim: Where data comes from and why it matters**
3. **The machinery of evidence: Building data you can trust**

---

## TL;DR

Statistics begins with a practical problem: you cannot measure everyone, so you must choose a sample. Which people you choose, what you measure about them, and how the measurement happens decide whether your sample tells you the truth about the population or lies to you in ways you'll never detect. The method matters more than the size.

---

## Cold open: The Literary Digest, 1936

October 1936. The *Literary Digest*, a magazine of genuine prestige, had predicted the outcome of every U.S. presidential election since 1916. Sixteen straight. Their formula worked: send surveys to many people, count the responses, announce the result.

This time they sent postcards to ten million Americans. Two million sent them back. The data was massive. The Digest tabulated the numbers and made their prediction: Kansas governor Alf Landon would defeat Franklin Delano Roosevelt, 57% to 43%.

The election happened. Roosevelt won 61% to 39%. The Digest's margin of error was not a statistical hiccup. It was catastrophic—18 percentage points in one direction, the other way from reality.

What went wrong?

The sample was huge. Two million responses. Surely with that much data, the result should be reliable.

But reliability is not about size. It is about *who you are asking*.

The Digest's sample came from three sources: magazine subscriptions, telephone directories, and automobile registration lists. In 1936—the depths of the Great Depression—these were the wealthy. The poor could not afford subscriptions, cars, or phones. Roosevelt was beloved by the poor and working-class voters. Those voters were not in the Digest's sample. They could not be.

The sample, though enormous, was **biased**—systematically skewed toward a group that had reasons to vote differently from the whole population.

A large biased sample is worse than a small unbiased one. Size cannot fix the method. Method is where the truth lives or dies.

### Learning objectives

By the end of this chapter you will be able to:

- **Identify** the components of a statistical study (population, sample, parameter, statistic) and **apply** them to real scenarios.
- **Distinguish** qualitative, quantitative discrete, and quantitative continuous data, and **recognize** what calculations each allows.
- **Evaluate** sampling methods (simple random, stratified, systematic, cluster, convenience) and **identify** sources of bias.
- **Recognize** the difference between sampling error and nonsampling error.
- **Analyze** observational studies versus randomized experiments to understand what evidence can show.
- **Design** a basic study to answer a testable question.

### Prerequisites

Comfort with fractions and percentages. Ability to think about whether a part can represent a whole. No advanced math required; the reasoning matters more than the calculation.

### Why this chapter matters

Every statistical claim you will see—on a poll, a product label, a medical study, a news report—rests on data. The data rests on how it was gathered. A claim is only as good as the method that produced it. This chapter teaches you to ask the hard questions about method before you believe any number.

You will read hundreds of statistical claims in your working life. Most will be true. Some will be honest mistakes. Some will be the result of careful bias on behalf of people with interests to protect. Your defense is method literacy: knowing what kinds of sampling can fool you, what kinds of comparisons prove causation (and what kinds do not), and when a sample is large enough and how large is actually large.

---

## Concept 1 — Populations, samples, and the parameter-statistic gap

A polling firm in the days before a tight election sits in an office where 200 phone lines ring constantly. Each interview takes five minutes. The firm is trying to answer a question: *What percentage of registered voters in this state intend to vote for candidate A?*

They cannot ask all 2.3 million registered voters. That is impossible.

So they ask 1,200.

From those 1,200 answers, they compute a percentage. Suppose 52% of the people they called say they intend to vote for candidate A.

Now comes the hard part: *Does this tell us what the full population thinks?*

**The population**, from the Greek *populo* (the people), is the entire group you care about. In this case: all registered voters in the state. You want to know something about the population. You want to know the true percentage, $p$ (the population *parameter*), who intend to vote for A. You will never know $p$ exactly. You cannot ask everyone.

**A sample** is a subset of the population. The 1,200 people who answered the phone are the sample. From the sample, you compute a number called a **statistic**. The statistic, $\hat{p}$ (pronounced "p-hat"), is 0.52—the percentage in the sample who intend to vote for A.

The statistic is an *estimate* of the parameter. It is your best guess at the true population percentage, based on the data you have.

Here is the central question of this chapter: *How good is that guess?*

The answer depends almost entirely on how you chose the sample.

### From choice to bias: Why method matters more than size

Suppose you stand on a street corner near a college campus and ask the first 100 people who walk by whether they support a tuition increase. You find that 30% do.

You have a sample of 100. That is a decent-sized sample. But the method was terrible. You chose people on a college campus, probably students and staff. You did not call by phone across the whole population. You did not randomly select from a voter registration list. You chose the easiest people to find.

The result is **biased** toward the characteristics of people near college campuses. Older adults, working-class voters who are not near campus, people in rural areas—they are underrepresented or absent. Your sample does not match the population.

Now suppose you use a random number generator to select 1,200 phone numbers from the voter registration list, call those numbers, and find that 52% intend to vote for A.

The method is sound. Every registered voter had an equal chance of being called. The sample should resemble the population. Your estimate is still not perfect—it is a sample, not a census—but it is honest.

A **simple random sample** gives every member of the population an equal chance of being selected. If you have a list of all 2.3 million voters, you assign each one a number, then use a random number generator to pick 1,200 numbers. Those 1,200 people make up your sample. Each group of 1,200 is equally likely to be chosen.

That is the gold standard. It is expensive and slow, but it works.

### Worked example — parameter and statistic in a clinical trial

A pharmaceutical company wants to know the proportion of patients with a specific chronic pain condition who will experience significant relief from a new medication. They cannot treat the entire population of patients with this condition—there are millions. Instead, they recruit 500 patients with the condition, randomize them to receive either the new medication or a placebo, and measure how many in each group experience significant relief.

In the medication group (250 patients), 180 experience significant relief.

**Population:** All patients with this chronic pain condition (parameter unknown, perhaps millions).

**Sample:** The 500 patients enrolled in the study (carefully selected to match the broader population, though not perfectly).

**Parameter:** The true proportion of all patients with this condition who would experience significant relief from the medication—unknown, perhaps 0.70 or 0.72. Denoted $p$.

**Statistic:** The proportion of the sample in the medication group who experienced relief: $180 / 250 = 0.72$ or 72%. Denoted $\hat{p}$.

The company will report: "In our trial, 72% of patients experienced significant relief." Behind that claim sits the hope that the sample statistic is close to the population parameter. But *close* depends on how the sample was chosen.

### Common misconceptions

**"A large sample is always reliable."** The Literary Digest sent surveys to 10 million people and got 2 million responses. The sample was enormous. It was also biased—systematically skewed toward the wealthy. No amount of size fixes a broken method.

**"Random means I choose whoever I feel like."** No. Random means every member of the population has a known, equal probability of being chosen, and a machine (like a random number generator) makes the choice, not your judgment. Your judgment is the enemy of randomness.

**"If my sample is big enough, I don't need to worry about the method."** Wrong. The method decides whether the sample can represent the population at all. Size improves precision once the method is sound, but a biased method ruins everything.

---

## Concept 2 — Types of variables: What you can and cannot do with data

You walk into a hospital and the nurse asks you three questions.

"What is your blood type?" You answer: A positive.

"How many times have you visited this hospital before?" You answer: 3.

"How much pain are you in right now, on a scale from 0 to 10?" You answer: 7.

Each answer is data. Each answer is a **variable**—a characteristic or measurement that differs from person to person.

But the three variables are fundamentally different. You can do different things with each one.

**Blood type** (A+, B−, O+, and so on) is **categorical** or **qualitative** data. It places you in a category. Categories have no order. A+ is not higher than O−. There is no "average blood type." You cannot add blood types or compute their mean. If you ask: *What is the mean blood type of patients in this hospital?*, the question is nonsensical. Blood type makes sense for counting: *How many patients have O−?* It does not make sense for arithmetic.

**Number of previous visits** (0, 1, 2, 3, ...) is **quantitative** data—it is a number. You can add these numbers, compute their mean, ask whether one patient has visited more times than another. But notice the structure: the data come from *counting*. You count the visits. You get a whole number. You cannot have 2.5 previous visits. This is called **quantitative discrete** data. Discrete means separated, countable, jumping from one value to the next.

**Pain level** (0 to 10) is also quantitative, but of a different kind. It could, in principle, be 7.5 or 6.3—any value in a range. This is called **quantitative continuous** data. Continuous data come from *measuring*, not counting. They can take any value in a range.

The distinction is important because different calculations apply to different kinds of data.

Categorical data: count them. Ask which category is most common. Report frequencies and percentages.

Quantitative discrete data: count them, but also add, subtract, compute means and standard deviations.

Quantitative continuous data: add, subtract, compute means and standard deviations, compute medians, analyze distributions.

You cannot meaningfully compute the mean of categorical data. You can compute means of quantitative data. This is the boundary.

### Worked example — classifying variables

A researcher studies first-year college students. She records the following for each student:

- Whether they live on campus or off campus (on/off)
- How many hours per week they study (0 to 30)
- Their major (biology, history, psychology, etc.)
- Their exam score (0 to 100)
- How much sleep they got last night (hours)

**On-campus or off-campus:** Categorical. Two categories. Cannot add them.

**Hours per week studying:** Quantitative discrete. Counting hours. Could be 0, 5, 10, 20. (In practice, hours are often treated as continuous, but they come from counting units—discrete.)

**Major:** Categorical. Many categories. Cannot add them.

**Exam score:** Quantitative continuous. Ranges from 0 to 100. Could be 73, 73.5, 73.25. You can compute means. If 30 students took the exam and their mean score is 78, that is meaningful.

**Sleep hours:** Quantitative continuous. From 0 to maybe 12. Could be 6 hours, 6.5 hours, 7.25 hours. Can compute means.

The researcher can ask: *What is the average exam score of biology majors?* That is meaningful. She can ask: *What is the average major?* That is nonsensical.

### The measurement scale matters: Nominal, ordinal, interval, ratio

Statisticians distinguish four **levels of measurement**. Each level allows different operations.

**Nominal** data are categorical with no order. Blood type, brand of car, color of eyes, yes/no responses. Categories have labels but no ranking. You can count them but cannot order them. A is not "less than" B in blood type.

**Ordinal** data are categorical with order. Top five national parks ranked 1 to 5. Movie ratings (one star, two stars, three stars). Course satisfaction (unsatisfactory, satisfactory, good, excellent). The categories have an order, but the *distance* between them is undefined. The difference between "good" and "excellent" might not be the same as the difference between "unsatisfactory" and "satisfactory."

**Interval** data are numerical with order and equal distances between values, but no true zero. Temperature in Celsius: 0°C is not the absence of heat; temperatures below zero exist. The difference between 30°C and 40°C is the same as the difference between 80°C and 90°C (10 degrees), but 40°C is not twice as hot as 20°C.

**Ratio** data are numerical with order, equal distances, and a true zero. Height in inches (0 inches is the absence of height; you cannot have negative height). Exam score out of 100 (0 is failing; you cannot score below 0). 80 points is twice 40 points. Salary in dollars: 0 is no income; $40,000 is twice $20,000.

For ratio and interval data, all arithmetic makes sense: means, standard deviations, percentiles. For ordinal data, you can count and rank, but the distances are meaningless. For nominal data, you can only count.

### Worked example — deciding what analysis is appropriate

A researcher surveys 200 college students. For each student, she records:

- Class year (first-year, sophomore, junior, senior)
- GPA (0.0 to 4.0)
- Satisfaction with housing (1 to 5 scale, where 1 = very dissatisfied, 5 = very satisfied)

**Class year:** Ordinal. Has order (first-year < sophomore < junior < senior) but the distance between them is not uniform or measurable. You can count how many are in each year and rank them, but reporting the *mean* class year (say, 2.3) is meaningless.

**GPA:** Ratio. Has a true zero (0.0 = no academic credit earned), and all arithmetic is meaningful. The mean GPA of the 200 students, say 3.15, is a real, useful number. A 4.0 is exactly twice a 2.0.

**Satisfaction:** Ordinal. The scale 1-5 has order (1 is more dissatisfied than 5), but the distance from 1 to 2 might not equal the distance from 4 to 5. Some researchers treat ordinal data as interval for practical purposes (compute means), but strictly speaking, they should not.

In practice, the class year and satisfaction would be summarized by counting: "30 students are first-years, 35 sophomores, ..." and "40 students rated their housing as very satisfied, 50 as satisfied, ..." The GPA would be summarized by computing the mean and standard deviation.

### Common misconceptions

**"All numbers are the same kind of data."** No. A score of 5 on a pain scale is not the same as a 5 in a five-category rating. The first might be ordinal (an order, but unknown distances); the second is categorical. Different kinds of data demand different analyses.

**"I can always compute a mean."** No. The mean of categorical data is meaningless. The mean of ordinal data is debatable. Means make sense for interval and ratio data.

**"Continuous and discrete are not important."** They are critical. Discrete data (counts) have no values between the integers. Continuous data can take any value in a range. This affects which statistical tests are appropriate.

---

## Concept 3 — Observational studies and randomized experiments: What can prove causation

You notice that students who study more hours per week have higher exam scores. Does studying *cause* higher scores?

It probably does. But the data you have—a list of students, their study hours, and their exam scores—cannot *prove* causation. The data show a *correlation*. They could support causation, but they could also hide a confounder.

A **confounding variable** is a third variable that affects both the explanatory variable and the response variable, making them appear related when the relationship might not be causal.

Suppose students in the honors program study more hours and also score higher on exams. But maybe the honors program includes smarter students to begin with. The third variable—initial ability—affects both study hours and exam scores. The relationship between study hours and exam performance might be confounded by ability.

To prove causation, you need to *isolate* the explanatory variable from all other differences between groups.

An **observational study** collects data on people as they are, without intervening. You observe study hours and exam scores and see if they correlate. Observational studies are fast and cheap, but they cannot prove causation because you cannot rule out confounders.

A **randomized experiment** assigns people randomly to different treatment groups, so the groups start out the same. Then the researcher applies different treatments and measures the result. If the groups differ in the response after receiving different treatments, that difference must be *caused* by the treatment, because randomization balanced all the potential confounders.

Here is an example. You want to test whether a meditation app reduces test anxiety. You recruit 400 college students. You randomly assign 200 to use the app every day for four weeks, and 200 to a control group (they do not use the app). After four weeks, you measure anxiety levels in both groups.

Because students were *randomly assigned*, the meditation group and the control group should be similar in all other ways: age, major, initial anxiety level, study habits, sleep, everything. The only systematic difference is whether they used the app.

If the meditation group ends up less anxious than the control group, the difference is *caused* by the app (or by the process of using an app—the placebo effect). You cannot be 100% certain, but you can be much more confident than an observational study would allow.

The trade-off is cost and complexity. Randomized experiments are harder to set up and more expensive. Observational studies are natural and cheap. Choose based on what you need: quick insight or proof of causation.

### Worked example — observational study versus randomized experiment

A company wants to know: Does our new wellness program reduce sick days?

**Observational approach:** The company looks at its current employees. Some participate in the wellness program (self-selected), others do not. The company compares sick days in the two groups. They find: wellness participants take 3 days off per year; non-participants take 5 days off per year.

Conclusion: The program reduces sick days.

But is it true? Maybe. Or maybe the kind of person who volunteers for a wellness program is already more health-conscious and would take fewer sick days anyway. Initial health or conscientiousness is a confounder.

**Randomized approach:** The company randomly assigns employees to either the wellness program (200 employees) or a control group that continues their usual routine (200 employees). After one year, the company compares sick days. Again: program participants take 3 days off; control group takes 5 days off.

Because employees were *randomly assigned*, the two groups were balanced on all other traits: age, initial health, conscientiousness, everything. The only systematic difference is the program. The difference in sick days is *caused* by the program.

### Common misconceptions

**"Correlation proves causation."** No. Correlation is an association. Causation means one variable directly affects the other. Confounders can create correlations without causation.

**"A big observational study is as good as a small experiment."** No. A huge observational study cannot prove causation; even a small, well-designed experiment can. Method beats size for causal claims.

**"If the study was well-done, observational data can prove causation."** No. Observational studies are *limited* by design. You cannot rule out confounders because you do not assign treatments. Experiments, if done right, isolate the explanatory variable from confounders.

---

## Integration — From puzzle to practice

Return to the Literary Digest. The question was: *What percentage of voters intend to vote for Landon?* The population was all registered voters in the United States. The parameter was the true percentage.

The Digest tried to estimate the parameter by sampling. But the sample was biased—skewed toward the wealthy. The statistic (the percentage in their sample) did not match the parameter (the true percentage in the population).

Why? Because the sample method was broken.

A simple random sample of 1,500 voters—picked by random number generator from a voter registration list—would have been far more reliable than the Digest's 2 million self-selected, magazine-subscription responses.

Now imagine a researcher wants to test whether a new reading curriculum improves test scores. She has 100 high school students. She divides them into two groups: 50 get the new curriculum, 50 get the standard curriculum. She randomly assigns students to groups (not by choice, but by drawing names from a hat). After one school year, she compares test scores.

This is a randomized experiment. If the new-curriculum group scores higher, the increase is *caused* by the curriculum. Why? Because random assignment balanced all the other variables—prior ability, family income, motivation, everything—between the two groups. The only systematic difference is the curriculum.

The machinery is this:

1. **Identify what you want to know** (a parameter).
2. **Choose how to gather data** (sampling method or experiment design).
3. **Collect the data** (conduct the sample or experiment).
4. **Compute a statistic** (the sample result).
5. **Interpret** (what does the statistic tell you about the parameter?).

Step 2 is where the truth lives or dies. A sound method produces reliable inferences. A broken method produces garbage, no matter how much data you collect.

---

## Exercises

### Warm-up

**Exercise 1.1** *(LO: identify components).* A researcher surveys 500 college students about their average weekly sleep. The students are selected by stopping every tenth person leaving the dining hall.

a) Identify the population and sample.
b) Identify the parameter and statistic.
c) Is this a simple random sample? Why or why not?

**Exercise 1.2** *(LO: classify data).* Classify each variable as categorical, quantitative discrete, or quantitative continuous.

a) Hair color
b) Number of credit cards owned
c) Weight in pounds
d) College major
e) Age in years

**Exercise 1.3** *(LO: measurement scales).* Match each scenario to its measurement level: nominal, ordinal, interval, or ratio.

a) Ranking five restaurants from best to worst
b) Recording temperature in Fahrenheit
c) Assigning employee ID numbers
d) Height in centimeters

### Application

**Exercise 1.4** *(LO: sampling bias).* A company wants to know if employees are satisfied with their benefits. They email a survey to all 1,000 employees. 150 respond; 80% say they are satisfied.

a) Identify the sampling method.
b) Is there potential bias? Explain why or why not.
c) Who is underrepresented in this sample?

**Exercise 1.5** *(LO: observational vs. experiment).* A medical researcher observes that people who drink coffee have lower rates of Parkinson's disease. Is this proof that coffee prevents Parkinson's? Explain what confounder could explain the correlation.

**Exercise 1.6** *(LO: design a study).* You want to test whether a new app helps people stick to a diet. Describe how you would design a randomized experiment to test this. What is your explanatory variable? Your response variable? How would you randomly assign people to groups?

### Synthesis

**Exercise 1.7** *(LO: integrate components).* A school district wants to know whether a new tutoring program improves test scores for struggling students. They randomly select 300 students who scored below the district average last year. 150 are randomly assigned to the tutoring program; 150 continue without tutoring. After one year, they compare test scores.

a) Identify the population, sample, parameter, and statistic.
b) Is this observational or experimental? How do you know?
c) If the tutoring group scores higher, can you conclude the tutoring caused the improvement? Why or why not?

**Exercise 1.8** *(LO: critical evaluation).* A news headline reads: "Study shows chocolate lovers live longer." The study surveyed 1,000 people who buy chocolate regularly and found they live an average of 5 years longer than non-chocolate-buyers. Critique this study. What sampling bias exists? What confounder could explain the finding?

### Challenge

**Exercise 1.9** *(LO: design and critique).* Design a study to test whether a four-day work week improves employee productivity. Your sample can be 200 employees at one company. Should you use a randomized experiment or observational study? Why? How would you measure productivity? What confounders might arise?

**Exercise 1.10** *(LO: open-ended reasoning).* The Literary Digest polled 10 million people and predicted Landon would win. A pollster named George Gallup polled only 50,000 people and predicted Roosevelt would win. Gallup was right; the Digest was spectacularly wrong. Explain how a smaller sample could be more accurate. What did Gallup do differently?

---

## Chapter summary

You can now do six things you could not do before.

**You can distinguish population from sample, and parameter from statistic.** The population is everyone; the sample is a subset. The parameter is the truth you want to know; the statistic is your estimate from the sample. The size of the sample matters less than how it was chosen.

**You can identify whether a sampling method is biased.** Simple random sampling gives every member of the population an equal chance of being chosen. Stratified sampling ensures representation from subgroups. Systematic, cluster, and especially convenience sampling all carry risks of bias. Bias cannot be fixed by collecting more data.

**You can classify data as categorical, quantitative discrete, or quantitative continuous, and you know what calculations each allows.** Categorical data can be counted. Quantitative discrete data can be counted and averaged (but come from counts of whole units). Quantitative continuous data can be measured, counted, and averaged. The level of measurement (nominal, ordinal, interval, ratio) determines which operations are meaningful.

**You can recognize the difference between observational studies and randomized experiments.** Observational studies show correlations but cannot prove causation because confounders might explain the association. Randomized experiments isolate the explanatory variable by assigning subjects randomly to treatment groups, so confounders are balanced across groups. Experiments can prove causation.

**You can spot confounders and lurking variables.** A confounder is a third variable that affects both the explanatory and response variables, making them appear related when the relationship might not be causal. Randomization spreads confounders equally across groups, canceling out their individual effects.

**You can critique a statistical study.** You ask: How was the sample chosen? Is the method unbiased or does the method create systematic error? Is this observational or experimental? If observational, what confounders might explain the finding? If experimental, was random assignment used?

The insight that carries forward: **method is everything**. A large biased sample is worse than a small unbiased one. A well-designed observational study shows what is true now; a randomized experiment can prove what *causes* change. Choose the right method for your question.

What you should be able to teach someone who asks: Why the Literary Digest failed; what makes a sample representative; why random assignment matters; the difference between correlation and causation.

---

## Connections forward

Chapter 2 will teach you descriptive statistics—how to organize and visualize data once you have a sample. You will learn to compute means, medians, and standard deviations, and to read what a graph of data is actually showing. Those tools rest on what you learned here: how to recognize good data versus bad data, and how to know when the data you have can answer the question you asked.

Later, in Chapter 7, you will learn probability—the mathematics of what *should* happen if a process is random and fair. That theory gives you the language to evaluate whether a sample result (a statistic) is close enough to the population truth (the parameter) to trust it. Probability and sampling together become the foundation for inference: asking *how confident can I be in this estimate?* That question is the heart of statistics.

For now, the practical skill is this: before you believe any statistical claim, ask where the data came from. Ask how the sample was chosen. Demand the method. The answer tells you whether the data can be trusted.

---

## What would change my mind

If I learned that a specific sampling method I described as prone to bias is actually unbiased in a particular real-world context I overlooked, or if the Literary Digest's failure involved a methodological factor beyond sample selection (such as systematic data entry errors), I would refine the treatment of those examples.

## Still puzzling

I do not yet fully understand why some organizations continue to use convenience samples and publish results as if they represent populations, given more than a century of evidence that the method fails. The incentive structure must reward speed and cost savings over accuracy, but the magnitude of the gap between what practitioners know and what they do remains striking to me.

---

## Tags

sampling methods, bias, population and sample, Literary Digest 1936, randomized experiments, confounding variables, data types, simple random sampling, observational studies, parameter estimation
---

## LLM Exercise — Chapter 1: Sampling and Data (Analyze One Dataset Project)

**Project:** Analyze One Real Dataset End-to-End — across the semester, pick one publicly-available dataset and apply each chapter's techniques to it. By Ch 13: a 5,000–8,000 word portfolio-quality statistical analysis report.
**What you're building this chapter:** the foundation — pick your dataset, document its sampling design, classify its variables.
**Tool:** **Claude Project** "Stats Analysis — [Your Dataset]" — every later chapter adds a section.

---

**The Prompt:**

```
I'm starting a semester-long project to do a complete statistical
analysis of one real public dataset. Each chapter, I'll apply that
chapter's techniques. By Chapter 13 I'll have a portfolio-quality
analysis report.

Help me set up. Ask me ONE question at a time, waiting for my
answer.

1. Pick the dataset. The dataset must be:
   - Real (no synthetic data — that defeats the project).
   - Public (you can share it without violating privacy).
   - At least 100 rows (for hypothesis testing later); 1000+ is
     better.
   - At least 4 variables, mixed categorical + quantitative.
   - About a topic you care about.

   Good sources for ideas:
   - Kaggle (huge variety; pick one with a clear documentation
     story).
   - data.gov (US government data).
   - UCI ML repository.
   - Sports: Lahman Baseball Database; FBref for soccer; NBA API.
   - Climate: NOAA, ECMWF.
   - Health: WHO, CDC datasets, MIMIC (research access).
   - Surveys: ANES, GSS, World Values Survey.
   - Finance: Yahoo Finance, FRED.

2. Why this dataset. One paragraph — what made you pick it. Having
   a stated reason helps you finish.

3. The big question. Pick ONE specific question you most want to
   answer about the dataset by Chapter 13. Examples:
   - "Does the 3-point shot revolution show up in the data?"
   - "Has urban temperature in Boston risen significantly since
     1950?"
   - "Are health outcomes for low-income vs. high-income patients
     different after controlling for [X]?"
   - "Do reviewers rate restaurants with higher prices higher,
     after controlling for cuisine?"

4. The sampling story. Document how the data was collected:
   - What's the population the dataset claims to represent?
   - What was the sampling frame (the list of units that could
     potentially be sampled)?
   - What sampling method was used (SRS, stratified, convenience,
     census)?
   - What sources of bias might be present? (Selection bias,
     non-response bias, response bias, survivorship bias —
     name any that apply.)

5. Variable types. List EVERY variable in the dataset. For each:
   categorical (nominal or ordinal) / quantitative discrete /
   quantitative continuous. This list shapes every later chapter's
   methods.

After all five answers, write a 400–600 word **Project Foundation**
section. Include:
- The dataset's name and source URL.
- The big question (in one sentence).
- The sampling story.
- The variable inventory (a table with name, type, description).
- A "what I'd revise about how this data was collected" note —
  what bias might affect every conclusion the project reaches.

Save the Foundation Document as the first section of the
analysis report.
```

---

**What this produces:** A 400–600 word Project Foundation section. Most students at this stage realize their dataset has 1-2 sampling issues they hadn't noticed. Name them now — the rest of the project lives or dies on how those biases affect later conclusions.

**How to adapt this prompt:**

- *For your own project:* If you have access to a real dataset from your own work or research, use it. The investment in the project pays off when the dataset is one you care about.
- *For ChatGPT / Gemini:* Works as written.
- *For Claude Code:* Useful for downloading and exploring the dataset (`pandas.read_csv`, `df.info()`, `df.describe()`).
- *For a Claude Project:* Essential. The Foundation Document lives in the project context for every later chapter.

**Connection to previous chapters:** This is the project's opening.

**Preview of next chapter:** Chapter 2 covers descriptive statistics. You'll compute mean, median, SD, percentiles, and produce histograms + box plots for the key variables in your dataset.


---

## 🕰️ AI Wayback Machine

**Florence Nightingale David** was 20th-century British statistician — Karl Pearson's protégée — whose work on combinatorial probability and survey sampling is still cited.

**Run this:**

```
Who is Florence Nightingale David, and how does their work connect to sampling and data we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Florence Nightingale David"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Florence Nightingale David's framework to a small dataset you actually have.
- Add a constraint: "Answer including criticisms or limits of Florence Nightingale David's framework."

What changes? What gets better? What gets worse?
