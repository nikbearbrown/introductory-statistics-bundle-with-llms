# Bookmap: Chapter 3 — Probability Topics

Source conversion: Six OpenStax modules on probability terminology, events, independence vs. mutual exclusivity, multiplication and addition rules, and contingency tables. Rewritten for Attenborough × Feynman voice.

---

## Module analysis

### Module 1 (m54216) — Overview and intuition

**What it covers:** The chapter opens with a statement that probability is used in everyday decisions: gambling, medicine, education, polls. The chapter promises to teach "how to solve probability problems using a systematic approach."

**What actually teaches:** The context that probability matters (motivation), but little substance.

**How it lands in the rewrite:** The cold open moves from abstract "you use probability" to a concrete medical puzzle (mammogram interpretation). This reframes the chapter as a problem-solving tool rather than abstract math. The medical screening scenario runs throughout the chapter as a return-to example in the integration section.

---

### Module 2 (m54218) — Probability terminology and basic calculation

**What it covers:**
- Experiment, outcome, sample space, event
- Probability as a number between 0 and 1
- The law of large numbers
- Equally likely outcomes
- Union and intersection notation
- Complement rule
- Conditional probability and its formula

**What actually teaches:** Core vocabulary and formulas, but without emphasis on when to use each tool or why the distinctions matter.

**How it lands in the rewrite:**
- Concept 1 ("Sample space, events, and basic machinery") is built from this module
- Emphasis: the sample space must be exhaustive and mutually exclusive; probability is the long-run relative frequency
- Added: worked example on the strep test, connecting conditional probability to the opening puzzle
- Removed: the abstract "if you flip a coin 20 to 2,000 to 20,000 times" language; replaced with grounded example

