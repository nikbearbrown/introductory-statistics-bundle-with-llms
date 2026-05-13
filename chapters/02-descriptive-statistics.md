# Chapter 2 — Descriptive Statistics

## Three title options

1. **The Shape of Numbers: How the middle, the spread, and the story in a histogram let you see what data are actually saying**
2. **What Lives in the Distribution: Center, variation, and the skew that separates a precise picture from a lie**
3. **Reading a Dataset: From histograms to box plots—the visual and numerical tools that make data speak**

---

## TL;DR

Descriptive statistics is how you see what a dataset is actually showing. Start with a picture: a histogram reveals whether the data cluster in one place or spread across many. Then measure the center—the mean (average) or median (middle value)—and ask which one makes sense for your question. Finally, quantify the spread. A standard deviation tells you how far, on average, values stray from the mean. When one number sits far from the others (an outlier), the median becomes more honest than the mean. The shape of the distribution—symmetrical, left-skewed, or right-skewed—changes which measures to trust.

---

## Cold open: The salary negotiation

You walk into a hiring meeting at a tech company. The recruiter says, "Our engineers earn an average of $95,000 a year." You're impressed. Then you ask to see the distribution. The spreadsheet lands on your desk: one principal engineer earning $780,000, and forty-two junior engineers earning $48,000 to $62,000. The mean ($95,000) is pulled up by that single outlier. The median—the true middle—is $51,500. Same dataset. Two completely different stories.

This chapter teaches you to see both stories, and to know which one to believe.

### Learning objectives

By the end of this chapter you will be able to:

- **Display** data using histograms, stem-and-leaf plots, and box plots, and **interpret** what the shape tells you.
- **Calculate** the mean, median, and mode, **choose** the right one for your question, and **understand** why outliers break the mean.
- **Compute** the range, interquartile range (IQR), variance, and standard deviation, and **translate** what each one measures.
- **Compare** datasets using measures of spread and identify potential outliers using the 1.5 × IQR rule.
- **Explain** how skewness changes the relationship between mean and median.
- **Determine** percentiles and quartiles from ordered data.

### Prerequisites

Comfort with arithmetic (addition, division, squaring). Ability to order numbers from smallest to largest. Willingness to stare at a list of data and ask: "What is actually happening here?"

### Why this chapter matters

Every time you read "the average American earns," "test scores have improved," or "this product is rated higher"—you are reading a statistical claim. Chapter 1 taught you to collect data without bias. This chapter teaches you to describe what the data show truthfully. The mean can lie. The median might mislead you in a different way. A histogram can be designed to exaggerate or hide the story. Your job is to see through the noise and report what's real.

---

## Concept 1 — Getting the shape: Visualization before you measure

When you have two thousand observations—two thousand salaries, two thousand test scores, two thousand customer wait times—a raw list is overwhelming. You need a picture first.

### The histogram: where the data actually cluster

A **histogram** divides the data into adjacent intervals (called *bins* or *classes*) and counts how many observations fall in each. The height of each bar is the count (or *frequency*). Unlike a bar graph, the bars touch because the intervals are continuous.

To build one:

1. Find the minimum and maximum values in your dataset.
2. Decide how many intervals you want (typically 5 to 15, depending on your dataset size). A rough rule: use the square root of *n*, the number of observations. For 100 observations, that's 10 intervals.
3. Calculate the interval width: (max − min) / number of intervals.
4. Set the first interval boundary slightly below the minimum (so no value lands on an edge boundary and creates ambiguity).
5. Count how many observations fall in each interval.
6. Draw a bar for each interval with height equal to the count.

[FIGURE: Histogram example. Horizontal axis: continuous variable (e.g., salary in dollars), divided into adjacent intervals. Vertical axis: frequency (count). Bars touch each other. Title demonstrates how to read height and frequency.]

**Why it matters:** The histogram shows you where the data cluster. Are they bunched in the middle, or spread across the range? Are they higher on one side? That shape tells you everything about what to measure next.

#### A worked example — histogram from grouped data

Fifty sociology students reported hours spent on social media per week. The frequency table shows:

