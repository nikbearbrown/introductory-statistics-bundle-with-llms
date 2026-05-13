# Chapter 13 — Linear Regression and Correlation

## Three title options

1. **The Line That Explains: From scatter to prediction, why regression lets us see what one variable tells us about another**
2. **When Two Things Move Together: Correlation, causation, and the mechanics of the least-squares line**
3. **Explaining the Scatter: How regression isolates signal from noise, and why the line never tells the whole story**

---

## TL;DR

When two variables move together, correlation measures how tightly they move together in a linear pattern. Regression goes further: it finds the line that minimizes squared distances from the data, giving you the best prediction of one variable from the other. But here is the essential warning: the line is only as good as your data, and correlation is never proof of cause. The chapter that closes this book shows you the machinery of association—the mathematics that lets you quantify what you're seeing—and names where the machinery breaks down.

---

## Cold open: The moment Galton planted his peas

Francis Galton was an obsessive measurer. In the 1870s, he grew sweet pea plants, measured their seeds, recorded everything. Then he collected seeds from his tallest plants and from his shortest plants and planted them in a new generation. He measured those seeds. And something strange happened: the tall plants' seeds produced plants that were, on average, shorter than their parents. The short plants' seeds produced plants that were, on average, taller than their parents.

The offspring did not match the parents. Instead, they regressed—they moved back toward the average.

Galton did not understand the mechanism at first. He called it regression. The word stuck. Regression to the mean. His children moving backward from their parents' extremes toward the middle. And we now use the same word—regression—for the statistical machinery that lets us see that movement.

The phenomenon is everywhere. Sons of very tall fathers are tall, but not as tall as their fathers. Daughters of very short mothers are short, but not as short. A student who scores exceptionally high on one exam does not score quite as high on the next. A company that dominates one year does not dominate quite as thoroughly the next.

This is not a flaw in the data. It is not a failure of inheritance. It is a real property of the world: extremes tend to moderate when measured again. Regression to the mean happens because the extreme value was partly luck, partly skill. Luck does not usually repeat.

But Galton's insight goes deeper. If two variables move together—heights of parents and heights of children, exam scores in one semester and the next, one measure of a company's performance and another—then we can draw a line through that scatter. And that line is not random. It obeys a rule. It minimizes something precise. It tells you what the second variable is most likely to be given what you know about the first.

This chapter teaches you that line and why it works. More importantly, it teaches you what it cannot do.

### Learning objectives

By the end of this chapter you will be able to:

- **Recognize** when two variables are correlated and **measure** the strength of a linear relationship with *r*, the correlation coefficient.
- **Interpret** the sign and magnitude of *r*, and **distinguish** correlation from causation.
- **Derive** and **calculate** the least-squares regression line, understanding slope and intercept as measures of association, not proof of effect.
- **Compute** residuals, interpret their meaning, and **diagnose** whether a linear model fits the data.
- **Explain** $r^2$, the coefficient of determination, as the proportion of variance explained.
- **Make predictions** using a regression line and **recognize** when a prediction is extrapolation and therefore unreliable.

### Prerequisites

Understanding of means and standard deviations from Chapter 2. Comfort with the coordinate plane. Willingness to distinguish between "moving together" and "one causing the other."

### Why this chapter matters

Regression is the statistical machinery that lets you quantify association. It is everywhere: predicting house prices from square footage, estimating earnings from education level, modeling how drug dose affects patient response. The strength of regression is that it gives you a line—a single number that summarizes how much one variable changes as the other increases.

But regression is also where students most often go wrong. Because you can always draw a line through data does not mean the line is causal. Because the line fits the data you have does not mean it will fit new data. Because you can make a prediction does not mean the prediction is accurate. This chapter shows you how the line works. More importantly, it shows you what the line cannot show.

---

## Concept 1 — Seeing co-movement: Scatter plots and the correlation coefficient

**Cold open: Two students, two test scores**

Sarah scores 72 on the midterm. She scores 68 on the final.

Marcus scores 85 on the midterm. He scores 88 on the final.

