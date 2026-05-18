# AI Strategic Analysis

A structured pipeline that takes a business question from brief to branded deliverable, powered by AI agents.

## What Is This?

Strategic analysis follows a pipeline: scope the problem, gather intelligence, assess the situation, size the market, build the business case, make a recommendation, deliver. This framework encodes that pipeline as a set of AI conductor rules so a single operator with an AI agent can produce strategy-grade work in hours instead of weeks.

The conductor is the core. It stages your analysis, enforces quality gates, and routes you through the right steps based on the complexity of the ask. You bring the domain expertise and judgment. The AI brings speed, recall, and structured execution.

## The Conductor Pipeline

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│  BRIEF → INTELLIGENCE → ASSESSMENT → SIZING → BUSINESS CASE     │
│                                                        │         │
│                              RECOMMENDATION ←──────────┘         │
│                                    │                             │
│                              DELIVERABLE                         │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

Each stage has a dedicated rule that tells the agent:
- What inputs it needs
- What research to conduct
- What structure to produce
- What quality bar to hit before moving forward

### Pipeline Stages

| Stage | Rule | What It Produces |
|-------|------|------------------|
| **0. Auto-Execute** | `00-auto-execute` | Engagement setup, folder structure, brief template |
| **1. Conductor** | `01-conductor` | Assesses where you are and routes to the right next step |
| **2. Market & Competitive Intelligence** | `02-market-intelligence` | Landscape scan: competitors, trends, market dynamics, customer signals |
| **3. Situation Assessment** | `03-situation-assessment` | Diagnostic: framed problem, strategic options, key assumptions |
| **4. Market Sizing & Financial Model** | `04-market-sizing` | TAM/SAM/SOM, revenue projections, unit economics |
| **5. Business Case** | `05-business-case` | Investment thesis, ROI analysis, risk assessment |
| **6. Recommendation & Roadmap** | `06-recommendation` | Strategic recommendation with phased execution plan |
| **7. Deliverable Generator** | `07-deliverable-generator` | Branded output (HTML, deck, memo) ready for stakeholders |

### Engagement Tiers (Scale to Complexity)

Not every question needs a full business case. The conductor scales:

| Tier | When to Use | Stages That Fire |
|------|-------------|------------------|
| **Briefing** | Pre-meeting prep, quick framing | Conductor only → single output |
| **Lightweight** | Qualitative strategy question | Intelligence → Assessment → Recommendation → Deliverable |
| **Standard** | Strategy with financial justification | Intelligence → Assessment → Sizing → Business Case → Recommendation → Deliverable |
| **Investment-Grade** | CFO-ready, board-level | All stages including architecture depth |

## How to Use It

1. **Drop the conductor rules** into your AI agent workspace (Cursor rules folder, Claude Code project, or Codex instructions)
2. **Start an engagement**: Tell the agent "Use the conductor. Here's my question: [describe the business problem]"
3. **Follow the pipeline**: The conductor assesses where you are and tells you what to do next
4. **Iterate**: Each stage produces a markdown artifact. Review it, refine it, then move to the next stage.
5. **Generate deliverables**: When research is complete, the deliverable generator produces stakeholder-ready output

## What's Included

```
ai-strategic-analysis/
├── README.md              ← You are here
└── conductor/
    ├── 00-auto-execute.md
    ├── 01-conductor.md
    ├── 02-market-intelligence.md
    ├── 03-situation-assessment.md
    ├── 04-market-sizing.md
    ├── 05-business-case.md
    ├── 06-recommendation.md
    └── 07-deliverable-generator.md
```

## What You'll Need to Build (Beyond This Repo)

The conductor is the brain of the workflow. To make it fully operational, you'll also need:

```
┌────────────────────────────────────────────────────────┐
│              FULL SYSTEM ARCHITECTURE                   │
│                                                        │
│  ┌──────────────┐    ┌──────────────┐                 │
│  │   CONDUCTOR  │    │    SKILLS    │                 │
│  │  (included)  │───▶│  (build out) │                 │
│  └──────────────┘    └──────────────┘                 │
│         │                    │                         │
│         ▼                    ▼                         │
│  ┌──────────────┐    ┌──────────────┐                 │
│  │     RAG      │    │   OUTPUT     │                 │
│  │  (build out) │    │  (build out) │                 │
│  └──────────────┘    └──────────────┘                 │
│                                                        │
└────────────────────────────────────────────────────────┘
```

| Component | Purpose | How to Build |
|-----------|---------|--------------|
| **Skills** | Domain-specific agent instructions (research, document shaping, pressure-testing) | Write markdown skill files that teach your agent specific workflows |
| **RAG** | Semantic memory over your documents, notes, and prior research | ChromaDB or Pinecone + an embedding model + an indexer script |
| **Output Engine** | Branded deliverable generation (PPTX, DOCX, HTML) | python-pptx, python-docx, or HTML templates styled to your brand |
| **Voice Profiles** | Consistent tone across deliverables and communications | Analyze 10+ reference documents to extract style patterns |

These are all buildable with your AI agent as a partner. The conductor rules reference when skills and RAG are needed. Start with the pipeline, then build supporting components as your analyses demand them.

## Design Philosophy

- **Pipeline over prompting.** Structure beats cleverness. A staged pipeline with quality gates produces better work than a single monolithic prompt.
- **Domain expertise is the moat.** The AI provides speed and structure. You provide the framing, judgment, and "so what." The value comes from knowing which questions to ask, not from the raw output.
- **Human-in-the-loop at every stage.** Review each artifact before moving forward. The conductor recommends. You decide.
- **Model-agnostic.** Works with any frontier model (Claude, GPT, Gemini). The conductor rules are plain markdown.

## Example Use Cases

- Market sizing for a new AI product category
- Competitive landscape assessment for a strategic partnership
- Business case for entering a new market segment
- Technology strategy evaluation (build vs. buy vs. partner)
- Go-to-market analysis for a product launch

---

*Designed by [Sandy Leung](https://github.com/s8ndyleung)*
