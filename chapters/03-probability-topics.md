# Chapter 3 — Probability Topics

## Three title options

1. **What Happens When You Don't Know: Probability as precision under uncertainty**
2. **The Machinery of Chance: How we measure outcomes when the future is unmade**
3. **Thinking in Odds: From drug trials to coin flips to the decision you make right now**

---

## TL;DR

Probability is how we talk precisely about what we don't yet know. It translates *maybe* into numbers between 0 and 1. This chapter teaches you to build a sample space (all possible outcomes), identify events within it, and use addition and multiplication rules to calculate the probability of complex outcomes. The key tension: are two events independent (one doesn't affect the other) or dependent (one does)? Are they mutually exclusive (can't happen together) or not? These distinctions let you move from intuition to calculation.

---

## Cold open: The mammogram puzzle

A woman in her fifties gets a routine mammogram. The radiologist calls back. The test came back positive for breast cancer. The patient is terrified. But before she schedules surgery, she asks a question her doctor should have raised first: "Given that I tested positive, how likely is it I actually have cancer?"

This is not the same as the question the mammogram answers. The test is accurate — it catches about 98% of women who actually have cancer. But that's not what matters now. What matters is: I tested positive; what does that tell me?

The answer depends on something the test itself doesn't measure: how common is breast cancer in the population to begin with? If 1 in 100 women in her age group has cancer, and the test catches 98% of them but produces false positives in 10% of women who don't have cancer, the math says: a positive test means she has maybe a 9% chance of actually having cancer.

She'd be far more likely to *not* have cancer and just to be one of the false positives.

This chapter teaches you the mathematics that resolves that puzzle. It is the machinery of conditional probability — how information changes what we should believe.

### Learning objectives

By the end of this chapter you will be able to:

- **Define** a sample space and represent it with lists, tree diagrams, and tables.
- **Identify** events and compute their probability from equally likely outcomes.
- **Distinguish** between independent and mutually exclusive events — they are different, and students confuse them.
- **Apply** the multiplication rule (for AND) and addition rule (for OR), adjusting for dependence and overlap.
- **Compute** conditional probabilities and use them to update beliefs in light of new information.
- **Use** contingency tables and tree diagrams to organize data and reason about complex probability scenarios.

### Prerequisites

Arithmetic with fractions and decimals. The ability to count outcomes and organize them into groups. Comfort with the notation $P(A)$ to mean "the probability of event $A$."

### Why this chapter matters

Probability is the mathematics of decisions under uncertainty. Every medical test, every polling prediction, every weather forecast rests on probability thinking. When a doctor interprets a test result, when a jury assesses the chance a defendant is guilty, when a patient decides whether to take a medication with side effects — they are reasoning about probabilities. This chapter teaches you to reason with rigor instead of intuition. Intuition about probability is often wrong, sometimes catastrophically.

Later chapters will build on this foundation. Chapter 4 moves from abstract probability to random variables — probability applied to measurable quantities. Chapter 7 introduces the binomial distribution, which counts successes across repeated trials. Hypothesis testing (Chapters 9 and 10) will hinge on your ability to think about what outcomes would be *likely* if some assumption is true and what outcomes would be *unlikely* — that is, probability in the service of evidence.

---

## Concept 1 — Sample space, events, and the basic machinery

**Cold open: A physician reading a dice in a bottle**

You are a pediatrician. A parent brings in their child with a sore throat. You suspect strep. You take a throat culture. The test comes back: *positive*. What do you know?

You know the test detected something in the child's throat. But you already knew that — the parent wouldn't have come in otherwise. What you're trying to figure out is: given this positive test, is it more likely the child has strep than not?

That question is probability, but it is not simple probability. It is conditional probability — the probability of the underlying reality (strep, or not) given the evidence (the test result).

Before we can answer that, we need vocabulary.

### The sample space: All possible outcomes

An **experiment** is something that can happen in more than one way and whose outcome is not predetermined. Flipping a coin is an experiment. Rolling a die is an experiment. Administering a strep test is an experiment.

The **sample space** of an experiment is the set of all possible outcomes. For a single fair coin, the sample space is $S = \{H, T\}$ — heads or tails. For a single die, the sample space is $S = \{1, 2, 3, 4, 5, 6\}$. The sample space must be *exhaustive* — every possible outcome must be listed — and *mutually exclusive* — no outcome can happen at the same time as another.

An **event** is any subset of the sample space. An event might be a single outcome — *rolling a 2* — or a collection of outcomes — *rolling an even number*. When we flip two coins, the event "at least one head" is $\{HH, HT, TH\}$ — three of the four possible outcomes.

The **probability** of an event is a number between 0 and 1, inclusive. $P(A) = 0$ means the event can never occur. $P(A) = 1$ means it will always occur. $P(A) = 0.5$ means the event is equally likely to occur as not to occur. The probability is the long-term relative frequency — if you repeat the experiment many times, the fraction of times the event occurs approaches the probability.

### Computing probability from equally likely outcomes

When all outcomes in the sample space are equally likely, the probability of an event is simple:

$$P(A) = \frac{\text{number of outcomes in } A}{\text{total number of outcomes in } S}$$

A fair die has six equally likely outcomes. The event "rolling an even number" has three outcomes: $\{2, 4, 6\}$. So $P(\text{even}) = 3/6 = 0.5$. The event "rolling at least a 5" has two outcomes: $\{5, 6\}$. So $P(\text{at least 5}) = 2/6 = 1/3 \approx 0.333$.

This is elementary, but notice what it requires: you must be able to count the sample space accurately, and you must be confident that the outcomes are equally likely. With a fair die, both are true. With a real die — especially one from your board games at home — the second assumption might fail. Casino dice are manufactured to avoid the bias that comes from the divots carved out for the spots.

### Common misconceptions

**Probability requires large numbers.** No. If you flip a coin once, the probability of heads is still 0.5, even though you can't run the experiment large numbers of times. Probability describes the uncertainty, not the frequency of repetition.

**Long-term means your next flip will probably be heads.** No. The *long-run relative frequency* approaches 0.5, but that says nothing about the next flip. Each flip is still 50-50. This is the **gambler's fallacy** — the belief that past outcomes influence future ones in a fair game. They don't. The coin has no memory.

**Equally likely means I don't know which outcome will occur.** Not quite. Equally likely means the physical process is symmetric with respect to each outcome — the die is fair, the coin is balanced, the sample is truly random. Ignorance alone doesn't make outcomes equally likely.

### Worked example — the strep test

A rapid strep test has the following accuracy. If a child truly has strep, the test detects it 98% of the time. If a child does *not* have strep, the test incorrectly says they do 15% of the time (the false positive rate). In a pediatric clinic population, about 10% of children with sore throats actually have strep.

You test a child and get a positive result. What is the probability the child actually has strep?

*Given:*
- $P(\text{truly has strep}) = 0.10$
- $P(\text{test positive} \mid \text{truly has strep}) = 0.98$
- $P(\text{test positive} \mid \text{does not have strep}) = 0.15$

*Question:* $P(\text{truly has strep} \mid \text{test positive}) = ?$

This is not one we can answer yet with just sample spaces. It requires conditional probability, which comes later. But notice the structure: the test is highly accurate at detecting strep when it's there. Yet the answer turns out to be closer to 40% than 98%, because strep is rare. Most positive tests are false positives.

---

## Concept 2 — Independent vs. mutually exclusive, and the multiplication rule

**Cold open: The card counter and the dealer's glance**

A blackjack player sits at a casino table. The deck has been reshuffled. Over the next twenty minutes, she plays hands one after another. Each hand is independent of the previous one — knowing what happened last hand doesn't change the odds for this hand. The deck composition is the same. The rules are the same. The outcome of hand 1 has no effect on the probability distribution for hand 2.

But at one table, two events are mutually exclusive: I cannot draw the ace of spades and the ace of hearts on the same hand if I'm only drawing one card. If I draw the ace of spades, the event "ace of hearts" cannot happen. These events share no outcomes.

Independence and mutual exclusivity are not the same thing. Understanding the difference is the most common sticking point for intro probability students.

### Independence: One event doesn't change the probability of the other

Two events $A$ and $B$ are **independent** if the probability of $A$ is the same whether or not $B$ has occurred:

$$P(A) = P(A \mid B)$$

The vertical bar means "given that" — $P(A \mid B)$ is read "the probability of $A$ given $B$."

Equivalently, $A$ and $B$ are independent if:

$$P(A \cap B) = P(A) \cdot P(B)$$

The intersection symbol $\cap$ means AND — the probability that both $A$ and $B$ occur is the product of their individual probabilities.

Example: Roll two fair dice. Let $A$ = "first die shows a 3" and $B$ = "second die shows a 5." These are independent. Knowing the first die showed a 3 tells you nothing about the second die. $P(A) = 1/6$, $P(B) = 1/6$, and $P(A \cap B) = (1/6)(1/6) = 1/36$.

### Mutual exclusivity: The events share no outcomes

Two events $A$ and $B$ are **mutually exclusive** if they cannot both occur:

$$P(A \cap B) = 0$$

Example: Draw one card from a standard deck. Let $A$ = "the card is a heart" and $B$ = "the card is a diamond." These are mutually exclusive. A card cannot be both a heart and a diamond. There is no card in both sets.

Notice: if $A$ and $B$ are mutually exclusive, then knowing $B$ occurred means $A$ definitely did not occur. So $P(A \mid B) = 0$. They are *not* independent (unless one of them has probability 0, a degenerate case).

### The multiplication rule: For AND (intersection)

If you want the probability that both $A$ and $B$ occur — that is, $P(A \cap B)$ — you use the multiplication rule:

$$P(A \cap B) = P(A) \cdot P(B \mid A)$$

If $A$ and $B$ are independent, then $P(B \mid A) = P(B)$, so the rule simplifies:

$$P(A \cap B) = P(A) \cdot P(B) \quad \text{(if independent)}$$

But if $A$ and $B$ are dependent, then $P(B \mid A)$ differs from $P(B)$ because the occurrence of $A$ has changed the landscape. You must account for that change.

**Worked example — drawing cards without replacement**

You have a standard 52-card deck. Draw two cards, one at a time, without replacing the first card.

*Question 1:* What is the probability that both cards are hearts?

The first card has 13 hearts out of 52 cards: $P(\text{first is heart}) = 13/52$.

If the first card was a heart, there are now 12 hearts left in a 51-card deck: $P(\text{second is heart} \mid \text{first was heart}) = 12/51$.

So $P(\text{both hearts}) = (13/52) \cdot (12/51) = 156/2652 = 13/221 \approx 0.0588$.

*Question 2:* Compare this to drawing *with* replacement.

If you put the first card back, there are still 13 hearts in 52 cards for the second draw: $P(\text{second is heart} \mid \text{first was heart}) = 13/52 = P(\text{second is heart})$.

The events are independent: $P(\text{both hearts}) = (13/52) \cdot (13/52) = 169/2704 \approx 0.0625$.

Notice the difference: $0.0588$ vs. $0.0625$. Removing the first card changes the odds for the second draw. The events are dependent.

### Common misconceptions

**Independent events are the same as mutually exclusive events.** No. In fact, independent events (where $P(A \cap B) = P(A) \cdot P(B)$ is usually nonzero) cannot be mutually exclusive (where $P(A \cap B) = 0$) unless one of them has probability 0. Two fair dice rolls are independent. Two events like "the card is a heart" and "the card is a diamond" are mutually exclusive but not independent — they are completely dependent (if one happens, the other definitely doesn't).

**Multiply when you see the word "and."** Yes, usually. But be careful: the rule is $P(A \cap B) = P(A) \cdot P(B \mid A)$. You multiply by the conditional probability of the second event given the first, not just by $P(B)$ alone.

---

## Concept 3 — Addition rule, conditional probability, and Bayes

**Cold open: The drug test dilemma**

A company tests its employees for illegal drugs. The test is 95% accurate: it correctly identifies 95% of people who use drugs and correctly clears 95% of people who don't. An employee tests positive.

Before firing them, the company asks: how confident can we be they actually use drugs?

The answer depends on the base rate — how common drug use is in the population being tested. If 1% of employees use drugs, a positive test means the employee probably doesn't (false positive is more likely). If 50% use drugs, a positive test is pretty good evidence they do.

This is conditional probability: $P(\text{actually uses drugs} \mid \text{test positive})$. It is not the same as $P(\text{test positive} \mid \text{actually uses drugs})$, which the company already knows is 95%.

### The addition rule: For OR (union)

The probability that at least one of two events occurs — that is, $A$ or $B$ or both — uses the addition rule:

$$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$

Why subtract the intersection? Because $P(A) + P(B)$ counts the outcomes in both sets twice. You must subtract those double-counted outcomes once to get the right total.

If $A$ and $B$ are mutually exclusive (so $P(A \cap B) = 0$), the rule simplifies:

$$P(A \cup B) = P(A) + P(B) \quad \text{(if mutually exclusive)}$$

**Example:** A student is applying to two colleges: A (where she has a 40% chance of admission) and B (where she has a 30% chance). Assuming independence, what is the probability she gets into at least one?

$P(A) = 0.40$, $P(B) = 0.30$, $P(A \cap B) = 0.40 \cdot 0.30 = 0.12$.

$P(\text{at least one}) = 0.40 + 0.30 - 0.12 = 0.58$.

She has a 58% chance of getting into at least one college.

### Conditional probability: Restricting the sample space

The probability of event $A$ given that event $B$ has occurred is:

$$P(A \mid B) = \frac{P(A \cap B)}{P(B)}$$

(assuming $P(B) > 0$)

The key insight: when you know $B$ has occurred, the sample space is no longer the full universe. It is restricted to the outcomes where $B$ is true. You're computing what fraction of those outcomes also have $A$ true.

**Example:** Roll a fair die. Let $B$ = "the result is even" = $\{2, 4, 6\}$. Let $A$ = "the result is less than 5" = $\{1, 2, 3, 4\}$.

The full sample space has six equally likely outcomes. But you're given that $B$ occurred, so the sample space reduces to $\{2, 4, 6\}$ — three outcomes.

Of those three outcomes, how many are also in $A$? Only 2 and 4, so two outcomes.

$P(A \mid B) = 2/3$.

Using the formula: $P(A \cap B) = P(\{2, 4\}) = 2/6 = 1/3$. $P(B) = 3/6 = 1/2$. So $P(A \mid B) = (1/3) / (1/2) = 2/3$. It matches.

### The complement rule

The complement of an event $A$ is the event "not $A$," written $A'$:

$$P(A) + P(A') = 1$$

or equivalently:

$$P(A') = 1 - P(A)$$

This is simple but powerful. Sometimes it is easier to compute the probability that something doesn't happen and subtract from 1 than to compute the probability that it does.

**Example:** A archer hits her target 75% of the time. She takes three shots. What's the probability she misses at least one?

It's easier to compute the complement: the probability she hits *all three* is $0.75^3 \approx 0.422$. So the probability she misses at least one is $1 - 0.422 = 0.578$.

### Bayes' theorem: Updating belief with evidence

Here is the formula that resolves the drug test puzzle and the medical screening puzzle:

$$P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B)}$$

This is Bayes' theorem (from Thomas Bayes, an 18th-century clergyman and mathematician). It is profound because it tells you how to update your belief about something ($A$) given new evidence ($B$).

- $P(A)$ is the **prior** — what you believed about $A$ before seeing evidence $B$.
- $P(B \mid A)$ is the **likelihood** — how probable the evidence is if $A$ is true.
- $P(B)$ is the **marginal probability** of the evidence — how likely the evidence is overall.
- $P(A \mid B)$ is the **posterior** — what you should believe about $A$ after seeing evidence $B$.

**Worked example — the mammogram revisited**

*Given:*
- Prior: $P(\text{cancer}) = 0.01$ (1% of screened women have cancer)
- Likelihood: $P(\text{positive test} \mid \text{cancer}) = 0.98$ (the test catches 98% of cancer cases)
- False positive rate: $P(\text{positive test} \mid \text{no cancer}) = 0.10$ (the test wrongly signals cancer in 10% of cancer-free women)

*Question:* A woman tests positive. What is $P(\text{cancer} \mid \text{positive test})$?

*Step 1:* Compute $P(\text{positive test})$ — the probability of a positive test regardless of whether cancer is present.

$$P(\text{positive test}) = P(\text{positive} \mid \text{cancer}) \cdot P(\text{cancer}) + P(\text{positive} \mid \text{no cancer}) \cdot P(\text{no cancer})$$

$$= 0.98 \cdot 0.01 + 0.10 \cdot 0.99 = 0.0098 + 0.099 = 0.1088$$

*Step 2:* Apply Bayes' theorem.

$$P(\text{cancer} \mid \text{positive}) = \frac{P(\text{positive} \mid \text{cancer}) \cdot P(\text{cancer})}{P(\text{positive})} = \frac{0.98 \cdot 0.01}{0.1088} = \frac{0.0098}{0.1088} \approx 0.090$$

The woman has about a 9% chance of actually having cancer.

This seems counterintuitive — the test is 98% accurate at detecting cancer. But cancer is rare. Most positive tests come from the much larger pool of cancer-free women being falsely flagged. The base rate matters.

### Working with contingency tables and tree diagrams

For complex problems with multiple stages, two tools help organize the calculation:

**Contingency tables** organize outcomes in rows and columns, making it easy to compute intersections and conditionals.

| | Test positive | Test negative | Total |
|---|---|---|---|
| Cancer | 98 | 2 | 100 |
| No cancer | 99 | 891 | 990 |
| Total | 197 | 893 | 1,000 |

This table is built from: 1,000 women screened, 1% have cancer (100), 99% don't (900). Of the 100 with cancer, 98% test positive (98) and 2% test negative (2). Of the 900 without cancer, 10% test positive (90) and 90% test negative (810).

To find $P(\text{cancer} \mid \text{positive})$: look at the "positive test" column. Of the 197 positive tests, 98 are cancer cases. So $P(\text{cancer} \mid \text{positive}) = 98/197 \approx 0.497$.

Wait, that's closer to 50%, not 9%. Let me recalculate with the numbers I gave: if 10% of cancer-free women test positive, that's 0.10 \cdot 900 = 90 false positives, not 99. So the table should be:

| | Test positive | Test negative | Total |
|---|---|---|---|
| Cancer | 98 | 2 | 100 |
| No cancer | 90 | 810 | 900 |
| Total | 188 | 812 | 1,000 |

Now $P(\text{cancer} \mid \text{positive}) = 98/188 \approx 0.521$, still roughly 50%. The discrepancy with my earlier calculation suggests I made an error — let me recompute more carefully.

Actually, $P(\text{positive}) = 98 + 90 = 188$ out of 1,000, so $P(\text{positive}) = 0.188$. Then:

$$P(\text{cancer} \mid \text{positive}) = \frac{0.98 \cdot 0.01}{0.188} = \frac{0.0098}{0.188} \approx 0.052$$

That's about 5%, which is closer to the intuition that most positive tests are false positives. The contingency table method is often clearer: it forces you to count actual outcomes rather than relying on formulas.

**Tree diagrams** organize conditional probabilities in stages. At each branch, the probabilities condition on what has already happened. Multiplying along a path gives the joint probability; summing across paths that lead to the same endpoint gives the marginal probability.

Common misconceptions

**Bayes' theorem is only for medical tests.** No. Any time you have a prior belief and new evidence, and you want to update your belief, Bayes' theorem applies. It is the mathematics of learning from data.

**P(A|B) is the same as P(B|A).** They are usually very different. $P(\text{positive} \mid \text{cancer}) = 0.98$ (very likely to test positive if you have cancer) but $P(\text{cancer} \mid \text{positive}) = 0.052$ (less likely to have cancer given a positive test). This inversion is the core of Bayes' theorem.

**If the prior is 1%, the posterior can't be more than 1%.** Wrong. Very strong evidence can flip a small prior into a substantial posterior. If a prior is 1% but you get 100 pieces of evidence that each 99% favor the alternative, the posterior can be very large.

---

## Integration — from puzzle to calculation

Return to the three puzzles we opened with. Each one requires a clear understanding of sample spaces, events, independence, and conditional probability.

**The strep test:** The child tests positive. But positive tests are common in a population where strep is rare. A contingency table of 1,000 children with sore throats, where 10% have strep, shows that a positive test has maybe a 40% chance of meaning actual strep (depending on the test's false positive rate). The pediatrician must know this to counsel the parent appropriately.

**The drug test:** An employee tests positive. But the base rate of drug use in the employee population is low. A test that is 95% accurate catches most users but also generates false positives among the 99% who don't use drugs. A single positive test is not cause for termination; a second test or a more specific test is needed.

**The mammogram:** A woman in her fifties tests positive. The test is accurate, but cancer is rare. Bayes' theorem reveals that her actual chance of having cancer is much lower than the test's accuracy would suggest. The key is distinguishing the test's accuracy (likelihood given cancer) from the post-test probability of cancer (posterior).

All three share a structure: you know how likely the evidence is given the hypothesis ($P(\text{evidence} \mid \text{hypothesis})$), but you want to know how likely the hypothesis is given the evidence ($P(\text{hypothesis} \mid \text{evidence})$). Bayes' theorem does that translation.

---

## Exercises

### Warm-up

**Exercise 3.1** *(LO: sample space and equally likely outcomes.)* A student rolls a fair, six-sided die and flips a fair coin. (a) Describe the sample space. (b) What is the probability the die shows an even number and the coin shows heads?

**Exercise 3.2** *(LO: identify events and compute probability.)* From a standard 52-card deck, one card is drawn. (a) What is the probability the card is a heart or a king? (b) What is the probability the card is not a heart?

**Exercise 3.3** *(LO: independence vs. mutually exclusive.)* Consider the events "rolling a die and getting a 3" and "flipping a coin and getting heads." (a) Are these events independent? (b) Are these events mutually exclusive? Explain your reasoning for each.

### Application

**Exercise 3.4** *(LO: multiplication rule with dependence.)* A box contains 6 red marbles and 4 blue marbles. You draw two marbles without replacement. (a) What is the probability both are red? (b) What is the probability the first is red and the second is blue?

**Exercise 3.5** *(LO: addition rule.)* A student applies to two colleges. The probability of acceptance at college A is 0.35, at college B is 0.50. Assuming independence, what is the probability the student is accepted to at least one college?

**Exercise 3.6** *(LO: conditional probability.)* In a class of 100 students, 60 are female, 40 are male. Of the females, 20 play soccer. Of the males, 15 play soccer. (a) What is the probability a randomly selected student plays soccer? (b) What is the probability a student is female given that the student plays soccer?

### Synthesis

**Exercise 3.7** *(LO: contingency table and Bayes.)* A test for a rare disease has a 99% sensitivity (correctly identifies 99% of people with the disease) and 98% specificity (correctly clears 98% of people without the disease). The disease affects 0.1% of the population. (a) Use a contingency table to find the probability a person who tests positive actually has the disease. (b) Interpret your result.

**Exercise 3.8** *(LO: tree diagram with multiple stages.)* An urn contains 5 red balls and 3 blue balls. Draw two balls, one at a time, without replacement. (a) Use a tree diagram to find the probability of drawing one red and one blue (in either order). (b) Find the probability both balls are the same color.

### Challenge

**Exercise 3.9** *(LO: integrate multiple concepts.)* A company manufactures widgets. The probability a widget is defective is 0.02. Defective widgets are caught by quality control 95% of the time. Non-defective widgets pass inspection 98% of the time. (a) If a widget fails inspection, what is the probability it is actually defective? (b) If a widget passes inspection, what is the probability it is actually non-defective?

**Exercise 3.10** *(LO: open-ended reasoning.)* Three cards are drawn from a standard deck without replacement. (a) What is the probability all three are spades? (b) What is the probability at least one is a heart? (c) If the first two cards are spades, what is the probability the third is also a spade?

---

## Chapter summary

You can now do three things you probably could not do before.

You can **construct a sample space** for an experiment and represent it as a list, a tree diagram, or a contingency table. You understand that the sample space must be exhaustive and mutually exclusive, and that probabilities of events are computed as the ratio of favorable outcomes to total outcomes (when all outcomes are equally likely).

You can **distinguish between independence and mutual exclusivity**. You know that independent events do not affect each other's probabilities, while mutually exclusive events cannot occur together. You can apply the multiplication rule correctly, adjusting for dependence.

You can **use conditional probability and Bayes' theorem to update belief in light of evidence**. You understand that a test's accuracy (likelihood given hypothesis) is different from the probability of the hypothesis given a positive test (posterior). You can build a contingency table or a tree diagram to organize data and reason through multi-stage probability problems.

The thing to watch for, going forward, is **base rates**. Intuition fails when we ignore how common something is in the population. A test that is 99% accurate is still likely to produce false positives if the condition is rare. A policy that seems 95% fair can still systematically disadvantage a minority group if applied to millions of decisions. Probability thinking—disciplined, careful, grounded in sample spaces and base rates—is your defense against being fooled by numbers.

What you should now be able to teach a friend: why a positive test doesn't necessarily mean what you think it means; the difference between independent and mutually exclusive; how to organize a probability problem so the calculation becomes straightforward.

---

## Connections forward

In Chapter 4, you will meet the random variable — a quantity that takes on values according to a probability distribution. That chapter applies the machinery you've learned here to measurable quantities: the number of heads in 10 coin flips, the number of defective items in a batch, the lifetime of a lightbulb. Probability becomes a tool for modeling data.

Chapter 7 extends this to one of the most important distributions: the binomial distribution, which counts successes across repeated independent trials. The multiplication rule you learned here — multiplying independent probabilities — is the backbone of that distribution.

And in Chapters 9 and 10, when you learn hypothesis testing, you will use probability in reverse. You'll ask: "If this assumption were true, how likely would my observed data be?" The answer comes from probability calculations like the ones you've just mastered. Hypothesis testing is conditional probability applied to scientific reasoning.

For now, the skill is this: when you see a number reported as a probability or a likelihood — a weather forecast, a medical test result, a polling prediction — you can ask the questions that let you interpret it. What is the base rate? What is the false positive rate? Is this the probability of the evidence given the hypothesis, or the probability of the hypothesis given the evidence? These questions, and the ability to work through the math to answer them, are what this chapter gives you.
---

## LLM Exercise — Chapter 3: Probability Topics (Analyze One Dataset Project)

**Project:** Analyze One Real Dataset.
**What you're building this chapter:** the probability section — conditional probabilities, contingency tables, Bayes-style reasoning on real data.
**Tool:** **Claude Code** for the computation; **Claude Project** for the section.

---

**The Prompt:**

```
Chapter 3 of my Analyze-One-Dataset project. Prior sections in
this Claude Project. Chapter 3 covered: sample space and events;
P(A) and P(A^c); the addition rule P(A∪B) = P(A) + P(B) − P(A∩B);
independence P(A∩B) = P(A)·P(B); conditional probability P(B|A) =
P(A∩B)/P(A); tree diagrams and two-way tables; Bayes-style
reasoning (base rate + likelihood → posterior).

Write the brief's "Probability Analysis" section in 400-700 words.

1. **Pick TWO categorical variables from your dataset.** They
   should plausibly be related. Example: in a sports dataset,
   "home/away" and "win/loss"; in a survey dataset, "education
   level" and "political party"; in a medical dataset,
   "smoker/non-smoker" and "disease/no disease."

2. **Build the contingency table.** Use pandas crosstab. The table
   shows joint counts of the two variables.

3. **Compute marginal probabilities.** P(variable_1 = level_A) =
   row total / grand total. Same for variable_2. These are your
   baseline rates.

4. **Compute joint probabilities.** P(A ∩ B) = cell / grand total.

5. **Compute conditional probabilities.** P(B | A) = cell / row
   total. The conditioning is what tells you whether A and B are
   related.

6. **Check independence.** If A and B were independent, P(B | A)
   = P(B). Compare your computed P(B | A) to P(B). Are they
   close? Big differences suggest dependence — which is the
   interesting case. (Chapter 11 will formally test independence
   with chi-square.)

7. **Apply Bayes' thinking.** Pick a question that requires
   inverting: "given event A occurred, how likely is event B?"
   This is often the clinically/practically important question.
   Show the math:
   P(B | A) = P(A | B) · P(B) / P(A).

End with a "What the conditional structure reveals" paragraph.
Often the most interesting finding is the gap between marginal
and conditional probabilities — that gap is the relationship
between the two variables, made visible.
```

---

**What this produces:** A 400-700 word section with a real contingency table, marginal/joint/conditional probabilities, and a Bayesian reframing of the relationship.

**How to adapt this prompt:**

- *For your own project:* The two-variable choice shapes the section. Pick variables where dependence is interesting AND defensible.
- *For ChatGPT / Gemini:* Works as written.
- *For Claude Code:* `pd.crosstab()` is the workhorse. Add `normalize='index'` for conditional probabilities by row.
- *For a Claude Project:* Append.

**Connection to previous chapters:** Chapter 2's descriptive analysis identified the variables; Chapter 3 examines their joint structure.

**Preview of next chapter:** Chapter 4 covers discrete random variables — pmfs, E(X), binomial, Poisson. You'll identify a discrete variable in your dataset and compute its expected value and SD.


---

## 🕰️ AI Wayback Machine

**Andrey Kolmogorov** was Soviet mathematician who axiomatized probability theory in 1933 — the foundation of all modern statistical reasoning.

**Run this:**

```
Who is Andrey Kolmogorov, and how does their work connect to probability we covered in this chapter? Keep it to three paragraphs. End with the single most surprising thing about their career or ideas.
```

→ Search **"Andrey Kolmogorov"** on Wikipedia.

**Now make the prompt better.** Try one of these:

- Ask it to apply Andrey Kolmogorov's framework to a small dataset you actually have.
- Add a constraint: "Answer including criticisms or limits of Andrey Kolmogorov's framework."

What changes? What gets better? What gets worse?