Keisha scores 91 on the midterm. She scores 94 on the final.

What pattern do you see?

The students who scored higher on the midterm also scored higher on the final. The scores move together. If someone tells you a student's midterm score, you can make a reasonable guess about their final score. Not a perfect guess. But reasonable.

Now imagine instead: Sarah scores 72 on the midterm and 88 on the final. Marcus scores 85 on the midterm and 70 on the final. Keisha scores 91 on the midterm and 60 on the final. The relationship reverses. Higher midterm scores predict lower final scores. They move together, but in opposite directions.

Or imagine they do not move together at all: Sarah scores 72 on the midterm and 85 on the final. Marcus scores 85 on the midterm and 60 on the final. Keisha scores 91 on the midterm and 89 on the final. There is no pattern. You cannot predict one from the other.

To see this pattern visually, we plot the data as a scatter plot. The midterm score goes on the horizontal axis. The final score goes on the vertical axis. Each student is one point. If the points form a cloud that tilts upward from lower left to upper right, the variables move together positively. If the cloud tilts downward, they move together negatively. If the cloud is a shapeless blob, there is no linear relationship.

The scatter plot tells you the shape. But we need a number to measure strength. That number is *r*, the correlation coefficient.

### The correlation coefficient: Measuring co-movement

*Correlation*, from Latin *com* (together) and *relatio* (relation), measures how two variables move together. The correlation coefficient *r* ranges from −1 to 1. The sign tells you the direction. The magnitude tells you the strength.

When *r* = 1, every data point lies exactly on an upward-sloping line. Perfect positive correlation.

When *r* = −1, every data point lies exactly on a downward-sloping line. Perfect negative correlation.

When *r* = 0, there is no linear relationship. The points form a shapeless cloud.

When *r* = 0.8, the points cluster fairly tightly around an upward slope, but with scatter. Strong positive correlation.

When *r* = 0.3, the points show a weak upward trend, but the scatter is wide. Weak positive correlation.

The formula for *r* is:

$$r = \frac{\sum\left( x_{i} - \bar{x} \right)\left( y_{i} - \bar{y} \right)}{\sqrt{\sum\left( x_{i} - \bar{x} \right)^{2} \sum\left( y_{i} - \bar{y} \right)^{2}}}$$

This looks intimidating. But here is what it means: You take how far each *x* value is from the mean of *x*. You take how far each *y* value is from the mean of *y*. You multiply those distances. If both are above their means, the product is positive. If one is above and one is below, the product is negative. You add all those products. That is the numerator.

The denominator is the square root of the product of all the squared deviations. It is a scaling factor. It ensures that *r* stays between −1 and 1, regardless of the units you measure in.

In practice, you will never calculate *r* by hand for real data. The arithmetic is tedious for even a dozen data points. Software does it. But the idea is simple: *r* measures how much *x* and *y* move together, scaled so that perfect co-movement is 1, perfect opposition is −1, and no relationship is 0.

### A worked example — interpreting the correlation coefficient

The Bureau of Labor Statistics measures education level and median weekly earnings for workers in the United States. Let's say we have data for 30 occupation groups: high school graduate, associate degree, bachelor's degree, advanced degree, and everything in between, measured in years.

We collect two variables: *x* = years of education, *y* = median weekly earnings in dollars.

High school (12 years): $850
Associate degree (14 years): $1,050
Bachelor's degree (16 years): $1,400
Advanced degree (18+ years): $1,650

We plot these. The scatter goes upward, left to right. We calculate *r* = 0.92.

What does this mean?

*r* = 0.92 tells us: education and earnings move together very strongly. The points cluster tightly around an upward line. If you know someone's education level, you can predict their earnings with reasonable confidence.

But *r* = 0.92 does not mean: more education causes higher earnings. It means: education and earnings are associated. They move together. Causation is a different claim. Education could cause earnings to rise (employers pay more for educated workers). Earnings could cause education (people with higher earnings invest more in education). A third variable could cause both (cognitive ability drives both educational attainment and earning potential, regardless of the diploma).

