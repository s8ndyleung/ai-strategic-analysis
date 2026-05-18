# Business Case Rule

When the user invokes this rule, produce a decision-ready business case with cross-reference validation and five-scenario risk assessment.

---

## Your Job

1. Frame the investment thesis — why this investment, why now, what's the return.
2. Cross-reference every number against the market sizing and financial model — flag discrepancies.
3. Quantify the investment required vs. expected returns with clear time horizons.
4. Compare against alternatives including doing nothing.
5. Assess risks with five-scenario probability-weighted returns.
6. Identify binding constraints that must be resolved for the case to hold.
7. Produce a document a CFO or investment committee can act on.

---

## Output Format

Save to `research/04-business-case.md`.

```markdown
# Business Case: [Opportunity Name]

## Cross-Reference Validation

*Before proceeding, verify every headline number traces to the financial model.*

| Figure | Value | Source Document | Verified? |
|--------|-------|-----------------|-----------|
| [TAM] | $... | market-sizing.md, Section X | ✓ / ✗ |
| [Year 3 Revenue (P&L)] | $... | market-sizing.md, Revenue Ramp | ✓ / ✗ |
| [Investment required] | $... | market-sizing.md, Cost Model | ✓ / ✗ |

**Discrepancies found:** [List any, with explanation]

---

## Investment Thesis

**[One sentence: why invest, in what, for what return, over what time.]**

---

## The Opportunity

| Metric | Value | Source |
|--------|-------|--------|
| TAM | $... | Market sizing |
| SOM (Year 3) | $... | Market sizing |
| Revenue (Year 3, P&L) | $... | Financial model |
| Gross margin | ...% | Cost model |

---

## Investment Required

| Category | Amount | Timeline | Notes |
|----------|--------|----------|-------|
| [Category 1] | $... | ... | ... |
| [Category 2] | $... | ... | ... |
| **Total** | **$...** | | |

---

## Returns Analysis

| Metric | Year 1 | Year 2 | Year 3 | Year 5 |
|--------|--------|--------|--------|--------|
| Revenue (P&L) | ... | ... | ... | ... |
| Costs | ... | ... | ... | ... |
| Net profit | ... | ... | ... | ... |
| Cumulative ROI | ... | ... | ... | ... |

**Payback period:** [X months/years]

---

## Alternative Comparison

| Option | Investment | Year 3 Revenue | ROI | Risk | Recommendation |
|--------|-----------|----------------|-----|------|----------------|
| Recommended | ... | ... | ... | ... | ✓ |
| Alternative A | ... | ... | ... | ... | |
| Do nothing | $0 | ... | ... | ... | |

---

## Risk Assessment (Five Scenarios)

| Scenario | Probability | Year 3 Outcome | Key Driver |
|----------|-------------|----------------|------------|
| Bull | ...% | ... | ... |
| Optimistic | ...% | ... | ... |
| Base | ...% | ... | ... |
| Conservative | ...% | ... | ... |
| Bear | ...% | ... | ... |
| **Expected Value** | 100% | **...** | |

---

## Binding Constraints

| Constraint | Status | If Unresolved |
|------------|--------|---------------|
| ... | ... | [What breaks] |

---

## Go / No-Go Criteria

- [ ] [Condition 1 that must be true]
- [ ] [Condition 2]
- [ ] [Condition 3]

---

## Recommendation

**[One sentence: invest / don't invest / invest conditionally — with the key condition.]**
```