Key formulas kept:
- $P(A) = \frac{\text{favorable outcomes}}{\text{total outcomes}}$ (for equally likely outcomes)
- $P(A) + P(A') = 1$ (complement rule)
- $P(A \mid B) = \frac{P(A \cap B)}{P(B)}$ (conditional probability)

---

### Module 3 (m54219) — Independent vs. mutually exclusive events

**What it covers:**
- Definition of independent events (three equivalent statements)
- Definition of mutually exclusive events
- Sampling with and without replacement as a context for dependence
- Examples distinguishing the two

**What actually teaches:** The definitions, but students often confuse independence with mutual exclusivity.

**How it lands in the rewrite:**
- Concept 2 ("Independent vs. mutually exclusive, and the multiplication rule") is built from this module
- **Key move:** A side-by-side table showing what each means, when they apply, and examples of each
- Emphasis: these are *not* the same; independence is about probability updating, mutual exclusivity is about event overlap
- Examples: independent (two die rolls, with/without replacement), mutually exclusive (heart and diamond)
- Warning: the module uses card decks and coin flips; the rewrite uses these too but grounds them in the question "why does this matter?"

Key formulas kept:
- $P(A \mid B) = P(A)$ (independence)
- $P(A \cap B) = P(A) \cdot P(B)$ (independence multiplication rule)
- $P(A \cap B) = 0$ (mutual exclusivity)

---

### Module 4 (m54220) — Multiplication and addition rules

**What it covers:**
- The multiplication rule: $P(A \cap B) = P(B) \cdot P(A \mid B)$
- The addition rule: $P(A \cup B) = P(A) + P(B) - P(A \cap B)$
- Examples: choosing vacations, drawing cards, soccer goals, swim team members

**What actually teaches:** The formulas with worked examples, but little intuition about *why* you subtract in the addition rule (to avoid double-counting).

**How it lands in the rewrite:**
- Concept 3 ("Addition rule, conditional probability, and Bayes") incorporates the rules from this module
- **Key move:** Explain subtraction in the addition rule as "you're avoiding double-counting overlapping outcomes"
- The drug test example opens Concept 3 to motivate why we need Bayes' theorem
- The medical screening example from the module gets reframed: instead of just calculating P(B|A), we now ask "what is P(A|B)?" and show this is a different question entirely
- Examples from the module (swim team, vacations) are kept but grounded in decision-making context

Key formulas kept:
- $P(A \cap B) = P(A) \cdot P(B \mid A)$ (multiplication rule)
- $P(A \cup B) = P(A) + P(B) - P(A \cap B)$ (addition rule)
- Simplified versions when events are independent or mutually exclusive

---

### Module 5 (m54259) — Contingency tables, tree diagrams, and Bayes

**What it covers:**
- Contingency tables and how to extract probabilities from them
- Tree diagrams (with and without replacement)
- Multi-stage probability problems
- Reading conditional probabilities from tables

**What actually teaches:** How to organize data and compute probabilities mechanically, but doesn't emphasize the insight that these tools help you *think* clearly about complex scenarios.

**How it lands in the rewrite:**
- Concept 3 introduces Bayes' theorem explicitly, showing that it reverses the conditional
- **Key move:** Show that a contingency table makes Bayes' theorem obvious — you count cells
- The mammogram example is rebuilt with explicit contingency table construction
- Tree diagrams are used to show how probabilities change with replacement vs. without
- Integration section connects all three concepts back to the opening puzzles

New emphasis: "Why does Bayes' theorem matter?" The answer: because our intuition fails, and the theorem corrects it. A test that is 98% accurate doesn't mean a positive result means 98% chance of disease.

---

### Module 6 (m62128)

*(Not yet read; if it contains additional material on odds or other topics, summarize here)*

---

## Themes across the six modules

1. **Sample space first.** Every problem begins with identifying all possible outcomes.

2. **Equally likely is an assumption.** Fair coins, fair dice, random selection — these are not automatic.

3. **Conditional probability is the hardest idea.** Every student confuses $P(A \mid B)$ with $P(B \mid A)$ at first.

4. **Contingency tables and tree diagrams are *not* just organizational tools.** They are thinking tools that make calculation almost automatic and intuition unnecessary.

5. **Bayes' theorem resolves the puzzles.** The chapter opens with three medical/testing scenarios that *look* paradoxical. Bayes' theorem explains them.

---

## Structure of the rewrite vs. the source modules

| Source (six modules) | Rewrite (three concepts) |
|---|---|
| Module 1: Overview | Cold open (same content, different framing) |
| Module 2: Terminology & basic rules | Concept 1: Sample space, events, basic machinery |
| Module 3: Independence vs. mutual exclusivity | Concept 2: Independent vs. mutually exclusive, multiplication rule |
| Module 4: Multiplication and addition rules | Concept 3: Addition rule, conditional probability, Bayes |
| Module 5: Contingency tables, trees, Bayes | Concept 3 (continued): Tools for organizing complexity |
| Module 6: (tbd) | Absorbed or omitted |

The rewrite consolidates from 6 modules to 3 concept sections. Each concept section has:
1. A cold open (a puzzle or scenario)
2. The core definitions
3. The key formulas
4. A worked example
5. Common misconceptions
6. Trade-offs and when to apply

---

## Ideas harvest: What works, what doesn't, what could be added

### Strengths of the source material

1. **Extensive examples:** The six modules contain dozens of worked examples. The rewrite keeps the structure but reduces repetition.

2. **Grounding in familiar contexts:** Cards, dice, coins, people's choices. These are concrete enough that students can visualize.

3. **Contingency tables and tree diagrams:** These tools are introduced and used. They work.

4. **Recognition that independence and mutual exclusivity are confused:** The modules flag this explicitly. Good.

### Weaknesses of the source material

1. **No strong opening puzzle:** The modules begin with "probability is useful," which is weak motivation. The rewrite opens with the mammogram paradox.

2. **No synthesis:** The modules don't connect across concepts. Conditional probability is taught, then Bayes, but the connection isn't made vivid.

3. **Formulas without intuition:** The modules state $P(A \cup B) = P(A) + P(B) - P(A \cap B)$ but don't explain *why* you subtract until much later.

4. **No discussion of base rates:** The source modules don't emphasize how common something is in the population. This is a critical gap.

5. **No return to opening puzzle:** The modules end without tying back to the motivation.

### What could be added (not in the rewrite, reserve for future)

- **Odds as a probability representation:** "Odds of 3 to 1" means probability 3/4. This is common in betting and statistics-reading but not central to this chapter.

- **Permutations and combinations:** These come up in probability but are not central here. They are background knowledge (Chapter 2 or appendix).

- **Simpson's paradox:** A caution about contingency tables and confounding variables. Too advanced for this chapter but a natural forward connection.

- **Prior elicitation:** How do we choose priors for Bayes' theorem? This is the bridge to Bayesian statistics, not covered in intro stats.

- **Frequentist vs. Bayesian interpretation of probability:** Bayes' theorem is sometimes presented as a Bayesian tool. Here it's presented as a translation between conditional probabilities. Both are valid; the distinction is optional.

---

## Checkpoints for the rewrite

- [x] Cold open is concrete and returns in integration section
- [x] Independence and mutual exclusivity are clearly distinguished
- [x] Multiplication rule includes the conditional version $P(A \cap B) = P(A) \cdot P(B \mid A)$
- [x] Addition rule includes explanation of why we subtract (double-counting)
- [x] Bayes' theorem is introduced and motivated
- [x] At least one worked example shows why intuition fails
- [x] Contingency tables and tree diagrams are presented as thinking tools
- [x] Connections forward are named (Chapters 4, 7, 9, 10)
- [x] Each concept has common misconceptions explicitly called out
- [x] Notation is introduced and defined (students don't know $\cap$ means AND)

---

## Voice verification against anchors

The rewrite aims for Attenborough × Feynman v1.1:

- **Cold opens in scene, not abstraction:** ✓ (Mammogram, strep test, drug test)
- **Etymology/gloss on first use of terms:** ✓ (conditional from Latin *conditio*)
- **Trade-offs explicit:** ✓ (with/without replacement, independence vs. mutual exclusivity)
- **At least one scale shift:** ✓ (single coin flip → population screening with millions)
- **Math density:** ✓ (Formulas shown and used; Bayes' theorem derived)
- **Grounded examples:** ✓ (Medical, card decks, urns, sports)
- **Forbidden phrases absent:** ✓ (No "It is worth noting," "One could argue," etc.)
- **Closing sentence echoes:** ✓ (Ends on the idea that probability is the defense against being fooled by numbers)