Correlation is direction and strength of co-movement. Causation is one variable changing the other. Do not confuse them.

### Trade-off: $r$ vs. $r^2$

*r* = 0.9 sounds strong. And it is. But it is stronger than *r^2* = 0.81, which says: 81% of the variation in earnings can be explained by education level. That means 19% is explained by something else. 19% is a lot. It is the difference between a prediction being correct and being off by several hundred dollars.

We often report $r^2$ instead of *r* because $r^2$ has a clear interpretation: it is the proportion of variance explained. But we calculate *r* first, because *r* has the direction (positive or negative) and because squaring a correlation always loses information. When you see *r* = 0.7, remember that $r^2$ = 0.49. Nearly half the variation is unexplained.

### Common misconceptions

**"Correlation of 0.9 means 90% of the variance is explained."** No. *r* = 0.9 means $r^2$ = 0.81, so 81% is explained. The correspondence is squared, not linear.

**"If *r* is close to zero, there is no relationship."** There is no *linear* relationship. The two variables could be perfectly related in some nonlinear way. A correlation of zero means the scatter shows no tilted cloud, but it does not mean the variables are independent. Plot the data. See the shape. Correlation measures only straightness.

**"Correlation of 0.5 with a big sample is meaningless."** No. A correlation of 0.5 with 1,000 data points is statistically significant. It is a real, measurable association, even if half the variation is unexplained. "Statistically significant" means it is not due to random chance. "Practically significant" means it is large enough to matter for your application. Do not mix those up.

---

## Concept 2 — The regression line: Finding the line that best fits the scatter

**Cold open: A drug trial, dose and response**

A pharmaceutical company is testing a new pain reliever. They give patients doses of 50 mg, 75 mg, 100 mg, 125 mg, and 150 mg. For each dose, they measure pain relief on a 0-100 scale.

50 mg: 18 points of relief
75 mg: 32 points
100 mg: 42 points
125 mg: 55 points
150 mg: 68 points

The researchers plot the data. The points do not form a perfect line. But they cluster around an upward trend. If you had to draw one line that best represented that trend, where would you draw it?

This is not a casual question. There are infinitely many lines that pass through or near those five points. Each line gives a different prediction for the relief you would get from, say, 110 mg. How do you choose?

The answer: You choose the line that minimizes something. The least-squares regression line minimizes the sum of squared residuals. Every point has a residual—the difference between the actual value and the value predicted by the line.

*Residual*, from Latin *residuum* meaning what is left over, is what the line does not explain.

For the drug trial, suppose the line is *y* = 10 + 0.45*x*.

At dose 100 mg, the actual relief is 42. The line predicts: 10 + 0.45(100) = 55. The residual is 42 − 55 = −13.

The point is below the line. The line overestimated.

At dose 50 mg, the actual relief is 18. The line predicts: 10 + 0.45(50) = 32.5. The residual is 18 − 32.5 = −14.5.

Again below the line.

The residuals are the vertical distances from each point to the line. Some are positive (point above), some negative (point below). If you just add them, positive and negative cancel. So instead, you square each residual. Sum those squares. That is the Sum of Squared Errors, or SSE.

The least-squares line is the line that minimizes SSE. It is the line where the squared distances from all the points to the line are as small as possible, on average.

Why squares instead of absolute values? Because the calculus works out cleanly. Minimizing the sum of squared errors has a closed-form solution. You do not need to search or approximate. You can calculate the best-fit line directly.

### Deriving the regression line

The equation of the regression line is:

$$\hat{y} = b_{0} + b_{1}x$$

where *b*<sub>0</sub> is the intercept (where the line crosses the *y*-axis when *x* = 0) and *b*<sub>1</sub> is the slope (the change in *y* for each unit increase in *x*).

The slopes and intercept are:

$$b_{1} = r \left( \frac{s_{y}}{s_{x}} \right)$$

$$b_{0} = \bar{y} - b_{1}\bar{x}$$

