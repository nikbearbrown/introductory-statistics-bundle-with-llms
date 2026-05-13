# Pantry — Chapter 3: Probability Topics

## Notation guide

- $S$ — the sample space, the set of all possible outcomes
- $A, B, C$ — events (subsets of the sample space)
- $P(A)$ — the probability of event $A$, a number between 0 and 1
- $A \cap B$ — the intersection of $A$ and $B$, read as "$A$ AND $B$"; the set of outcomes in both
- $A \cup B$ — the union of $A$ and $B$, read as "$A$ OR $B$"; the set of outcomes in at least one
- $A'$ — the complement of $A$, read as "not $A$"; the set of outcomes not in $A$
- $P(A \mid B)$ — the conditional probability of $A$ given $B$, read as "the probability of $A$ given $B$"
- $\cap$ in the context of probability usually means multiplication
- $\cup$ in the context of probability usually means addition

## Key formulas

**Basic probability (equally likely outcomes):**
$$P(A) = \frac{\text{number of outcomes in } A}{\text{total number of outcomes}}$$

**Complement:**
$$P(A') = 1 - P(A)$$

**Multiplication rule (AND):**
$$P(A \cap B) = P(A) \cdot P(B \mid A)$$

**If independent:**
$$P(A \cap B) = P(A) \cdot P(B)$$

**Addition rule (OR):**
$$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$

**If mutually exclusive:**
$$P(A \cup B) = P(A) + P(B)$$

**Conditional probability:**
$$P(A \mid B) = \frac{P(A \cap B)}{P(B)}$$

**Bayes' theorem:**
$$P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B)}$$

Where:
$$P(B) = P(B \mid A) \cdot P(A) + P(B \mid A') \cdot P(A')$$

## Definitions

**Sample space:** The set of all possible outcomes of an experiment. Must be exhaustive (every outcome included) and mutually exclusive (no overlap).

**Event:** Any subset of the sample space.

**Experiment:** A procedure whose outcome is not predetermined.

**Equally likely outcomes:** Outcomes that have the same probability. Often assumed when outcomes come from a fair process (fair coin, fair die, random selection).

**Independence:** Two events are independent if knowing one occurred doesn't change the probability of the other. Mathematically: $P(A \mid B) = P(A)$ or equivalently $P(A \cap B) = P(A) \cdot P(B)$.

**Mutual exclusivity:** Two events are mutually exclusive if they cannot both occur. Mathematically: $P(A \cap B) = 0$.

**Conditional probability:** The probability of one event given that another event has already occurred. The sample space is restricted to the event that has occurred.

**Prior probability:** The probability you assign to an event before seeing new evidence. In Bayes' theorem, this is $P(A)$.

**Likelihood:** The probability of the observed evidence given a hypothesis. In Bayes' theorem, this is $P(B \mid A)$.

**Posterior probability:** The probability you assign to an event after seeing new evidence. In Bayes' theorem, this is $P(A \mid B)$.

## Critical distinctions students often confuse

| | Independent | Mutually exclusive |
|---|---|---|
| **Definition** | One event doesn't affect the probability of the other | Events cannot both occur |
| **Formula** | $P(A \cap B) = P(A) \cdot P(B)$ | $P(A \cap B) = 0$ |
| **Condition** | Knowing $B$ doesn't change $P(A)$ | If $B$ occurs, $A$ cannot |
| **Example** | Two die rolls | Card is a heart and a diamond |
| **Can they both be true?** | No, unless one has probability 0 | No (and that's the definition) |

## Common errors in problem-solving

1. **Confusing $P(A \mid B)$ with $P(B \mid A)$:** These are usually different. A test being 95% accurate at detecting disease is not the same as: if you test positive, you have 95% chance of disease.

2. **Forgetting to adjust for dependence:** When drawing without replacement, the second draw's probability depends on the first draw.

3. **Ignoring base rates:** A test that is 99% accurate produces mostly false positives if the condition is rare.

4. **Multiplying when you should add:** Use multiplication for AND (intersection), addition for OR (union).

5. **Double-counting in the addition rule:** Remember to subtract $P(A \cap B)$ to avoid counting overlapping outcomes twice.

6. **Assuming all outcomes are equally likely:** This is only true for fair processes (fair coins, fair dice, random selection).

## Worked examples worth memorizing

**Example 1: Drawing without replacement**
A standard deck has 52 cards. Draw two without replacing the first. Probability both are hearts?
- First heart: 13/52
- Second heart given first was heart: 12/51
- Both hearts: (13/52) · (12/51) = 156/2652 ≈ 0.0588

**Example 2: Addition rule with overlap**
College A: 40% acceptance. College B: 30% acceptance. Independent. Probability of at least one?
- P(A or B) = 0.40 + 0.30 − (0.40)(0.30) = 0.40 + 0.30 − 0.12 = 0.58

**Example 3: Bayes' theorem (medical test)**
- Prior: 1% of population has disease
- Sensitivity: 98% (test positive | disease)
- Specificity: 95% (test negative | no disease)
- False positive rate: 5% (test positive | no disease)
- Question: P(disease | positive test)?

Build a contingency table for 10,000 people:
- 100 have disease, 9,900 don't
- Of 100 with disease: 98 test positive, 2 test negative
- Of 9,900 without disease: 495 test positive, 9,405 test negative
- Total positive tests: 98 + 495 = 593
- P(disease | positive) = 98/593 ≈ 0.165 (about 17%, not 98%)

## Contingency table template

| Event | Condition Met | Condition Not Met | Total |
|---|---|---|---|
| Occurs | a | b | a+b |
| Does not occur | c | d | c+d |
| Total | a+c | b+d | N |

From this table you can read:
- $P(\text{Event}) = (a+b)/N$
- $P(\text{Condition}) = (a+c)/N$
- $P(\text{Event} \cap \text{Condition}) = a/N$
- $P(\text{Event} \mid \text{Condition}) = a/(a+c)$
- $P(\text{Condition} \mid \text{Event}) = a/(a+b)$

## Tree diagram basics

A tree diagram shows conditional probabilities at each branch:
- Each path from root to leaf represents one complete outcome sequence
- The probability of that sequence is the product of the probabilities on the branches (multiplication rule)
- To find the probability of an event that can happen multiple ways, sum the probabilities of all paths leading to that event

Example: Urn with 3 red, 8 blue. Draw 2 with replacement.
- P(RR) = (3/11) · (3/11) = 9/121
- P(RB) = (3/11) · (8/11) = 24/121
- P(BR) = (8/11) · (3/11) = 24/121
- P(BB) = (8/11) · (8/11) = 64/121
- P(at least one red) = P(RR) + P(RB) + P(BR) = 9/121 + 24/121 + 24/121 = 57/121

---

## Checkpoints for reasoning about a probability problem

1. **Have I clearly identified the sample space?** Can I list or describe all possible outcomes?

2. **Are all outcomes equally likely?** If not, what makes them unequal?

3. **Is this asking for AND or OR?** AND uses multiplication; OR uses addition.

4. **Are the events independent or dependent?** If dependent, I need conditional probability.

5. **Are the events mutually exclusive?** If yes, $P(A \cap B) = 0$ and the addition rule simplifies.

6. **Is this a conditional probability problem?** Look for "given," "if," "knowing that."

7. **Do I know the base rate?** For any inference about a hypothesis from evidence, the base rate matters.

8. **Could a contingency table or tree diagram help organize the data?** Often yes for complex problems.
