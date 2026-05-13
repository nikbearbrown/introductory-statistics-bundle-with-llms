# Pantry — Chapter 2 (Descriptive Statistics)

Computational support, formulas, and step-by-step worked examples.

---

## Worked calculations: Standard deviation

### Simple example (5 values)

Data: 2, 4, 6, 8, 10

**Step 1: Mean**
$$\overline{x} = \frac{2 + 4 + 6 + 8 + 10}{5} = 6$$

**Step 2: Deviations and squared deviations**

| $x_i$ | Deviation $(x_i - \overline{x})$ | Squared $(x_i - \overline{x})^2$ |
|-------|----------------------------------|--------------------------------|
| 2     | −4                               | 16                              |
| 4     | −2                               | 4                               |
| 6     | 0                                | 0                               |
| 8     | 2                                | 4                               |
| 10    | 4                                | 16                              |

**Step 3: Sum of squared deviations**
$$\sum (x_i - \overline{x})^2 = 16 + 4 + 0 + 4 + 16 = 40$$

**Step 4: Variance (sample)**
$$s^2 = \frac{40}{5-1} = \frac{40}{4} = 10$$

**Step 5: Standard deviation**
$$s = \sqrt{10} = 3.162$$

---

## Worked calculations: Quartiles and IQR

### Dataset: 13 house prices

Ordered (smallest to largest):  
114,950; 158,000; 230,500; 387,000; 389,950; 479,000; 488,800; 529,000; 575,000; 639,000; 659,000; 1,095,000; 5,500,000

**Five-number summary:**

1. **Minimum** = 114,950
2. **Q1 (25th percentile):**  
   - *n* = 13 (odd)
   - Lower half: 1–6 → values up to 479,000
   - Middle of lower half (position 3.5) = average of positions 3 and 4
   - Q1 = (230,500 + 387,000) / 2 = **308,750**

3. **Median (50th percentile):**  
   - Position = (13 + 1) / 2 = 7
   - Median = **488,800**

4. **Q3 (75th percentile):**  
   - Upper half: 8–13 → values from 529,000 onward
   - Middle of upper half (position 10.5) = average of positions 10 and 11 overall
   - Q3 = (639,000 + 659,000) / 2 = **649,000**

5. **Maximum** = 5,500,000

**IQR calculation:**
$$\text{IQR} = Q3 - Q1 = 649,000 - 308,750 = 340,250$$

**Outlier boundaries:**
- Lower fence: $Q1 - 1.5 \times \text{IQR} = 308,750 - 1.5(340,250) = -201,625$
- Upper fence: $Q3 + 1.5 \times \text{IQR} = 649,000 + 1.5(340,250) = 1,159,375$

**Outlier check:**  
The value 5,500,000 > 1,159,375 → **suspected outlier**

---

## Percentile calculation from ordered data

### Dataset: 29 Academy Award-winning actors' ages

18, 21, 22, 25, 26, 27, 29, 30, 31, 33, 36, 37, 41, 42, 47, 52, 55, 57, 58, 62, 64, 67, 69, 71, 72, 73, 74, 76, 77

**Find the 70th percentile:**

$$i = \frac{k}{100}(n+1) = \frac{70}{100}(29+1) = 21$$

Position 21 is an integer, so the 70th percentile = value at position 21 = **64 years**

**Find the 83rd percentile:**

$$i = \frac{k}{100}(n+1) = \frac{83}{100}(29+1) = 24.9$$

*i* = 24.9 is not an integer. Round down to 24, round up to 25.
- Value at position 24 = 71
- Value at position 25 = 72
- 83rd percentile = (71 + 72) / 2 = **71.5 years**

---

## Grouped frequency table: Estimating the mean

### Dataset: Professor Blount's statistics test scores

| Grade interval | Frequency | Midpoint |
|---|---|---|
| 50–56.5 | 1 | 53.25 |
| 56.5–62.5 | 0 | 59.5 |
| 62.5–68.5 | 4 | 65.5 |
| 68.5–74.5 | 4 | 71.5 |
| 74.5–80.5 | 2 | 77.5 |
| 80.5–86.5 | 3 | 83.5 |
| 86.5–92.5 | 4 | 89.5 |
| 92.5–98.5 | 1 | 95.5 |

**Formula:**
$$\text{Mean of grouped data} = \frac{\sum fm}{\sum f}$$

