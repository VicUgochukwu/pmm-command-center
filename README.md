# PMM Command Center

*A data-driven product marketing system where campaign performance feeds back into your knowledge base, so every asset you create is informed by what actually worked.*

---

## Why This Exists

Marketing teams generate a lot of content. Very few close the loop. You launch a campaign, measure results, then start the next campaign from scratch — or worse, from gut feel and whatever the last person remembers working.

PMM Command Center fixes this by treating your marketing knowledge base as a living system. Eight AI agents handle everything from structuring your raw strategy docs to generating campaign assets to reviewing them against your brand standards. But the real differentiator is what happens *after* launch: performance data flows back into the knowledge base, so your positioning, messaging, and competitive intelligence evolve based on real-world results — not just opinion.

The feedback loop is the product. Everything else is infrastructure to make it work.

---

## The System

**Eight agents, one knowledge base, closed-loop performance tracking.**

| Agent | What It Does |
|-------|-------------|
| **Context Builder** | Codifies unstructured docs into structured knowledge base templates |
| **Asset Builder** | Creates marketing content grounded in your knowledge base context |
| **Advisory Board** | Reviews content from buyer persona perspectives — scores for resonance |
| **Alignment Auditor** | Reviews for positioning, messaging, and style guide alignment |
| **Pipeline Runner** | Coordinates multi-agent workflows, gates quality, manages handoffs |
| **Performance Analyst** | Ingests campaign data, generates insights, recommends KB updates |
| **Competitor Watcher** | Monitors competitor changes, flags what needs updating |
| **Segment Strategist** | Strategic segment advisory — identifies opportunities, recommends pivots |

You don't manage these agents directly. Describe what you need, and the system routes to the right agent (or chains several together in a pipeline).

### Pipelines

- **Content Creation** — Asset Builder drafts, Advisory Board + Alignment Auditor review in parallel, revise, quality gate
- **Knowledge Codification** — Context Builder structures, dual review, refine, quality gate
- **Full Campaign** — Codification pipeline feeds into content creation pipeline
- **KB Onboarding** — Triage your raw docs, confirm the plan, populate, review, gap report
- **Quick Mode** — Asset Builder generates draft-tier output, no review (for low-stakes content)
- **Performance Review** — Performance Analyst ingests campaign data, generates insights, recommends KB updates

### Quality Tiers

Quality scoring is contextual, not a fixed rubric. But the general gates:

- **Draft** — Generated, not yet reviewed
- **Review** — Scored by Advisory Board + Alignment Auditor
- **Launch-Ready** — Resonance >= 85 AND alignment >= 90

---

## How the Feedback Loop Works

1. **Build your knowledge base.** Share your positioning docs, persona decks, competitive research, case studies. The Context Builder structures everything. The Advisory Board and Alignment Auditor review it.

2. **Generate campaign assets.** Ask for ads, emails, landing pages, battlecards. The Asset Builder pulls from your structured knowledge base — real positioning, real proof points, real brand voice.

3. **Launch and measure.** Run your campaigns. Collect performance data.

4. **Feed results back in.** Share campaign performance data with the Performance Analyst. It identifies what messaging resonated, which segments responded, what fell flat — and recommends specific updates to your knowledge base.

5. **Knowledge base improves.** Updated positioning and messaging inform the next round of content. Each cycle gets sharper.

This is what makes PMM Command Center different from a template library. Templates are static. This system learns.

---

## What's Inside

```
product-knowledge-base/
├── 00-projects/           # Local-only workspace (gitignored)
├── 01-segment-context/    # Positioning, messaging, personas per segment
│   └── {{segment}}/
│       ├── positioning-strategy.md
│       ├── messaging-framework.md
│       ├── buying-committee.md
│       └── market-landscape.md
├── 02-campaigns/          # Campaign folders with briefs & generated assets
├── 03-prompts/            # Platform-specific content generators
├── 04-style-guides/       # Brand voice & writing principles
├── 05-sales-enablement/   # Competitive intelligence per competitor
│   └── {{competitor}}/
│       ├── competitor-overview.md
│       ├── battlecard.md
│       ├── objection-handling.md
│       └── counter-narratives.md
├── 06-agents/             # Agent specifications and skills
│   └── skills/
│       ├── context-builder/
│       ├── asset-builder/
│       ├── advisory-board/
│       ├── alignment-auditor/
│       ├── pipeline-runner/
│       ├── performance-analyst/
│       ├── competitor-watcher/
│       └── segment-strategist/
├── 07-proof-points/       # Case studies and verified data claims
├── 08-transcripts/        # Call intelligence (Gong, Apollo, etc.)
├── experiments/           # A/B test results, campaign performance, messaging effectiveness
├── research/              # Market research, analyst reports, competitor changelog
└── integrations/          # MCP configs, API connections, tool-specific setup
```

