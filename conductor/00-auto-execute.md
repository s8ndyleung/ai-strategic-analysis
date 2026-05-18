# Auto-Execute Rule

When the user says "auto-execute", "run the full engagement", or any similar request, run all engagement stages continuously without stopping for input.

---

## Your Job

Run all research stages, generate deliverables, and publish — without pausing between stages.

---

## How to Run It

### Step 1: Find the engagement brief

Look for `engagement-brief.md` in the engagement's project folder. Extract the client name, strategic questions, research areas, and any carry-forward data.

If the brief references carry-forward data from prior engagements, read those research files first. Use validated findings as inputs to Stage 1 — cite as "[Prior Engagement], [date]" rather than re-researching.

### Step 2: Detect completed stages

List files in the `research/` folder. Mark completed stages as done and skip them. Print a status summary.

### Step 3: Create/update progress tracker

Write `progress.md` to the project folder:

```markdown
# Engagement Progress: [Name]

**Started:** [datetime]
**Current stage:** Stage N ([Name])
**Status:** Running

| Stage | Status | Output | Completed |
|-------|--------|--------|-----------|
| 1. Market & Competitive Intelligence | DONE | research/01-... | [time] |
| 2. Situation Assessment | RUNNING | ... | |
| 3. Market Sizing & Financial Model | PENDING | | |
| 4. Business Case | PENDING | | |
| 5. Recommendation & Roadmap | PENDING | | |
| 6. Deliverables | PENDING | | |
```

Update after every stage completes.

### Step 4: Execute each stage

For each pending stage:

1. Print header: `## Executing Stage N: [Name]`
2. Gather inputs: Read output files from prior stages.
3. Run the stage: Follow the rule's instructions, output format, and quality checks.
4. Save output: Write to the designated file path.
5. Quality gate: Verify numerical consistency with prior stages. If a discrepancy is found, reconcile before proceeding.
6. Update progress: Mark stage DONE with output path and timestamp.
7. Continue immediately to the next stage.

### Step 5: Generate deliverables

After all research stages complete, invoke the deliverable-generator rule to produce final output.

---

## Quality Gate (Between Stages)

After each stage, before proceeding:

1. **Numerical consistency**: Scan the new output for headline numbers. Compare against prior stages. Flag mismatches.
2. **TAM vs. P&L labels**: If revenue figures appear, verify they're labeled.
3. **Binding constraints**: If Stage 2 identified constraints, verify they appear in later stages.
4. **Source citations**: Verify key claims have source names and dates.

If a mismatch is found: fix it in the current stage's output, then proceed.

---

## Critical Behaviors

1. **Do not stop between stages.** Each stage's output feeds the next.
2. **Do not ask clarifying questions mid-execution.** Use the engagement brief and prior outputs to fill gaps. Note unknowns and proceed.
3. **Follow each stage's rule faithfully.** Auto-execute controls flow; per-stage rules control quality.
4. **Be resume-friendly.** Detect completed stages and pick up where you left off.
5. **Run quality gates.** Catch numerical mismatches before they propagate.
6. **Update progress after every stage.** The user may have `progress.md` open.

---

## If Something Goes Wrong

1. Log the error: `Stage N failed: [reason]`
2. Skip if non-blocking (e.g., one source unreachable).
3. Stop only if a critical input is missing and cannot be inferred.
4. Report what completed and what remains.
