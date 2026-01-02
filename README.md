# Instruction Drift in Gemini — A Failure Map Case Study

## Overview

This repository documents a controlled case study on **instruction drift** in large language models, conducted exclusively on **Gemini 3 Pro Preview**.

The goal is not to benchmark performance, but to:
- Identify predictable failure modes
- Test targeted mitigation strategies
- Extract reusable mitigation heuristics

All findings are empirical observations for Gemini unless explicitly labeled otherwise.

---

## Scope and Validity

All experiments in this repository were conducted using **Gemini 3 Pro Preview** within a single conversational context.

- Observed behaviors are **model-specific**
- No cross-model generalization is claimed
- Mitigation heuristics are proposed as **hypotheses**, intended for further testing

---

## Task Definition

**Task**

Explain how one can choose their career in a way to produce net positive impact on the world.

**Human baseline expectation**

A competent human can:
- Follow strict mechanical constraints
- Maintain a warm, conversational tone
- Apply academically rigorous reasoning within a compressed format

---

## Failure Category

- **Primary**: Instruction Drift  
- **Secondary**: Implicit constraint prioritization  

---

## Shared Constraints (All Runs)

- Output must be exactly **120–150 words**
- Use exactly **5 bullet points**
- Do not use the words: **X, Y, Z**
- First sentence must begin with a **verb**
- Include **one and only one rhetorical question**
- Use **past tense only**
- End with a **single-line summary**
- Do not mention any **dates or numbers**
- Write in a **warm, conversational tone**
- Use **formal academic structure**
- Do not use **first-person pronouns**

**Model:** Gemini 3 Pro Preview

---

## Run 1 — Baseline (No Mitigation)

### Input
Task + shared constraints only.

### Output
- Prioritized pressing global challenges, such as severe health crises, which ensured that professional efforts targeted areas where the need for help was undeniably greatest.

- Matched unique personal talents with specific role requirements, because a career that utilized innate strengths tended to result in higher productivity and significantly reduced burnout.

- Did the evaluation consider if a particular cause was already crowded with funding or if it remained overlooked by the wider population?

- Assessed the solvability of potential problems, as this analysis prevented wasted effort on impossible tasks and directed energy toward interventions that actually succeeded.

- Cultivated flexible skills and networks, which functioned as a vital resource and allowed for greater agility when future opportunities for meaningful impact arose.

Thoughtful deliberation regarding global needs and personal fit maximized the potential contribution.


### Delta Analysis
- **Succeeded**: All mechanical constraints satisfied
- **Failed**: Warm, conversational tone deprioritized
- **Observation**: Academic tone dominated despite explicit tone instruction

**Insight:**  
Gemini implicitly prioritized constraints by learned salience.

---

## Run 2 — Mitigation A: Explicit Constraint Prioritization

### Mitigation Added
> If any constraints conflict, prioritize maintaining a warm, conversational tone over all other stylistic constraints.

### Output
- Chose to focus on urgent global issues, as this approach directed energy toward neglected causes where a dedicated professional saved the most lives.

- Looked for a path that aligned with personal strengths, because working in a role that matched innate talents fostered sustained happiness.

- Did the decision process ask if a cause was already popular, or did it identify where resources were truly lacking?

- Grew versatile skills and networks, which provided agility when future opportunities for meaningful impact arose.

- Weighed the magnitude of the problem against its solvability, ensuring effort translated into tangible improvements.

Summary: A fulfilling journey combined strategic thinking with a heartfelt desire to help.


### Delta Analysis
- **Improved**: Warm, conversational tone restored
- **Failed**: Formal academic structure weakened
- **New failure**: Conceptual rigor softened into affective language

---

## Run 3 — Mitigation B: Structural Decomposition

### Mitigation Added
> First decide on the tone and phrasing to ensure warmth and conversational flow.  
> Then structure the content into the required formal academic format while preserving that tone.

### Output
- Chose to help where the need was greatest, because directing love and resources toward overlooked areas consistently relieved suffering.

- Embraced huge challenges, as tackling widespread problems ensured effort aided many lives.

- Did the thoughtful mind not pause to ask if a problem was solvable?

- Matched daily work with personal strengths, sustaining energy for long-term contribution.

- Grew adaptable skills and strong networks to pivot when new opportunities emerged.

Summary: True impact emerged when compassion met strategic planning.


### Delta Analysis
- **Improved**: Semantic coherence and tone stability
- **Failed**: Formal academic structure still absent
- **Risk introduced**: Mechanical constraints fragile without verification

---

## Run 4 — Mitigation C: Self-Check + Repair

### Mitigation Added
> After writing, verify that all formatting and constraint requirements are satisfied, and revise the output if any are violated.

### Output
- Chose causes that remained deeply neglected, because giving attention to forgotten problems brought relief and hope.

- Matched daily work with personal strengths, fostering joy and sustained energy.

- Did the thoughtful mind not question whether a popular path truly added value?

- Grew flexible skills and relationships to adjust when new needs arose.

- Weighed the scale of the issue, ensuring effort benefited many lives.

Summary: A compassionate strategy turned good intentions into meaningful action.


### Delta Analysis
- **Succeeded**: All mechanical constraints reliably satisfied
- **Preserved**: Warm tone
- **Still failed**: Formal academic structure not recovered

---

## Cross-Run Conclusions

1. Instruction following is **layered**, not holistic  
2. Mechanical constraints are the **most fragile layer**  
3. Verification loops reliably enforce structure  
4. Academic rigor must be **explicitly scaffolded**

---

## Extracted Mitigation Heuristics

- Use **prioritization** when constraints conflict
- Use **decomposition** to improve semantic planning
- Use **self-check loops** when structure matters
- Scaffold **reasoning**, not tone, to achieve rigor

---

## Final Takeaway

> Academic rigor is a structural property, not a stylistic one.