Look at the slope formula. It says: the slope is the correlation *r*, scaled by the ratio of standard deviations.

This is not a coincidence. It connects correlation and regression. If *r* = 0 (no correlation), the slope is 0 (horizontal line; no change). If *r* = 1 (perfect positive correlation), the slope is the ratio of standard deviations (maximum responsiveness). If *r* = −1 (perfect negative correlation), the slope is the negative of that ratio.

The scaling by standard deviations matters. If *y* is measured in dollars and *x* in years, the slope is in dollars per year. If *y* is in cents and *x* in months, the slope is in cents per month. The standard deviations convert *r* from an abstract correlation into a concrete slope with units.

The intercept formula says: the line passes through the point (*x̄*, *ȳ*), the means of both variables. If you know the slope and the means, you know where the line crosses the *y*-axis.

### A worked example — predicting final exam score from midterm score

A statistics class has 25 students. The midterm is out of 100. The final is out of 100. Here are the results:

Mean midterm: 74
Mean final: 76
Standard deviation of midterm: 10
Standard deviation of final: 11
Correlation: *r* = 0.85

Calculate the regression line. Predict the final exam score for a student who scores 85 on the midterm.

**Step 1: Calculate the slope.**

$$b_{1} = 0.85 \times \frac{11}{10} = 0.85 \times 1.1 = 0.935$$

For each point increase on the midterm, the final is predicted to increase by 0.935 points.

**Step 2: Calculate the intercept.**

$$b_{0} = 76 - 0.935 \times 74 = 76 - 69.19 = 6.81$$

**Step 3: Write the equation.**

$$\hat{y} = 6.81 + 0.935x$$

**Step 4: Predict for a student with midterm score 85.**

$$\hat{y} = 6.81 + 0.935 \times 85 = 6.81 + 79.48 = 86.29$$

The predicted final exam score is 86.29, or approximately 86.

Notice: The student's midterm score of 85 is 11 points above the mean of 74. But the predicted final score of 86.29 is only 10.29 points above the mean final of 76. The prediction regresses toward the mean. This is Galton's insight again. You do not expect the same deviation on the final as on the midterm. You expect some regression back toward the middle. The regression line captures exactly that amount of regression.

---

## Concept 3 — Diagnosing fit: Residuals, $r^2$, and the limits of the line

**Cold open: The perfect line and the cloud of points**

Imagine two scatter plots side by side.

Plot A: 50 data points scattered so tightly around a line that you can barely see the scatter. The line is doing almost all the explaining.

Plot B: 50 data points scattered in a wide cloud. The line passes through the middle, but most points are far from it. The line is doing some explaining, but there is a lot left over.

Both plots could have the same correlation. (In fact, correlation does not depend on the sample size. *r* = 0.8 with 50 points means the same thing as *r* = 0.8 with 500 points.) But the scatter around the line tells a different story.

This is where residuals and $r^2$ come in.

### Residuals: What the line misses

For every data point, the residual is:

$$e_{i} = y_{i} - \hat{y}_{i}$$

The actual value minus the predicted value.

If the residual is zero, the point lies exactly on the line.

If the residual is positive, the actual value is above the line.

If the residual is negative, the actual value is below the line.

A scatter plot of residuals is diagnostically valuable. Plot the fitted values (*ŷ*) on the horizontal axis and the residuals on the vertical axis.

If the line is a good fit, the residual plot should show:
- Points scattered randomly above and below zero with no pattern.
- No outliers far from the line.
- Roughly equal spread above and below across all values of *x*.

If the residual plot shows:
- A curved pattern (points below the line at the edges, above in the middle, or vice versa), the relationship is not linear. A straight line is the wrong model.
- Outliers far from zero, some data points are very poorly predicted. Investigate them.
- The spread increasing as *x* increases (a fan shape), the variance is not constant. Predictions are less reliable at high values of *x* than at low values.

A residual plot tells you whether your model assumptions hold. The regression line assumes a linear relationship with constant variance and normally distributed errors. If the residual plot violates those assumptions, the line is less trustworthy.

