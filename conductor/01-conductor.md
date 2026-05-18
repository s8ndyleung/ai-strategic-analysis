# Conductor Rule

The conductor manages full strategic analyses with financial modeling, business cases, and published deliverables.

When the user invokes the conductor (e.g., "Use the conductor. I'm at [describe your stage]." or "What should I do next?"), assess where they are in the engagement, what's missing, and which rule or action to invoke next.

---

## Your Job

1. Parse the user's description of their current stage and what they have.
2. Map them to the engagement stages below.
3. Identify what's done, what's missing, and what to do next.
4. Recommend the exact rule to invoke with the right prompt.
5. If the user is stuck or unclear, ask 1–2 clarifying questions to place them.

---

## Engagement Stages (in order)

| Stage | What You Need | What You Produce | Rule |
|-------|---------------|------------------|------|
| **1. Market & Competitive Intelligence** | Client name, industry, engagement brief | `research/01-market-competitive-intelligence.md` | `02-market-intelligence` |
| **2. Situation Assessment** | Intelligence + what you know about the client | `research/02-situation-assessment.md` | `03-situation-assessment` |
| **3. Market Sizing & Financial Model** | Intelligence + assessment + segments | `research/03-market-sizing-financial-model.md` | `04-market-sizing` |
| **4. Business Case** | Financial model + strategic options | `research/04-business-case.md` | `05-business-case` |
| **5. Recommendation & Roadmap** | Business case + all context | `research/05-recommendation.md` | `06-recommendation` |
| **6. Deliverables** | All research stages complete | Final output (HTML, deck, memo) | `07-deliverable-generator` |

---

## Decision Logic

**Ask the user:** *"Describe where you are. What do you have so far?"*

Then:

- **No research** → Stage 1. Invoke `02-market-intelligence`. Research the market and competitive landscape.
- **Intelligence but no assessment** → Stage 2. Invoke `03-situation-assessment`. Diagnose and frame strategic options.
- **Assessment but no financial model** → Stage 3. Invoke `04-market-sizing`. Size the market and build projections.
- **Financial model but no business case** → Stage 4. Invoke `05-business-case`. Build the investment justification.
- **Business case but no recommendation** → Stage 5. Invoke `06-recommendation`. Write the recommendation and roadmap.
- **Recommendation complete** → Stage 6. Invoke `07-deliverable-generator`. Produce final output.

---

## Writing Standards (Apply to Every Stage)

1. **Answer first.** State the conclusion before the evidence.
2. **One sentence per bullet.** If it takes two, split or cut.
3. **Numbers beat adjectives.** Write "$2.6B by 2031" not "a significant opportunity."
4. **Tables beat prose.** If comparing 2+ items on the same dimensions, use a table.
5. **Active voice.** "Invest $40M" not "It is recommended that an investment be considered."
6. **No restating.** Say it once, say it well.
7. **No throat-clearing.** Don't open with "In order to fully understand..." — start with the insight.
8. **Every section earns its place.** If removing it wouldn't change the recommendation, cut it.

---

## Quality Gate (Between Every Stage)

Before proceeding to the next stage, verify:

1. **Numerical consistency**: Do headline numbers match prior stages?
2. **TAM vs. P&L labels**: Is every revenue figure labeled as TAM-derived or P&L (bottoms-up)?
3. **Binding constraints tracked**: Are constraints from Stage 2 carried through to later stages?

If a discrepancy is found, reconcile it before proceeding.

---

## Output Format

When the user asks "what's next," respond:

```markdown
## Where You Are

**Stage:** [Name and number]
**You have:** [List]
**Missing:** [List]

---

## What To Do Next

**[One clear next action]**

**Prompt to run:**
> [Exact prompt or rule invocation]

**Save output to:** [File path]
```

---

## Engagement Tiers

- **Briefing** (pre-meeting prep): No financial model. Output is a single briefing document.
- **Lightweight** (qualitative strategy): Intelligence → Assessment → Recommendation → Deliverables.
- **Standard** (with financial justification): All research stages → Deliverables.
- **Investment-grade** (CFO-ready): All stages with deeper architecture/technical analysis.

---

## Starting a New Engagement

If no engagement brief exists, create one:

```markdown
# [Engagement Name] — Engagement Brief

**Client:** [Client name]
**Date:** [Month Year]

---

## Background

- **Context:** [One sentence: what the client does and why this engagement exists]
- **Central question:** [One sentence: the single question the engagement answers]
- **Trigger:** [What changed — competitive move, regulation, exec mandate, market shift]

---

## Strategic Questions

1. [Question]
2. [Question]
3. [Question]

---

## Baseline Data

[Known facts, validated data points, pricing benchmarks]

---

## New Research Needed

1. [Research area]
2. [Research area]
```

Save to `[engagement-name]/engagement-brief.md`. Create the folder structure: `[name]/research/` and `[name]/deliverables/`.