where *f* = frequency, *m* = midpoint.

**Calculation:**
$$\sum fm = 53.25(1) + 59.5(0) + 65.5(4) + 71.5(4) + 77.5(2) + 83.5(3) + 89.5(4) + 95.5(1)$$
$$= 53.25 + 0 + 262 + 286 + 155 + 250.5 + 358 + 95.5 = 1,460.25$$

$$\sum f = 1 + 0 + 4 + 4 + 2 + 3 + 4 + 1 = 19$$

$$\text{Mean} = \frac{1,460.25}{19} = 76.86$$

---

## Interpreting percentiles in context

### SAT score example

A student's SAT reading score is at the 85th percentile.

**Interpretation:**  
- 85% of test-takers scored at or below this student's score
- 15% scored above it
- The student is in the top 15% of all test-takers
- If 2 million students took the test, approximately 300,000 scored higher

### DMV wait time example

A customer's wait time of 32 minutes is the 85th percentile of all wait times.

**Interpretation:**  
- 85% of people waited 32 minutes or less (shorter wait)
- 15% waited longer
- This is a **long wait** — in the top 15%
- A low percentile would be desirable here (short waits are good)

---

## Relationship between center measures and distribution shape

### Symmetrical distribution
- Mean ≈ Median ≈ Mode
- Example: test scores normally distributed around 75
- All three measures are appropriate; choose based on audience

### Right-skewed (positive skew)
- Mean > Median > Mode
- Long tail toward high values pulls the mean rightward
- Example: household incomes (many middle-income, few millionaires)
- **Prefer median** for honest center

### Left-skewed (negative skew)
- Mean < Median < Mode
- Long tail toward low values pulls the mean leftward
- Example: test scores when most students score high (ceiling effect)
- **Prefer median** for honest center

---

## Histogram construction: step-by-step

### Data: 30 student heights (inches)

60, 61, 61, 62, 62, 62, 63, 63, 64, 64, 64, 64, 65, 65, 65, 66, 66, 67, 67, 67, 68, 68, 69, 69, 70, 70, 71, 71, 72, 73

**Step 1: Find range**
- Min = 60, Max = 73
- Range = 13 inches

**Step 2: Decide number of intervals**
- Rule of thumb: √n = √30 ≈ 5.5 → use 6 intervals

**Step 3: Calculate width**
- Width = Range / Number of intervals = 13 / 6 ≈ 2.17 → round to 2.2 or use 2

**Step 4: Set boundaries (avoiding edge issues)**
- Using width = 2, start at 59.9 (slightly below min)
- Intervals: [59.9–62), [62–64), [64–66), [66–68), [68–70), [70–72.9]

**Step 5: Count frequencies**

| Interval | Frequency |
|---|---|
| 59.9–62 | 4 |
| 62–64 | 6 |
| 64–66 | 7 |
| 66–68 | 5 |
| 68–70 | 5 |
| 70–72.9 | 3 |

**Total:** 4 + 6 + 7 + 5 + 5 + 3 = 30 ✓

**Step 6: Draw histogram**
- X-axis: height intervals (continuous)
- Y-axis: frequency (0 to 8)
- Bars touch (no gaps)
- Taller bars at 62–64 and 64–66 → students cluster in mid-range

---

## Key formulas: Quick reference

**Mean (sample):**
$$\overline{x} = \frac{\sum_{i=1}^{n} x_i}{n}$$

**Median (position):**
$$\text{Position} = \frac{n+1}{2}$$

**Variance (sample):**
$$s^2 = \frac{\sum_{i=1}^{n} (x_i - \overline{x})^2}{n-1}$$

**Standard deviation (sample):**
$$s = \sqrt{s^2}$$

**IQR:**
$$\text{IQR} = Q3 - Q1$$

**Outlier boundaries:**
$$\text{Lower} = Q1 - 1.5 \times \text{IQR}$$
$$\text{Upper} = Q3 + 1.5 \times \text{IQR}$$

**Percentile rank (given a value):**
$$\text{Percentile} = \left( \frac{x + 0.5y}{n} \right) \times 100$$

where *x* = number of values below the target, *y* = frequency of the target value, *n* = total sample size.

**Percentile value (given a percentile rank):**
$$i = \frac{k}{100}(n+1)$$

where *k* = desired percentile. If *i* is not an integer, interpolate between positions ⌊i⌋ and ⌈i⌉.