| Hours (interval) | Frequency |
|---|---|
| 0–4.9 | 8 |
| 5–9.9 | 14 |
| 10–14.9 | 16 |
| 15–19.9 | 9 |
| 20–24.9 | 3 |

To construct the histogram:

- Interval width: all intervals are 5 hours wide (by design).
- Bars are drawn at the x-values 0–4.9, 5–9.9, and so on.
- Heights are 8, 14, 16, 9, and 3 respectively.
- The tallest bar is at 10–14.9 hours. That's where most students cluster.

**Observation:** The data are not symmetrical. More students report heavy use (10–15 hours) than light use (0–5 hours). The distribution is *skewed left*—it has a long tail toward the lower hours. This skew is important; it tells us the mean will be pulled higher than the median.

### Stem-and-leaf plots: seeing individual values

A **stem-and-leaf plot** (or **stemplot**) is useful for small datasets (up to about 50 observations). It preserves the actual data values while showing the distribution shape.

Each value is split into a *stem* (the leading digit or digits) and a *leaf* (the final significant digit).

For example: the value 43 has stem 4 and leaf 3. The value 156 has stem 15 and leaf 6.

To construct:

1. List stems in a vertical column, from smallest to largest.
2. For each observation, write its leaf next to the appropriate stem.
3. Arrange leaves in increasing order (left to right) next to each stem.

#### A worked example — test scores

Exam scores for 20 students: 49, 53, 55, 55, 61, 63, 67, 68, 68, 69, 69, 72, 73, 74, 78, 80, 83, 88, 88, 88.

| Stem | Leaf |
|---|---|
| 4 | 9 |
| 5 | 3, 5, 5 |
| 6 | 1, 3, 7, 8, 8, 9, 9 |
| 7 | 2, 3, 4, 8 |
| 8 | 0, 3, 8, 8, 8 |

**Reading the plot:** Most scores cluster in the 60s and 70s. The 80s have three students with the score 88, which appears frequently. The 40s and 50s have fewer observations. The shape suggests the distribution has a slight left skew—more concentration in the middle-to-upper range, with a tail toward the lower scores.

### Box plots: the five-number summary at a glance

A **box plot** (also called a **box-and-whisker plot**) summarizes data using five numbers:

- **Minimum:** the smallest value
- **Q1 (first quartile):** the 25th percentile; 25% of data fall at or below this
- **Median (Q2):** the 50th percentile; the middle value
- **Q3 (third quartile):** the 75th percentile; 75% of data fall at or below this
- **Maximum:** the largest value

The **interquartile range (IQR)** = Q3 − Q1. It captures the spread of the middle 50% of the data.

A box plot shows:

- A box from Q1 to Q3 (the IQR)
- A line inside the box at the median
- Whiskers (lines) extending from Q1 to the minimum and from Q3 to the maximum
- **Outliers** plotted as individual points beyond the whiskers

[FIGURE: Box plot. Horizontal axis: variable (e.g., age, salary). Box spans Q1 to Q3, with median line marked inside. Whiskers extend to min and max. Any points beyond 1.5 × IQR from Q1 or Q3 are plotted separately as outliers.]

**Outlier detection:** A value is a *suspected outlier* if it lies:
- Below Q1 − 1.5(IQR), or
- Above Q3 + 1.5(IQR)

This rule separates unusual values from those that are simply at the extreme end of a normal spread.

#### A worked example — real estate prices

Thirteen house prices (in dollars): 114,950; 158,000; 230,500; 387,000; 389,950; 479,000; 488,800; 529,000; 575,000; 639,000; 659,000; 1,095,000; 5,500,000.

Five-number summary:
- Min = 114,950
- Q1 = (230,500 + 387,000) / 2 = 308,750
- Median = 488,800 (the 7th value)
- Q3 = (639,000 + 659,000) / 2 = 649,000
- Max = 5,500,000

IQR = 649,000 − 308,750 = 340,250

Outlier boundaries:
- Lower: 308,750 − 1.5(340,250) = −201,625 (no houses below this)
- Upper: 649,000 + 1.5(340,250) = 1,159,375

The house priced at 5,500,000 exceeds the upper boundary. **It is a suspected outlier.** The 1,095,000 house is also unusual but falls within the whisker range.

