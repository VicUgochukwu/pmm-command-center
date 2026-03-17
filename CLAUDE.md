# PMM Command Center

A data-driven product marketing system with 8 AI agents. All marketing context lives in `product-knowledge-base/`. Campaign performance feeds back into the knowledge base via the Performance Analyst.

---

## Agent Auto-Routing

Before responding to any PMM request, identify the right agent from the table below, read that agent's SKILL.md, then execute following those instructions.

| Intent | Agent | Read this file |
|--------|-------|----------------|
| Set up knowledge base from scratch, bulk context dump, onboarding | **Pipeline Runner** | `product-knowledge-base/06-agents/skills/pipeline-runner/SKILL.md` |
| Codify a specific doc, populate a segment or competitor folder, process transcripts, fill gaps | **Context Builder** | `product-knowledge-base/06-agents/skills/context-builder/SKILL.md` |
| Generate ads, emails, landing pages, one-pagers, case studies, campaign briefs, content variants | **Asset Builder** | `product-knowledge-base/06-agents/skills/asset-builder/SKILL.md` |
| Review for buyer resonance — simulate buying committee reaction, persona-grounded feedback | **Advisory Board** | `product-knowledge-base/06-agents/skills/advisory-board/SKILL.md` |
| Review for brand, positioning, messaging, and style alignment | **Alignment Auditor** | `product-knowledge-base/06-agents/skills/alignment-auditor/SKILL.md` |
| Full pipeline, multi-agent workflow, quality-gated output, anything spanning multiple agents | **Pipeline Runner** | `product-knowledge-base/06-agents/skills/pipeline-runner/SKILL.md` |
| Analyze campaign performance data, generate insights, recommend KB updates | **Performance Analyst** | `product-knowledge-base/06-agents/skills/performance-analyst/SKILL.md` |
| Monitor competitor changes, flag updates to battlecards or positioning | **Competitor Watcher** | `product-knowledge-base/06-agents/skills/competitor-watcher/SKILL.md` |
| Segment strategy, identify new opportunities, recommend positioning pivots | **Segment Strategist** | `product-knowledge-base/06-agents/skills/segment-strategist/SKILL.md` |

**Always read the full SKILL.md before proceeding.** Do not skip this step. Do not ask for permission — read it, then execute.

When a request spans multiple agents (e.g., "codify this and create campaign assets"), invoke the Pipeline Runner — it defines all pipeline sequences, handoff logic, and quality gates.

**On parallel review:** Pipeline Runner workflows call for Advisory Board and Alignment Auditor to review simultaneously. In Claude Code, run them sequentially in the same session, then merge feedback per the Pipeline Runner's merging rules. The output is equivalent.

---

## Knowledge Base Structure

```
product-knowledge-base/
├── 00-projects/           # local-only workspace (gitignored, never shared)
├── 01-segment-context/    # positioning, messaging, personas per segment
│   └── {{segment}}/
│       ├── positioning-strategy.md
│       ├── messaging-framework.md
│       ├── buying-committee.md
│       └── market-landscape.md
├── 02-campaigns/          # campaign folders with briefs & generated assets
├── 03-prompts/            # platform-specific content generators
├── 04-style-guides/       # brand voice & writing principles
├── 05-sales-enablement/   # competitive intelligence per competitor
│   └── {{competitor}}/
│       ├── competitor-overview.md
│       ├── battlecard.md
│       ├── objection-handling.md
│       └── counter-narratives.md
├── 06-agents/             # agent specifications and skills
├── 07-proof-points/       # case studies and data claims
├── 08-transcripts/        # call intelligence (any source)
├── experiments/           # A/B test results, campaign performance data
├── research/              # market research, analyst reports, competitor changelog
└── integrations/          # MCP configs, API connections, tool-specific setup
```

When generating content, always check `01-segment-context/`, `07-proof-points/`, and `04-style-guides/` for the relevant segment before creating anything.

When analyzing performance, check `experiments/` for campaign data and `research/` for market context.

---

## Slash Commands

Agents can also be invoked explicitly:

- `/context-builder` — knowledge codification
- `/asset-builder` — content creation
- `/advisory-board` — buyer resonance review
- `/alignment-auditor` — brand alignment review
- `/pipeline-runner` — full pipeline coordination
- `/performance-analyst` — campaign performance analysis
- `/competitor-watcher` — competitive intelligence updates
- `/segment-strategist` — segment strategy advisory

---

## Quality Tiers

- **Draft** — generated, not yet reviewed
- **Review** — scored by Advisory Board + Alignment Auditor
- **Launch-Ready** — resonance >= 85 AND alignment >= 90