### $r^2$: The proportion of variance explained

We have already seen $r^2$ in Concept 1. Now we derive it from the residuals.

The total variation in *y* is measured by the sum of squared deviations from the mean:

$$\text{SS}_\text{total} = \sum (y_{i} - \bar{y})^{2}$$

The variation not explained by the line is the sum of squared residuals:

$$\text{SS}_\text{error} = \sum (y_{i} - \hat{y}_{i})^{2}$$

The variation explained by the line is:

$$\text{SS}_\text{regression} = \text{SS}_\text{total} - \text{SS}_\text{error}$$

The coefficient of determination is:

$$R^{2} = \frac{\text{SS}_\text{regression}}{\text{SS}_\text{total}} = 1 - \frac{\text{SS}_\text{error}}{\text{SS}_\text{total}}$$

This is the proportion of the total variation in *y* that is explained by *x* through the regression line.

$R^{2}$ = 0: The line explains none of the variation. It is just the horizontal line at the mean.

$R^{2}$ = 0.5: The line explains half the variation.

$R^{2}$ = 0.95: The line explains 95% of the variation. Only 5% is left as residual error.

For simple linear regression (one predictor), $R^{2} = r^{2}$.

### A worked example — examining residuals and $r^2$

Return to the exam data. We fit the line $\hat{y} = 6.81 + 0.935x$ with *r* = 0.85.

Calculate $R^{2}$:

$$R^{2} = r^{2} = 0.85^{2} = 0.7225$$

The regression line explains 72.25% of the variation in final exam scores. That means 27.75% is explained by other factors: how much students studied, whether they were well-rested, their underlying ability, luck, or plain measurement error.

27.75% is substantial. If you were using this line to predict final scores for placement or advising, you would want to know that a quarter of the variation is beyond the model. The line is useful. But it is not the whole story.

Now suppose we examine the residuals. Most students' actual final scores are within 5 points of the prediction. Three students are off by more than 10 points. Two of them scored much higher than predicted (strong final, weak midterm—perhaps they studied hard between exams). One scored much lower than predicted (weak final despite a decent midterm—perhaps they were ill on exam day, or did not study).

These outliers are valuable information. They tell us the model works well for most students but sometimes fails to capture what drives some students' performance. If you were advising a student, you would not just tell them "your predicted final is 86." You would ask: Is there something unusual going on? Are you studying more than your midterm score suggests? Less? Is your test anxiety getting better or worse?

The line is a summary. The residuals are the details that the summary misses.

### Trade-off: Fit vs. complexity

The more variables you add to a regression model, the higher $R^{2}$ gets. You could add midterm grade, GPA, hours studied, sleep quality, test anxiety, and family income. The $R^{2}$ would climb. The predictions would be more accurate.

But here is the cost: the more parameters you estimate, the more your model is fitting the specific data you have rather than learning a general pattern. This is called overfitting. A model with too many parameters predicts your current data well but predicts new data poorly.

This is why we often prefer simpler models even if they have lower $R^{2}$. A line with $R^{2}$ = 0.7 is sometimes better than a complex curve with $R^{2}$ = 0.92. The line is easier to understand, easier to communicate, and more likely to predict new observations correctly.

### Common misconceptions

**"A high $r^2$ means the model is good."** It depends on the application. For predicting house prices from square footage, $R^{2}$ = 0.6 might be excellent (lots of factors affect price beyond size). For predicting a physical constant in a physics experiment, $R^{2}$ = 0.6 might be worryingly low (you expect a tighter relationship).

**"If *r* is not significant, the line is useless."** Statistical significance is about whether the correlation is reliably different from zero. Practical significance is about whether the size of the effect matters. A very small correlation can be statistically significant with a huge sample but still too small to be useful for prediction.

**"Residuals should be normally distributed."** This is one of the regression assumptions. But if the residuals are approximately normal, the inferences (confidence intervals, hypothesis tests) are valid. If they are badly non-normal (heavily skewed, extreme outliers), the tests are less reliable. A residual plot will show this.