### Common misconceptions

**"A histogram always has to start at zero."** No. The vertical axis should start at zero, but the horizontal axis (the variable being measured) can start at any sensible point. If salaries range from $40,000 to $120,000, don't force the axis to include $0; you'll waste space and obscure the story.

**"Outliers are always mistakes."** Sometimes. But outliers can also reveal important facts—a student who studied far more than peers, a customer with an exceptionally large purchase, a measurement error. Always investigate.

**"The box plot hides information."** True, it summarizes. But that's the point. For 10,000 observations, a box plot is more informative than printing the list.

---

## Concept 2 — Measuring the center: Mean, median, mode

Three measures describe the "center" of data. Each answers a different question.

### The mean: the balance point

The **mean** (also called the *arithmetic mean* or *average*) is the sum of all values divided by the number of values. In symbols:

$$\overline{x} = \frac{\sum_{i=1}^{n} x_i}{n}$$

where $\overline{x}$ (read "*x* bar") is the sample mean, $\sum$ means "add up," $x_i$ is the *i*-th observation, and *n* is the sample size.

For a population, the symbol is $\mu$ (mu, the Greek letter m), pronounced "myoo":

$$\mu = \frac{\sum_{i=1}^{N} x_i}{N}$$

where *N* is the population size.

**Intuition:** Imagine the data as weights balanced on a seesaw. The mean is the point where the seesaw balances. If you have observations 2, 4, 6, the mean is 4. If you shift one value to 10, the mean shifts to (2 + 4 + 10) / 3 = 5.33. The seesaw tips to follow the outlier.

#### When data repeat: use frequencies

If the data are 1, 1, 1, 2, 2, 3, 4, 4, 4, 4, 4 (where some values repeat), calculate:

$$\overline{x} = \frac{3(1) + 2(2) + 1(3) + 5(4)}{11} = \frac{35}{11} = 3.18$$

Multiply each distinct value by its frequency, sum, and divide by total count.

#### A worked example — ER patient ages

A hospital tracks ages of 40 patients in the emergency room over one week (sorted): 3, 4, 8, 8, 10, 11, 12, 13, 14, 15, 15, 16, 16, 17, 17, 18, 21, 22, 22, 24, 24, 25, 26, 26, 27, 27, 29, 29, 31, 32, 33, 33, 34, 34, 35, 37, 40, 44, 44, 47.

Sum = 944; Mean = 944 / 40 = 23.6 years.

**Observation:** The mean is 23.6, but most patients are younger (cluster in the 14–27 range). One outlier (47 years) and several older patients pull the mean upward. This is the nature of the mean: it is sensitive to extreme values.

### The median: the middle, unmoved by outliers

The **median** is the middle value when data are ordered from smallest to largest. For *n* observations, the median is at position (*n* + 1) / 2.

- If *n* is odd, the median is the middle value (e.g., for 7 values, position 4).
- If *n* is even, the median is the average of the two middle values (e.g., for 40 values, average of positions 20 and 21).

In symbols, the median is often denoted *M*.

**Intuition:** The median is not pulled by outliers. Half the data are at or below it; half are at or above it. If you have a billionaire in a room of middle-class people, the mean income soars but the median stays close to what most people earn.

#### Continuing the ER example

40 patients: position = (40 + 1) / 2 = 20.5. The median is between the 20th and 21st values (the two 24s).

Median = (24 + 24) / 2 = 24 years.

**Comparison:** Mean = 23.6 years; Median = 24 years. They're close here because the outlier (47) is not extreme enough to dominate. But the median gives a slightly clearer picture of the "typical" patient age.

#### The critical salary example

A small town has 50 people. One earns $5,000,000; the other 49 earn $30,000.

Mean = (5,000,000 + 49 × 30,000) / 50 = $129,400.
Median = $30,000.

The mean is a lie for this dataset. The median tells the truth: most people in the town earn about $30,000.

**Rule of thumb:** When data contain outliers or extreme values, prefer the median. When data are roughly symmetrical, the mean and median are similar; either works.

### The mode: the most frequent value

