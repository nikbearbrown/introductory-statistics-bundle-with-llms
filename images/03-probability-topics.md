# Images and Diagrams — Chapter 3: Probability Topics

## [FIGURE: Sample space for two coin flips]

A Venn diagram or rectangle divided into four regions representing the sample space $S = \{HH, HT, TH, TT\}$ for flipping two fair coins. Each region is equally likely (probability 1/4). The student should notice:
- The sample space is exhaustive (every outcome is included)
- The outcomes are mutually exclusive (no overlap)
- Each outcome has equal probability

Regions can be shaded to highlight different events: "at least one head," "both the same," etc.

---

## [FIGURE: Two-set Venn diagram for events A and B]

A rectangle (the sample space) with two overlapping circles labeled $A$ and $B$. Four regions are visible:
1. Only in $A$ (event $A$ but not $B$)
2. Only in $B$ (event $B$ but not $A$)
3. In both (event $A \cap B$)
4. Outside both circles (neither $A$ nor $B$)

This diagram illustrates the addition rule: $P(A \cup B) = P(A) + P(B) - P(A \cap B)$ by showing that the union (shaded region of $A$ or $B$ or both) counts the overlap twice and must be corrected.

Variants:
- Circles that don't overlap (mutually exclusive events)
- Circles where one is completely inside the other (one event implies the other)
- Overlapping circles of different sizes (illustrating different probabilities)

---

## [FIGURE: Tree diagram for drawing with replacement]

An urn contains 3 red balls and 8 blue balls. Draw two balls with replacement.

Root branches into:
- **Red (R):** probability 3/11
  - Branches to: Red (3/11), probability 3/11 → outcome RR, probability (3/11)²
  - Branches to: Blue (8/11), probability 8/11 → outcome RB, probability (3/11)(8/11)
- **Blue (B):** probability 8/11
  - Branches to: Red (3/11), probability 3/11 → outcome BR, probability (8/11)(3/11)
  - Branches to: Blue (8/11), probability 8/11 → outcome BB, probability (8/11)²

The student should notice:
- Probabilities on branches going out from the same node sum to 1
- Probabilities along a path multiply (multiplication rule)
- All path probabilities sum to 1

Labels on branches are probabilities; labels at endpoints can be either probabilities (the product of the path) or frequencies (the product times the total number of trials).

---

## [FIGURE: Tree diagram for drawing without replacement]

An urn contains 3 red balls and 8 blue balls. Draw two balls without replacement.

Root branches into:
- **Red (R):** probability 3/11
  - Branches to: Red (2 left out of 10), probability 2/10 → outcome RR, probability (3/11)(2/10) = 6/110
  - Branches to: Blue (8 out of 10), probability 8/10 → outcome RB, probability (3/11)(8/10) = 24/110
- **Blue (B):** probability 8/11
  - Branches to: Red (3 out of 10), probability 3/10 → outcome BR, probability (8/11)(3/10) = 24/110
  - Branches to: Blue (7 left out of 10), probability 7/10 → outcome BB, probability (8/11)(7/10) = 56/110

The student should notice:
- Probabilities change on the second draw (depend on the first draw result)
- This illustrates dependence: the outcome of the first draw affects the second
- Multiplying along a path still gives the joint probability, but the conditional probabilities are different than with replacement

Compare to the "with replacement" diagram to see how dependence changes the tree structure.

---

## [FIGURE: Contingency table for a medical screening problem]

Two rows (Disease present / Disease absent), two columns (Test positive / Test negative), with cell entries and marginal totals.

Example with concrete numbers from 10,000 screened individuals:

|  | Test positive | Test negative | Total |
|---|---|---|---|
| Disease present | 98 | 2 | 100 |
| Disease absent | 495 | 9,405 | 9,900 |
| Total | 593 | 9,407 | 10,000 |

The student should be able to read from this table:
- $P(\text{Disease}) = 100/10,000 = 0.01$
- $P(\text{Positive}) = 593/10,000 \approx 0.0593$
- $P(\text{Disease} \cap \text{Positive}) = 98/10,000 = 0.0098$
- $P(\text{Disease} \mid \text{Positive}) = 98/593 \approx 0.165$ (restricting the sample space to the 593 positive tests)
- $P(\text{Positive} \mid \text{Disease}) = 98/100 = 0.98$ (restricting to the 100 who have disease)

This illustrates Bayes' theorem by showing that the conditional probabilities in the two directions are very different.

---

## [FIGURE: Distribution of outcomes from repeated coin flips]

A histogram showing the frequency of heads in 100 coin flips, repeated many times. The histogram should:
- Show the most common result is around 50 heads (50%)
- Show that results near 50 are more common than those far from 50
- Show the range of observed results (e.g., from 35 to 65 heads)
- Illustrate the law of large numbers: as the number of flips increases, the relative frequency of heads approaches 0.5

This connects probability (the theoretical prediction that P(heads) = 0.5) to empirical frequency (the actual proportion observed).

---

## [FIGURE: Bayes' theorem as a flow diagram]

A rectangle labeled "Prior $P(A)$" on the left. An arrow pointing right labeled "Evidence $B$ observed, with likelihood $P(B \mid A)$." A rectangle labeled "Posterior $P(A \mid B)$" on the right.

Additional labels:
- The width of the arrow could represent the strength of the evidence
- Below: the formula $P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B)}$
- A note: "The posterior is your updated belief after seeing the evidence."

This helps students visualize Bayes' theorem as a process: you start with a prior belief, you see evidence, and the theorem tells you how to update your belief to the posterior.

---

## [FIGURE: Comparing P(A|B) and P(B|A)]

Two rows, each with a contingency table or a small set of counts, side by side. Left side shows:

|  | B | not B | Total |
|---|---|---|---|
| A | 30 | 70 | 100 |

$P(A \mid B) = 30 / ?$ ... student must restrict to column B and count.

Right side shows the same data reframed:

|  | A | not A | Total |
|---|---|---|---|
| B | 30 | 20 | 50 |

$P(B \mid A) = 30 / ?$ ... student must restrict to row A and count.

The student should see that:
- $P(A \mid B)$ is computed by restricting to those where $B$ is true
- $P(B \mid A)$ is computed by restricting to those where $A$ is true
- These can be very different (30/50 ≠ 30/100)
- Bayes' theorem connects the two

---

## [FIGURE: Independence illustrated with tree diagrams]

Two side-by-side tree diagrams, labeled "Independent events (with replacement)" and "Dependent events (without replacement)."

For independent:
- Probabilities on the second level of branches are the same regardless of the first outcome
- The branches look identical regardless of which first outcome occurred

For dependent:
- Probabilities on the second level of branches change depending on the first outcome
- The branches look different

This visual comparison helps students see that independence means the second outcome's probability distribution doesn't change.

---

## Notes on creating these diagrams

- All diagrams should use clear, high-contrast colors and labeling
- Sample space diagrams should emphasize exhaustiveness and mutual exclusivity
- Tree diagrams should clearly show at which stage probabilities change (with vs. without replacement)
- Contingency tables should use shading to highlight which cells are summed for different probability calculations
- All diagrams should include interpretive labels ("This is the sample space," "This region represents...," etc.)