The `experiments/` folder is where performance data lives — A/B test results, campaign metrics, messaging effectiveness studies. This is what the Performance Analyst reads to close the feedback loop.

---

## Quick Start

1. **Fork the repo** and clone it locally (or connect it to Claude via GitHub)
2. **Gather your docs** — positioning, personas, competitive research, case studies, brand guidelines. Messy is fine. See the [preparation checklist](./SETUP-GUIDE.md#before-you-start-gather-your-docs)
3. **Set up your tool** — follow the [Setup Guide](./SETUP-GUIDE.md) for Claude Code or Cursor (~10 minutes)
4. **Dump your context** — share your docs and say "Set up my knowledge base with everything I've shared here"
5. **Review the output** — check the structured files, adjust what doesn't match your strategy, fill gaps from the gap report
6. **Start creating** — ask for campaign assets, battlecards, emails, landing pages. Everything is grounded in your actual strategy
7. **Close the loop** — after campaigns run, feed performance data back in with the Performance Analyst

**[Read the full Setup Guide →](./SETUP-GUIDE.md)**

---

## Choose Your Tool

| | **Claude Code** *(recommended)* | **Cursor** |
|---|---|---|
| **Best for** | Most people. Chat-based, no coding needed. | People who want to see the file tree and edit alongside the AI. |
| **Setup** | Fork the repo, open it in Claude, start chatting. | Clone the repo, run one activation command, chat. |
| **Get it** | [Claude →](https://claude.ai) / [Desktop →](https://claude.ai/download) | [Cursor →](https://cursor.sh) |

The knowledge base is plain text files. Once built, any AI tool can read it — Claude, ChatGPT, Gemini, Copilot. The agent system (routing, pipelines, review gates) runs on Claude Code and Cursor. The knowledge base works everywhere.

---

## FAQ

**How is this different from a template library?**
Templates are static. PMM Command Center is a closed-loop system — campaign performance data feeds back into your knowledge base, so your positioning and messaging evolve based on what actually works in market. Each cycle of content creation gets more effective.

**What does "data-driven" actually mean here?**
The Performance Analyst agent ingests real campaign data (A/B test results, engagement metrics, conversion data) and translates it into specific knowledge base updates. Instead of guessing why a campaign underperformed, you get evidence-based recommendations for adjusting your messaging, positioning, or targeting.

**Do I need to be technical?**
No. Claude Code works in your browser. Cursor is a desktop app. Neither requires coding experience.

**What do I need to prepare?**
Whatever marketing docs you have. The [Setup Guide](./SETUP-GUIDE.md#before-you-start-gather-your-docs) has a checklist. The system tells you exactly what's missing.

**Can my whole team use this?**
Yes. The knowledge base lives in GitHub with version history. When you update competitive positioning or feed in new performance data, everyone's AI gets the updated context. Connect teammates via Claude Projects, GitHub integration, or cloning the repo.

**What if my team uses different AI tools?**
The knowledge base is plain text files — any AI that can read files gets the same context. The agent system is built for Claude Code and Cursor, but the knowledge base works everywhere.

---

## License

[MIT License](./LICENSE). Free to use, adapt, and extend.

---

## Acknowledgments

PMM Command Center was inspired by [Product Marketing OS](https://github.com/itsebastienrankin/product-marketing-os) by Sebastien Rankin, released under the MIT License. We built on the structural foundation of that project and extended it with data-driven feedback loops, additional agents, and performance analytics capabilities.
