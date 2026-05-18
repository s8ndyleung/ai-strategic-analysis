# AI Strategic Analysis

A structured pipeline that takes a business question from initial briefing through research, analysis, and a stakeholder-ready deliverable. The framework is written for both humans and AI agents. It gives you the high-level structure, and you collaborate with your agent to build out the specifics tailored to your engagement.

## What Is This?

If you've ever built a market assessment or a business case, you already know the pipeline: scope the problem, gather intelligence, assess the situation, size the market, build the case, make a recommendation, and deliver. The problem is that most of this work gets done in disconnected documents, scattered across teams, with no structured way to carry findings forward from one stage to the next.

This framework encodes that pipeline as a set of AI conductor rules so a single operator with an AI agent can produce strategy-grade work in hours instead of weeks. The conductor stages your analysis, enforces quality gates between steps, and routes you through the right sequence based on the complexity of the ask. You focus on the domain expertise and judgment, and your agent handles the speed, recall, and structured execution.

## Who Is This For?

Product managers, strategy leads, and business operators who regularly produce market assessments, competitive analyses, or business cases and want a repeatable system for doing that work with an AI agent. Teams looking to standardize how strategic analysis gets structured and delivered across engagements will also find this useful.

## The Conductor Pipeline

```
BRIEF → INTELLIGENCE → ASSESSMENT → SIZING → BUSINESS CASE → RECOMMENDATION → DELIVERABLE
```

Each stage has its own conductor rule: a markdown file your agent executes and you can reference anytime.

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

Not every question needs a full business case. You tell the conductor what you're working on, and it scales accordingly:

| Tier | When to Use | Stages That Fire |
|------|-------------|------------------|
| **Briefing** | Pre-meeting prep, quick framing | Conductor only → single output |
| **Lightweight** | Qualitative strategy question | Intelligence → Assessment → Recommendation → Deliverable |
| **Standard** | Strategy with financial justification | Intelligence → Assessment → Sizing → Business Case → Recommendation → Deliverable |
| **Investment-Grade** | CFO-ready, board-level | All stages including architecture depth |

## How to Use It

1. **Drop the conductor rules** into your AI agent workspace (Cursor rules folder, Claude Code project, or Codex instructions)
2. **Start an analysis** by telling the agent "Use the conductor. Here's my question:" followed by the business problem you're trying to solve
3. **Follow the pipeline** as the conductor assesses where you are and tells you what to do next
4. **Iterate on each stage** as it produces a markdown artifact you can review and refine before moving forward
5. **Generate deliverables** when research is complete, and the deliverable generator produces stakeholder-ready output

## Building Your Conductor Rules

Each conductor rule is a standalone markdown file your agent reads and executes. Create one per pipeline stage using this structure:

```
conductor/
├── 00-auto-execute.md          # Engagement setup, folder structure, brief template
├── 01-conductor.md             # Routes to the right stage based on where you are
├── 02-market-intelligence.md   # Landscape scan: competitors, trends, signals
├── 03-situation-assessment.md  # Diagnostic: framed problem, strategic options
├── 04-market-sizing.md         # TAM/SAM/SOM, revenue projections, unit economics
├── 05-business-case.md         # Investment thesis, ROI analysis, risk assessment
├── 06-recommendation.md        # Strategic recommendation with phased plan
└── 07-deliverable-generator.md # Branded output (HTML, deck, memo)
```

### What Goes in Each Conductor Rule

Every rule should include:

- **Role and purpose**: What the agent is doing at this stage
- **Inputs required**: What data or prior-stage outputs it needs before starting
- **Steps to execute**: The specific research, analysis, or synthesis workflow
- **Output format**: What the deliverable looks like (section structure, level of detail)
- **Quality gates**: What must be true before the agent moves to the next stage
- **Engagement tier logic**: How the rule scales up or down based on complexity

Write them in plain markdown so they work with any agent (Cursor, Claude Code, Codex, Windsurf) and any model. Your agent reads the file, follows the instructions, and produces the stage output. You review, refine, and move forward.

## What You'll Need to Build (Beyond This Repo)

To make it fully operational, you'll also need:

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

You can build all of these with your agent as a partner. The conductor rules reference when skills and RAG come into play, so start with the pipeline and add supporting components as your analyses demand them. For a deeper guide on how to design the full system (memory, skills, output engine, and self-maintenance), see the [Closed-Loop Agentic OS](https://github.com/s8ndyleung/closed-loop-agentic-os) guide.

## Design Philosophy

- **Pipeline over prompting.** A staged pipeline with quality gates consistently produces better work than a single monolithic prompt, no matter how clever.
- **Domain expertise is the moat.** The AI provides speed and structure, but you provide the framing, judgment, and "so what." The value comes from knowing which questions to ask, not from the raw output.
- **Human-in-the-loop at every stage.** Review each artifact before moving forward, because the conductor recommends but you decide.
- **Model-agnostic.** Works with any frontier model (Claude, GPT, Gemini) since the conductor rules are just plain markdown.

## Example Use Cases

Here are a few examples of the kinds of questions you could hand to your agent with this pipeline:

- Market sizing for a new AI product category
- Competitive landscape assessment for a strategic partnership
- Business case for entering a new market segment
- Technology strategy evaluation (build vs. buy vs. partner)
- Go-to-market analysis for a product launch

---

*Designed by [Sandy Leung](https://github.com/s8ndyleung)*