---

## Integration and synthesis — When correlation breaks down, and why the line is not cause

Here is the moment to step back and name what regression cannot do.

Regression finds the line that best fits the scatter. It quantifies how tightly the variables move together. It lets you predict one variable from the other. But it does not tell you why they move together.

Two variables can be correlated for three reasons:

1. **X causes Y.** More education leads to higher earnings (education causes earning power).

2. **Y causes X.** Higher earnings lead to more investment in education (wealth enables education). Or: pain relief causes patients to increase their dose (response drives dose adjustment).

3. **A third variable causes both.** Cognitive ability causes both higher education and higher earnings. Time of day causes both coffee consumption and traffic accidents.

These three situations produce different scatter plots. They produce different correlations. But regression produces the same line for each. The line is agnostic about causation. It measures association.

To determine causation, you need experimental design, not just observation. You need to randomize: give some people more education (or assign them not to get it) and observe what happens to their earnings. You need temporal precedence: measure *x* before *y*, not both at the same time. You need to rule out confounders: show that the third variable did not cause both.

Observational data can suggest causal hypotheses. But it cannot prove them. Regression on observational data answers: "How strongly are these variables associated?" It does not answer: "Does one cause the other?"

This distinction—between association and causation—is where most statistical mistakes happen. A consulting firm publishes: "Companies with more women on the board earn higher returns." Is that because women improve leadership? Because high-performing companies recruit more women? Because women are more likely to join boards of healthy companies? Regression alone cannot say.

Here is the principle: **Never claim causation from regression without an experiment or a theory that rules out confounding.**

We also must name the assumption of linearity. Regression assumes the relationship between *x* and *y* is a straight line. Some relationships are not. A drug might have no effect below a threshold dose, then a strong effect above it, then a plateau at high doses. That is not linear. A linear regression would fit poorly and give misleading predictions.

Always plot the data first. Look at the scatter. Does it look like a line? Or is there curvature? If there is curvature, try transforming the data (taking logarithms, for example) or fitting a nonlinear model.

And finally, the assumption of extrapolation. The regression line is based on the range of data you observed. If your data range from 50 mg to 150 mg, the line was fit in that range. Predicting the effect at 200 mg is extrapolation. You are guessing what the relationship is outside the range you observed. It might bend. It might break. Extrapolation is unreliable.

Here is what the regression line actually tells you: *Given the data I observed, and assuming the relationship is linear, and assuming the next observation comes from the same population, this is the best prediction of Y given X.*

That is powerful. But it is not magic.

---

## Graduated exercises

### Warm-up

1. You measure height and weight for a sample of adults. You calculate the correlation and find *r* = 0.75. Interpret this in a sentence.

2. The scatter plot of advertising spend vs. sales shows points tilted downward from left to right. Is the correlation positive or negative?

3. A researcher calculates $R^{2}$ = 0.36 for a model predicting test scores from study hours. What percentage of variation in test scores is explained by study hours? What percentage is not explained?

4. The regression line is *ŷ* = 50 + 2*x*. Interpret the slope. Interpret the intercept.

### Application

5. You have test score data for 40 students. Midterm scores: mean = 78, SD = 12. Final scores: mean = 80, SD = 10. Correlation = 0.80.
   - Calculate the slope of the regression line predicting final from midterm.
   - Calculate the intercept.
   - Write the equation.
   - Predict the final score for a student who scores 90 on the midterm.
   - That student is 12 points above the mean midterm. How many points above the mean final are they predicted to be?

6. A company analyzes the relationship between employee tenure (years) and salary (thousands of dollars). They fit a regression line and calculate $R^{2}$ = 0.42. They report: "Our analysis shows tenure causes salary increases." Critique this claim.

### Synthesis

7. You are analyzing data on house price vs. square footage. The correlation is 0.60. A real estate agent says, "Since the correlation is 0.60, we can explain 60% of the variation in house prices from square footage." Is that correct? Explain.

8. A residual plot shows a clear fan shape: the spread of residuals increases as fitted values increase. What does this suggest about the regression model? What assumption is violated?

