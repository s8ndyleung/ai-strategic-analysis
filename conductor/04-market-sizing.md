# Market Sizing & Financial Model Rule

When the user invokes this rule, produce an integrated market sizing and financial model with sensitivity analysis.

---

## Your Job

1. Define and size the market using TAM/SAM/SOM with both top-down and bottom-up methods.
2. Segment the market and prioritize segments.
3. Build a revenue model with explicit assumptions per segment.
4. Build a cost model covering CapEx, OpEx, and variable costs.
5. Run five-scenario sensitivity analysis with probability-weighted expected value.
6. Reconcile TAM and P&L figures explicitly — never conflate them.

---

## Output Format

Save to `research/03-market-sizing-financial-model.md`.

```markdown
# Market Sizing & Financial Model: [Opportunity Name]

## Market Definition

**What we're sizing:** [Specific market, not the broader industry]
**Unit of measure:** [e.g., annual revenue, customers, seats]
**Geographic scope:** [e.g., Global, NA + EU]
**Time horizon:** [e.g., 2026–2031]

---

## TAM — Total Addressable Market

### Top-Down

| Input | Value | Source |
|-------|-------|--------|
| [Total industry revenue] | ... | [Source, Date] |
| [Relevant segment %] | ... | [Source] |
| **TAM (top-down)** | **...** | |

### Bottom-Up

| Input | Value | Source |
|-------|-------|--------|
| [Total potential customers] | ... | [Source] |
| [Average revenue per customer] | ... | [Pricing model] |
| **TAM (bottom-up)** | **...** | |

### Reconciliation

[Do they converge? If not, explain the gap and which is more reliable.]

**TAM estimate:** [$X–Y range]

---

## SAM and SOM

**SAM (Serviceable Addressable Market):** [TAM filtered by what you can actually reach]
**SOM (Serviceable Obtainable Market):** [SAM filtered by realistic capture rate]

| Filter | Value | Rationale |
|--------|-------|-----------|
| Geographic reach | ... | ... |
| Channel coverage | ... | ... |
| Product fit | ... | ... |
| **SAM** | **...** | |
| Competitive capture rate | ...% | [Benchmark or assumption] |
| **SOM** | **...** | |

---

## Market Segmentation

| Segment | Size | Growth Rate | Priority | Rationale |
|---------|------|-------------|----------|-----------|
| ... | ... | ... | High/Med/Low | ... |

---

## Revenue Model

### Assumptions

| Assumption | Value | Source / Rationale |
|------------|-------|-------------------|
| [Pricing per unit] | ... | ... |
| [Adoption curve] | ... | ... |
| [Churn rate] | ... | ... |

### Revenue Ramp (P&L — Bottoms-Up)

| Year | Customers | Revenue | Growth |
|------|-----------|---------|--------|
| Y1 | ... | ... | — |
| Y2 | ... | ... | ...% |
| Y3 | ... | ... | ...% |

*Note: These are P&L projections (bottoms-up), not TAM figures.*

---

## Cost Model

| Category | Y1 | Y2 | Y3 | Notes |
|----------|----|----|----| ----- |
| CapEx | ... | ... | ... | ... |
| OpEx | ... | ... | ... | ... |
| Variable | ... | ... | ... | ... |
| **Total** | ... | ... | ... | |

---

## Five-Scenario Sensitivity Analysis

| Scenario | Probability | Y3 Revenue | Y3 Profit | Key Driver |
|----------|-------------|------------|-----------|------------|
| Bull | ...% | ... | ... | [What goes right] |
| Optimistic | ...% | ... | ... | ... |
| Base | ...% | ... | ... | ... |
| Conservative | ...% | ... | ... | ... |
| Bear | ...% | ... | ... | [What goes wrong] |
| **Expected Value** | 100% | **...** | **...** | Probability-weighted |

---

## Key Risks to the Model

| Risk | Impact | Likelihood | Mitigation |
|------|--------|-----------|------------|
| ... | ... | ... | ... |
```

---

## Quality Standards

- **Label every number.** TAM-derived or P&L (bottoms-up) — never mix without explicit labels.
- **Source assumptions.** Every input to the model needs a source or explicit "assumption" flag.
- **Cross-validate.** Top-down and bottom-up TAM should converge within 2x. If not, explain why.
- **Be honest about confidence.** Flag assumptions that could swing the model by >20%.