The **mode** is the value that appears most often. A dataset can have one mode (unimodal), two modes (bimodal), or many modes (multimodal). Some datasets have no mode (all values appear equally often).

**When to use the mode:**

- Categorical data: "Which color T-shirt sells most?" The mode is the category with the highest count.
- Discrete data with clear peaks: if a dataset has two clear bumps in the histogram, the modes are the peaks.
- Marketing: "What is the typical purchase amount?" might be better answered by the mode than the mean (especially if one giant order exists).

#### A worked example — exam scores

Scores for 20 students: 50, 53, 59, 59, 63, 63, 72, 72, 72, 72, 76, 78, 81, 83, 84, 84, 84, 90, 93, 94.

The value 72 appears four times (more than any other). Mode = 72.

**Bimodal example:** Five real estate exam scores: 430, 430, 480, 480, 495.
- 430 appears twice
- 480 appears twice
- 495 appears once

The dataset is bimodal: modes are 430 and 480.

### The relationship between center measures and skewness

When a distribution is **symmetrical**, the mean, median, and mode are all approximately equal.

When a distribution is **skewed right** (long tail toward high values), the mean > median > mode. The mean gets pulled up by the high outliers.

When a distribution is **skewed left** (long tail toward low values), the mean < median < mode. The mean gets pulled down by the low outliers.

[FIGURE: Three histograms side by side. Left: symmetrical distribution, mean = median = mode. Center: right-skewed, mean pulled right. Right: left-skewed, mean pulled left. Arrows show relative positions of mean, median, mode.]

### Common misconceptions

**"The mean is always the best measure of center."** No. It breaks when outliers exist. Use median for data with extremes.

**"The mode is only useful for categories."** Modes appear in quantitative data too, and they tell a real story about frequency.

**"You report all three and let the reader choose."** That's lazy. *You* analyze the data. *You* decide which measure answers the question. Report the one that's honest for the question at hand, and explain why you chose it.

---

## Concept 3 — Measuring spread: Why the middle is only half the story

Two datasets can have the same mean but very different shapes. Spreadness (or *variation*) is the other half of understanding data.

### The range: simple but crude

The **range** is the difference between the maximum and minimum values:

$$\text{Range} = \text{Max} − \text{Min}$$

It's easy to compute but tells you nothing about what happens in between. Two datasets with the same range could be entirely different: one could have all values clustered at the endpoints, the other spread evenly across.

### The interquartile range: the spread of the middle

The **IQR** is Q3 − Q1. It measures the spread of the middle 50% of the data and is **not affected by outliers** (because Q1 and Q3 are themselves robust to extremes). This makes IQR more useful than range when outliers are present.

### Variance and standard deviation: measuring average squared distance from the mean

The **variance** is the average of the squared deviations from the mean. In symbols, for a sample:

$$s^2 = \frac{\sum_{i=1}^{n} (x_i - \overline{x})^2}{n - 1}$$

For a population:

$$\sigma^2 = \frac{\sum_{i=1}^{N} (x_i - \mu)^2}{N}$$