### Challenge

9. You fit a regression predicting income from education level for 1,000 people. The correlation is 0.25 (weak). A colleague says, "Since the correlation is so small, education does not affect income." What would you tell them?

10. Consider two scenarios: (A) A time-series regression showing that stock price follows a linear trend with $R^{2}$ = 0.95. (B) A cross-sectional regression predicting house prices from size with $R^{2}$ = 0.60. Why might (B) have more practical value than (A), despite the lower $R^{2}$?

---

## Chapter summary — Closing reflection

This chapter brings us to the end of a thirteen-chapter journey. We began with sampling and data, moved through probability and distributions, built confidence and hypothesis testing, and learned analysis of variance. Now we can quantify association.

The regression line is the machinery that binds two variables together mathematically. It is the line that minimizes squared prediction error. It passes through the means of both variables. Its slope is correlation scaled by the ratio of standard deviations. Its $R^{2}$ tells you how much of the variation is explained. Its residuals tell you what is left unexplained.

But here is what we have learned across all thirteen chapters: Statistics is not the mathematics of certainty. It is the mathematics of reasonable inference under doubt.

In Chapter 1, we learned that samples are never perfectly representative. There is always sampling error.

In Chapter 2, we learned that a single mean or median can hide the shape of the data. Summary statistics simplify but also obscure.

In Chapters 3 through 5, we learned that probability is not fate. Randomness means we cannot predict individual outcomes, only long-run frequencies.

In Chapters 6 through 9, we learned that distributions have shape, and that shape lets us bound our uncertainty. We can say, with a stated confidence, where a parameter lies.

In Chapters 10 through 12, we learned to test whether our data are consistent with a hypothesis. We learned that we could be wrong, and we quantified the risk.

Now, in Chapter 13, we learn to quantify association. The regression line shows us how one variable predicts another. But it does not show us causation. It does not show us what will happen if we intervene. It shows us what we observe.

And that distinction—between what we observe and what we can do—is the boundary of statistical reasoning. You can observe a correlation and say, "These move together." You cannot observe a correlation and say, "This one causes that one" without evidence from an experiment or a theory that rules out confounding.

Regression to the mean taught Galton that the world has a tendency to moderate extremes. Children inherit their parents' traits but also inherit randomness. Each generation is not as extreme as the last. Exceptional parents have somewhat ordinary children. Terrible students sometimes become accomplished people.

The regression line is mathematics captured that insight. It says: *Predict the next observation by moving part of the way from the mean toward the extreme you observed.* Not all the way. Some of the way. Because some of what made the observation extreme was luck, and luck is unlikely to repeat.

This is profound wisdom hidden in algebra.

---

## What would change my mind

I have presented regression as a descriptive tool: it summarizes how variables move together in data you have. I would revise this chapter if you presented evidence that practitioners routinely confuse "association" with "causation" in a way that could be avoided through different pedagogy. Perhaps a more forceful reiteration of the causal/associational distinction at multiple points would help. Or perhaps teaching regression after a dedicated chapter on experimental design would reduce confusion. I am not now certain.

---

## Still puzzling

I do not yet fully understand how to teach the leap from "I calculated r" to "I can interpret what this line means for prediction." The conceptual step from correlation as a number to regression as a predictive tool is where students most often get stuck. Better analogies or an earlier cold open might help. I would welcome alternatives.

---

## Tags

linear regression, correlation coefficient, least-squares line, residuals, coefficient of determination, causation, prediction, association

---
---

## LLM Exercise — Chapter 13: Linear Regression and Correlation (Analyze One Dataset Project) — FINAL CLOSER

**Project:** Analyze One Real Dataset — final integration.
**What you're building this chapter:** linear regression on your dataset + the compiled analysis report.
**Tool:** **Claude Code** + **Cowork** for final assembly.

---

**The Prompt:**

```
Chapter 13 — the closing chapter — of my Analyze-One-Dataset
project. Chapter 13 covered: scatter plots for visualizing
relationships; correlation coefficient r (between -1 and +1;
measures linear association strength); r² = coefficient of
determination (fraction of y's variance explained by x); least-
squares regression line ŷ = b₀ + b₁x; residuals (e = y − ŷ);
residual plot for assumption checking; assumptions (linearity,
independence, equal variance, normality of residuals); prediction
within vs. extrapolation outside data range; correlation ≠
causation.

Two parts.

PART A — Regression analysis.

1. **Pick two quantitative variables that could plausibly be
   related.** Build a scatter plot. Observe: is the relationship
   linear? Strong/moderate/weak? Positive/negative? Any outliers?

2. **Compute r and r².**
   - r = correlation coefficient.
   - r² = fraction of y's variance explained by x.
   - Interpret: a moderate r² (say, 0.40) means x explains 40%
     of y's variance.

3. **Fit the regression line.**
   - Slope b₁ = r · (s_y / s_x).
   - Intercept b₀ = ȳ − b₁ x̄.
   - Or use scipy.stats.linregress or statsmodels.api.OLS.
   - Interpret slope in context: "for each one-unit increase in
     [x], [y] increases on average by [slope] units."

4. **Check assumptions via residual plot.** Plot residuals vs.
   fitted values:
   - Random scatter → assumptions met.
   - Pattern → linearity violated.
   - Funnel shape → heteroscedasticity (unequal variances).
   - Outliers → influential points.

5. **The honest reading.** Even if r² is high, correlation ≠
   causation. Address:
   - Could the relationship be confounded by another variable?
   - Could it be reversed (y → x instead of x → y)?
   - Could it be coincidence (with enough variables, some
     correlate by chance)?

PART B — Compile the final report.

Have Claude assemble the full analysis. Each chapter's section is
already in the project. Need to:

1. Write the **Executive Summary** (300-500 words) at the top of
   the report:
   - The dataset and its source.
   - The big question.
   - The three or four most important findings.
   - The conclusion (with calibrated confidence).

2. Order the sections logically (the chapter order works, but
   tighten transitions).

3. Write a **Conclusions** section at the end:
   - Direct answer to the big question.
   - Limitations: sampling issues from Ch 1 + assumption violations
     from later chapters.
   - "What I'd refine if I had more data or more methods" — name
     specifically what's missing.

4. Format the document professionally — section headers, tables,
   figures with captions, references.

5. Output the **compiled report** as a single markdown document
   (5,000–8,000 words). This is the project's deliverable.

End with a 200-word **Coda** — what 13 chapters of analyzing one
dataset taught you about statistics that the textbook alone
wouldn't have. The coda is the project's intellectual-honesty
close.
```

---

**What this produces:** A regression analysis + the compiled 5,000–8,000 word statistical analysis report. This is the project's portfolio piece — a real piece of statistical analysis the student can show.

**How to adapt this prompt:**

- *For your own project:* The Executive Summary is the section a hiring manager or grad-school admissions reader will actually read. Spend disproportionate effort on it.
- *For ChatGPT / Gemini:* Works as written.
- *For Claude Code:* `scipy.stats.linregress` or `statsmodels.api.OLS` for regression.
- *For Cowork:* The right tool for the final assembly — Cowork can pull all 13 sections together into one document.

**Connection to previous chapters:** Every prior chapter feeds this. The "what 13 chapters taught me" coda is the project's reflective close.

**Preview of next chapter:** There is no next chapter — this is the close. What's next is the analysis report itself: a portfolio-quality piece of statistical analysis that any data-curious reader could follow.
```


---

## 🕰️ AI Wayback Machine

**Gertrude Cox** was first woman to chair a statistics department in the US — at North Carolina State — and a pioneer of experimental design and regression methods.

**Run this:**

```
Who is Gertrude Cox, and how does their work connect to regression and correlation we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Gertrude Cox"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Gertrude Cox's framework to a small dataset you actually have.
- Add a constraint: "Answer including criticisms or limits of Gertrude Cox's framework."

What changes? What gets better? What gets worse?