Note the difference: sample variance divides by *n − 1* (Bessel's correction), while population variance divides by *N*.

**Why squared deviations?** Because deviations can be positive or negative. Squaring makes them all positive. Squaring also amplifies large deviations (a distance of 10 from the mean becomes 100; a distance of 100 becomes 10,000), which gives weight to outliers.

The **standard deviation** is the square root of variance:

$$s = \sqrt{s^2} \quad \text{(sample)}$$

$$\sigma = \sqrt{\sigma^2} \quad \text{(population)}$$

Taking the square root returns you to the original units of measurement. If you're measuring heights in inches, the standard deviation is also in inches (whereas variance would be in square inches—an abstract unit).

#### A worked example — calculating standard deviation step by step

Five observations: 2, 4, 6, 8, 10.

Step 1: Calculate the mean.
$$\overline{x} = \frac{2 + 4 + 6 + 8 + 10}{5} = \frac{30}{5} = 6$$

Step 2: Calculate deviations $(x_i - \overline{x})$ for each value.
| $x_i$ | $x_i - \overline{x}$ | $(x_i - \overline{x})^2$ |
|---|---|---|
| 2 | −4 | 16 |
| 4 | −2 | 4 |
| 6 | 0 | 0 |
| 8 | 2 | 4 |
| 10 | 4 | 16 |

Step 3: Sum the squared deviations.
$$\sum (x_i - \overline{x})^2 = 16 + 4 + 0 + 4 + 16 = 40$$

Step 4: Divide by *n − 1* for sample variance.
$$s^2 = \frac{40}{5 - 1} = \frac{40}{4} = 10$$

Step 5: Take the square root for sample standard deviation.
$$s = \sqrt{10} \approx 3.16$$

**Interpretation:** On average, each observation is about 3.16 units away from the mean (6).

#### Another example: comparing two datasets

**Supermarket A:** Mean wait time = 5 minutes, SD = 2 minutes.
**Supermarket B:** Mean wait time = 5 minutes, SD = 4 minutes.

Both have the same average wait. But Supermarket B's standard deviation is twice as large, meaning waits are more unpredictable. At A, you expect 5 ± 2 minutes (usually between 3 and 7). At B, waits can be as short as 1 minute or as long as 9 minutes. Same mean, very different customer experience.

### Percentiles and quartiles: locating a value within the distribution

A **percentile** divides ordered data into 100 equal parts. The *p*-th percentile is the value below which *p*% of the data fall.

**Quartiles** are special percentiles:
- Q1 (first quartile) = 25th percentile
- Q2 (second quartile) = 50th percentile = median
- Q3 (third quartile) = 75th percentile

#### Calculating percentiles from ordered data

For the *k*-th percentile in a dataset of *n* values:

1. Calculate the index: $i = \frac{k}{100}(n + 1)$
2. If *i* is a whole number, the percentile is the value at position *i*.
3. If *i* is not a whole number, round down and up to the nearest integers. Average the values at those two positions.

#### A worked example — test percentiles

29 test scores (ordered): 18, 21, 22, 25, 26, 27, 29, 30, 31, 33, 36, 37, 41, 42, 47, 52, 55, 57, 58, 62, 64, 67, 69, 71, 72, 73, 74, 76, 77.

Find the 70th percentile.

$$i = \frac{70}{100}(29 + 1) = 0.7 \times 30 = 21$$

Position 21 (a whole number), so the 70th percentile is the 21st value: **64 years**.

Find the 83rd percentile.

$$i = \frac{83}{100}(29 + 1) = 0.83 \times 30 = 24.9$$

Round down to 24, round up to 25. Values are 71 (position 24) and 72 (position 25).

$$\text{83rd percentile} = \frac{71 + 72}{2} = 71.5$$

**Interpretation:** 70% of test-takers scored 64 or below; 83% scored 71.5 or below.

### Outlier detection using IQR

A value is a suspected outlier if:
$$x < Q1 - 1.5 \times \text{IQR} \quad \text{or} \quad x > Q3 + 1.5 \times \text{IQR}$$

This rule uses the IQR (which ignores extremes) to set reasonable boundaries. Values beyond these boundaries are flagged for investigation.

#### Real estate outlier example (revisited)

From Concept 1:
- IQR = 340,250
- Q3 = 649,000

Upper boundary = 649,000 + 1.5(340,250) = 1,159,375

The $5,500,000 house exceeds this boundary, so it's a suspected outlier. The principal architect's estate? A unique property? A data error? Investigate before deciding whether to include or exclude it from analysis.

### Common misconceptions

**"Standard deviation is always the best measure of spread."** Not if outliers dominate. IQR is more robust.

**"If std deviation is 2, almost all data fall within ± 2 of the mean."** That's true only for normally distributed data (which we cover in Chapter 6). For other distributions, the relationship is different.

**"Range is useless."** For a quick summary, it's fine. "Salaries range from $35,000 to $180,000" is informative. But pair it with IQR or SD for a fuller picture.

---

## Integration — putting it together

A wealth management firm has tracked 100 clients' annual portfolio returns over three years. They want to describe the distribution to prospective investors.

**Raw data (returns in percent):** −2.1, 0.5, 1.2, 1.8, 2.0, 2.3, 2.5, 2.7, 2.9, 3.1, ... (98 more values, ranging from −15.3 to 28.4).

### Step 1: Visualize with a histogram

Interval width = (28.4 − (−15.3)) / 10 = 4.37 ≈ 4.5

| Return interval | Frequency |
|---|---|
| −16 to −11.5 | 1 |
| −11.5 to −7 | 2 |
| −7 to −2.5 | 3 |
| −2.5 to 2 | 18 |
| 2 to 6.5 | 28 |
| 6.5 to 11 | 25 |
| 11 to 15.5 | 15 |
| 15.5 to 20 | 5 |
| 20 to 24.5 | 2 |
| 24.5 to 29 | 1 |

The histogram shows a roughly normal (bell-shaped) distribution, slightly left-skewed. Most returns cluster in the 2% to 11% range.

### Step 2: Calculate center measures

Mean = 6.2%
Median = 6.5%
Mode = 7% (appears in the 6.5–11 interval most often)

**Insight:** Mean and median are very close (6.2% vs. 6.5%), confirming the distribution is nearly symmetrical. No extreme outlier is pulling the mean away from the median.

### Step 3: Calculate spread measures

Range = 28.4 − (−15.3) = 43.7%

Five-number summary:
- Min = −15.3%
- Q1 = 2.8%
- Median = 6.5%
- Q3 = 10.5%
- Max = 28.4%

IQR = 10.5 − 2.8 = 7.7%

Standard deviation = 6.1%

### Step 4: Check for outliers

Outlier boundaries:
- Lower: 2.8 − 1.5(7.7) = −9.75%
- Upper: 10.5 + 1.5(7.7) = 22.05%

The return of 28.4% exceeds the upper boundary. **It's a suspected outlier**—probably a exceptional year or a particular client's outperformance.

### The presentation

"Our 100 clients achieved an average annual return of 6.2%, with a standard deviation of 6.1%. Half earned between 2.8% and 10.5%. Most returns clustered between 2% and 11%, though one client achieved 28.4%—an exceptional result. Downside protection was also evident: the lowest return was −15.3%, and only 6 of 100 clients saw losses. The distribution is robust and fairly symmetrical, with no systematic bias toward gains or losses."

This summary—histogram, three center measures, IQR, SD, and outlier note—tells the full story. Prospective clients understand both the typical outcome and the range of possibilities.

---

## Exercises

### Warm-up

**Exercise 2.1** *(LO: interpreting histograms).* A histogram shows the distribution of 200 college students' heights (in inches). The tallest bar spans 68–70 inches with a frequency of 45. The bar for 66–68 inches has frequency 38. What percentage of students are between 66 and 70 inches tall?

**Exercise 2.2** *(LO: mean vs. median).* A used-car lot has 9 vehicles priced at $8,000, $8,500, $9,000, $9,200, $9,500, $10,000, $11,000, $12,000, and $35,000. Calculate the mean and median price. Which better represents a typical vehicle at this lot, and why?

**Exercise 2.3** *(LO: standard deviation intuition).* Two grocery stores have the same average wait time at checkout: 4 minutes. Store A has a standard deviation of 0.5 minutes; Store B has a standard deviation of 2 minutes. What does this difference tell you about the customer experience at each store?

### Application

**Exercise 2.4** *(LO: five-number summary and box plot).* The following are commute times (in minutes) for 15 employees: 12, 14, 18, 20, 22, 25, 27, 28, 30, 32, 35, 38, 40, 42, 55. Calculate Q1, median, Q3, and IQR. Is the 55-minute commute an outlier by the 1.5 × IQR rule?

**Exercise 2.5** *(LO: percentiles).* A standardized test has 10,000 test-takers. You scored in the 87th percentile. Interpret this result. Approximately how many test-takers scored at or below your score?

**Exercise 2.6** *(LO: comparing distributions).* Two salespersons have the same mean monthly sales: $8,000. Person A's sales have SD = $400; Person B's have SD = $2,500. What can you infer about the reliability of each salesperson's performance?

### Synthesis

**Exercise 2.7** *(LO: interpreting shape and center).* A histogram of 500 online-class participation scores (0–100) is right-skewed, with most scores clustered between 60–85. The mean is 72 and the median is 75. Explain why the mean is lower than the median, and which measure better represents a typical student's participation.

**Exercise 2.8** *(LO: working with grouped data).* The following frequency table shows annual salaries (in thousands) for 50 employees in a firm:

| Salary interval (K$) | Frequency |
|---|---|
| 30–40 | 5 |
| 40–50 | 12 |
| 50–60 | 20 |
| 60–70 | 10 |
| 70–80 | 3 |

Estimate the mean salary using the midpoint method. Then construct a histogram. Describe the distribution's shape.

**Exercise 2.9** *(LO: detecting and interpreting outliers).* A dataset of 20 rental prices (in dollars per month) has Q1 = $900, Q3 = $1,400, and one value of $3,500. Is $3,500 a suspected outlier? If so, what might you investigate?

### Challenge

**Exercise 2.10** *(LO: real-world data interpretation).* You are hired to compare employee satisfaction at two firms using survey scores (1–10). Firm A has mean = 7.2, SD = 0.8. Firm B has mean = 7.0, SD = 1.8. Both firms report "average satisfaction around 7." Why might an employee prefer Firm A despite nearly identical means? What risk does low variation at Firm A suggest?

**Exercise 2.11** *(LO: synthesis — full descriptive analysis).* You collect data on the number of books read by 30 high-school students in one year: 0, 2, 3, 5, 5, 6, 7, 8, 8, 9, 10, 11, 12, 12, 13, 14, 15, 16, 17, 18, 19, 20, 22, 24, 25, 28, 30, 35, 40, 50.

(a) Construct a histogram using 5 equal-width intervals.
(b) Calculate the mean, median, and mode.
(c) Calculate Q1, Q3, and IQR.
(d) Identify any suspected outliers using the 1.5 × IQR rule.
(e) Write a paragraph describing the distribution's shape and what it tells you about reading habits in this school.

---

## Chapter summary

Descriptive statistics translates raw data into insight. You now know four ways to see the shape of data: histograms, stem-and-leaf plots, box plots, and the five-number summary. You can measure the center with mean, median, or mode—and you know which to choose when outliers or skewness appears.

You can quantify spread using range, IQR, variance, and standard deviation. Each serves a purpose: range is fast, IQR is robust to outliers, standard deviation is precise. You can identify unusual values using the 1.5 × IQR rule and investigate whether they are data errors, measurement anomalies, or genuine insights.

Most importantly, you understand that a single number (mean or median) is never the whole story. The distribution matters. The spread matters. The shape matters. A histogram showing you where the data actually live is worth more than a mean reported without context.

The salary negotiation from the cold open now makes sense. You ask for the median, not the mean. You ask for the standard deviation. You ask for a histogram. And you make a decision based on truth.

---

## Connections forward

In Chapter 3 (Probability Topics), we assign probabilities to events. We'll build on percentiles: if we know the distribution is normal and we know the mean and standard deviation, we can calculate the probability that a randomly selected value falls in any range.

In Chapter 6 (The Normal Distribution), we'll discover that the mean ± 1 SD, ± 2 SD, and ± 3 SD define predictable regions of probability for bell-shaped data. That connection turns standard deviation from a summary statistic into a forecasting tool.

In Chapter 9 (Hypothesis Testing), we'll use the standard deviation to build a test statistic that asks: "If the null hypothesis were true, how unlikely would our observed sample mean be?" The standard deviation is the ruler we use to measure that unlikelihood.

Throughout, the shapes and measures you learned today—the histogram, the IQR, the standard deviation, the detection of outliers—appear again and again. They are the vocabulary of statistical thinking.

---

## What would change my mind

If I discovered that a different outlier-detection rule (not 1.5 × IQR) better predicted which values were measurement errors or anomalies in a large medical or scientific dataset, I would revise my emphasis. The 1.5 × IQR rule works well in practice, but it is a convention, not a law.

---

## Still puzzling

I don't yet have a fully satisfying intuition for why dividing the sample variance by *n − 1* (rather than *n*) gives a better estimate of the population variance. The mathematical argument (Bessel's correction) is sound, but I want to see it from first principles in a way that feels inevitable, not conventional.

---

## Tags

descriptive-statistics, data-visualization, measures-of-center, measures-of-spread, outliers, percentiles, histogram, box-plot, variance, standard-deviation
---

## LLM Exercise — Chapter 2: Descriptive Statistics (Analyze One Dataset Project)

**Project:** Analyze One Real Dataset.
**What you're building this chapter:** the descriptive-statistics section of your analysis — visualizations, summary statistics, outlier identification.
**Tool:** **Claude Code** is genuinely useful here. Python with pandas + matplotlib + seaborn produces real charts.

---

**The Prompt:**

```
Chapter 2 of my Analyze-One-Dataset project. Foundation Document
is in this Claude Project. Chapter 2 covered: visualization
(histograms for distribution shape, box plots for spread + outliers,
scatter plots for relationships); measures of center (mean, median,
mode — the mean is sensitive to outliers, median is robust); measures
of spread (range, IQR, standard deviation, variance); percentiles
and z-scores; the empirical rule (68-95-99.7 for bell-shaped
distributions); the 1.5×IQR rule for outlier identification.

Write the brief's "Descriptive Analysis" section in 600-1000 words.

1. **Load and inspect.** Show the head() and info() output. Note
   any missing data, the data types pandas inferred, and the
   sample size (n).

2. **Univariate summaries.** For each quantitative variable:
   - Mean and standard deviation.
   - Median, IQR, min, max.
   - Skewness (positive = right-skewed = long right tail;
     negative = left-skewed; ~0 = roughly symmetric).
   - A histogram (produce with matplotlib).
   - A box plot.
   For each categorical variable:
   - Counts and proportions.
   - A bar chart.

3. **Outlier identification.** Use the 1.5×IQR rule:
   - Lower bound: Q1 - 1.5×IQR.
   - Upper bound: Q3 + 1.5×IQR.
   - Anything outside these bounds is flagged.
   For each outlier, note whether it's a data-entry error (clearly
   wrong values), a genuine extreme observation, or context-
   dependent (some sports stats produce many "outliers" that are
   real records).

4. **The empirical rule check.** Pick a quantitative variable that
   looks roughly bell-shaped on its histogram. Check whether ~68%
   of data falls within mean ± 1 SD, ~95% within mean ± 2 SD,
   ~99.7% within mean ± 3 SD. If it doesn't, the variable isn't
   well-approximated by a Normal distribution — note that for
   Chapter 6's revisit.

5. **Z-scores of two extremes.** Pick the maximum value and the
   minimum value of one variable. Compute z = (x − mean) / SD.
   In a Normal distribution, |z| > 3 happens about 0.3% of the
   time. If your extreme has |z| > 3, the variable likely isn't
   Normal (or these are real outliers worth investigating).

End with a "Key descriptive findings" paragraph — the 2-3 most
notable patterns from the descriptive analysis. These often shape
what hypothesis tests will be most interesting in Chapters 9-13.
```

---

**What this produces:** A 600-1000 word section with summary tables, histograms, box plots, and outlier analysis. The descriptive section is the foundation of any analysis report — clean output here pays for itself across all subsequent chapters.

**How to adapt this prompt:**

- *For your own project:* If your dataset has 100+ variables (some have), focus on the 5-10 most relevant to your big question.
- *For ChatGPT / Gemini:* Works as written.
- *For Claude Code:* The right tool here. A Jupyter notebook with cell-by-cell visualization is the cleanest workflow.
- *For a Claude Project:* Save the notebook output (HTML export) alongside the prose.

**Connection to previous chapters:** Chapter 1's variable inventory tells you what to compute summaries for.

**Preview of next chapter:** Chapter 3 covers probability. You'll compute conditional probabilities and contingency tables for categorical variables in your dataset.


---

## 🕰️ AI Wayback Machine

**John Tukey** was invented exploratory data analysis — the framework underlying every modern look at a dataset.

**Run this:**

```
Who is John Tukey, and how does their work connect to descriptive statistics we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"John Tukey"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply John Tukey's framework to a small dataset you actually have.
- Add a constraint: "Answer including criticisms or limits of John Tukey's framework."

What changes? What gets better? What gets worse?
