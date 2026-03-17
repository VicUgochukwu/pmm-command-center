# PMM Command Center Agent System Design

**Purpose:** A team of specialized AI agents that amplify PMM work by automating knowledge codification, content generation, quality assurance, competitive monitoring, performance analysis, and strategic support.

---

## Architecture Principles

1. **Single Responsibility** — Each agent does ONE thing well. Builders build. Reviewers review. The Pipeline Runner coordinates.
2. **Handoff logic lives in the Pipeline Runner only** — Individual agents describe what they accept and produce. They never decide who to call next.
3. **Parallel review** — Advisory Board (resonance) and Alignment Auditor (alignment) review the same draft simultaneously. Their feedback is merged into one revision pass.
4. **Clear I/O contracts** — Every agent has well-defined inputs and outputs so handoffs are clean and predictable.
5. **Quality-tiered outputs** — Every output is tagged Draft, Review, or Launch-Ready. Nothing ships as Launch-Ready until it passes both resonance (>= 85) and alignment (>= 90) thresholds.

---

## Agent Overview

| Agent | Category | Primary Function | Key Value |
|-------|----------|-----------------|-----------|
| **Pipeline Runner** | Coordinator | Selects pipelines, orchestrates handoffs, merges feedback, gates quality | Ensures agents work as a cohesive system |
| **Context Builder** | Builder | Codifies unstructured knowledge into PMM Command Center templates | Eliminates manual template filling, preserves institutional knowledge |
| **Asset Builder** | Builder | Creates marketing content and briefs using knowledge base context | Scales content production while maintaining brand consistency |
| **Advisory Board** | Reviewer | Reviews from buyer persona perspectives (brutally honest feedback) | Proxy user testing — ensures outputs resonate before launch |
| **Alignment Auditor** | Reviewer | Reviews for alignment with positioning, messaging, and style | Prevents brand drift, ensures on-strategy outputs |
| **Performance Analyst** | Analyst | Analyzes campaign data, identifies patterns, recommends KB updates | Closes the feedback loop between market performance and strategy |
| **Competitor Watcher** | Intelligence | Monitors competitor moves, maintains changelog, flags positioning impact | Keeps competitive intel current without manual tracking |
| **Segment Strategist** | Strategy | Evaluates new segment opportunities, recommends positioning differentiation | Data-backed segment expansion and prioritization |

---

## Detailed Agent Specifications

### Pipeline Runner

**Role:** Coordinates the agent team. Selects pipelines, orchestrates handoffs, runs parallel review cycles, merges feedback, and gates quality.

**Key Capability:** The ONLY agent that contains pipeline definitions and handoff logic. All other agents focus purely on their craft.

**When Activated:** Default for higher-level goals. For single-step tasks, individual agents can be used directly.

**Key Principle:** Bias toward fewer, higher-quality outputs over many unreviewed drafts.

---

### Context Builder

**Role:** Converts unstructured PMM knowledge into structured PMM Command Center templates.

**Accepts:** Bulk dumps of mixed marketing context, unstructured documents, notes, transcripts, research, case study URLs, data claims docs, revision constraints
**Produces:** Triage report (onboarding), populated PMM Command Center template files (segment context, competitive intelligence, case studies, data claims), comprehensive gap report

**Use Cases:**
- "Set up my knowledge base with everything I've shared here" (onboarding)
- "I have a positioning doc and persona deck — populate my SMB segment folder"
- "Convert these competitive research notes into a battlecard for Competitor X"
- "Codify all the case studies from [URL] into our proof points library"
- "Here's the missing persona research — update my knowledge base" (gap-filling)

---

### Asset Builder

**Role:** Creates marketing content and briefs using PMM Command Center knowledge base as context.

**Accepts:** Segment context, campaign brief/requirements, style guide, prompt templates, brief templates, revision constraints
**Produces:** Marketing assets (ads, emails, landing pages, case studies), campaign briefs, creative briefs

**Use Cases:**
- "Generate 3 Meta ad variants for our Q1 SMB campaign targeting CFOs"
- "Create a sales email sequence for enterprise prospects"
- "Build a campaign brief for our Q2 product launch"

---

### Advisory Board

**Role:** Acts as a brutally honest buying committee to provide persona-grounded feedback on content AND codified knowledge.

**Accepts:** Content or codified knowledge to review, segment personas
**Produces:** Per-persona resonance scores (0-100), prioritized feedback, actionable recommendations

**Use Cases:**
- "Review this campaign brief from our SMB buyer personas' perspective"
- "Get Advisory Board feedback on these 3 Meta ads for CFOs"
- "Do these personas and pain points actually match what buyers care about?"

**Key Value:** Catches resonance problems at the source — whether in the knowledge base itself or in downstream content built from it.

---

### Alignment Auditor

**Role:** Reviews content and codified knowledge for alignment with PMM Command Center positioning, messaging, and style guidelines.

**Accepts:** Content or codified knowledge to review, PMM Command Center knowledge base
**Produces:** Alignment score (0-100) with sub-scores, issue list by severity, paste-ready rewrite constraints

**Use Cases:**
- "Review this ad copy for alignment with our SMB positioning"
- "Check this email against our messaging pillars"
- "Audit this segment context for completeness and internal consistency"

---

### Performance Analyst

**Role:** Analyzes campaign performance data, A/B test results, and messaging effectiveness. Identifies patterns across campaigns and recommends knowledge base updates based on validated findings.

**Accepts:** Campaign performance data, A/B test results, channel metrics, conversion data
**Produces:** Experiment reports (saved to `experiments/`), cross-campaign pattern analysis, confidence-tiered findings (Preliminary / Emerging / Validated), recommended KB updates

**Use Cases:**
- "Analyze Q1 campaign results and identify which messaging pillars performed best"
- "Compare SMB vs. enterprise conversion rates across channels"
- "What patterns do you see across our last 5 campaigns?"
- "Which proof points are driving the highest engagement?"

---

### Competitor Watcher

**Role:** Monitors and logs competitive intelligence — product launches, pricing changes, funding rounds, leadership changes, strategic shifts. Maintains the competitor changelog and flags changes that may require updates to battlecards or positioning.

**Accepts:** Competitive intelligence (news, product updates, pricing changes, analyst reports)
**Produces:** Changelog entries (saved to `research/competitor-changelog.md`), impact assessments, recommended updates to `05-sales-enablement/` materials

**Use Cases:**
- "Log these competitive updates from this week"
- "Competitor X just launched a new feature — assess impact on our positioning"
- "Update the competitor changelog with Q1 moves"
- "Flag any battlecard updates needed based on recent competitor changes"

---

### Segment Strategist

**Role:** Identifies and evaluates new segment opportunities using market research, performance data, and competitive landscape analysis. Recommends positioning differentiation across segments.

**Accepts:** Market research (from `research/`), performance data (from `experiments/`), existing segment context, competitive landscape
**Produces:** Segment opportunity assessments, prioritization recommendations, positioning differentiation analysis, new segment proposals

**Use Cases:**
- "Evaluate the healthcare vertical as a potential new segment"
- "How should we differentiate positioning between SMB and mid-market?"
- "Which segments should we prioritize for Q3 based on performance data?"
- "Recommend a positioning strategy for entering the enterprise segment"

---

## Pipelines

All pipeline definitions live in the **Pipeline Runner** skill. Summary:

### Pipeline 1: Content Creation

```
[Optional] Context Builder → Asset Builder → Advisory Board + Alignment Auditor (parallel) → Merge Feedback → Asset Builder (revise) → Quality Gate
```

### Pipeline 2: Knowledge Codification

```
Context Builder → Advisory Board + Alignment Auditor (parallel) → Merge Feedback → Context Builder (revise) → Quality Gate
```

### Pipeline 3: Full Campaign (Codify + Create)

```
Pipeline 2 (to completion) → Pipeline 1 (using codified context)
```

### Pipeline 4: Knowledge Base Onboarding

```
Context Builder (triage) → User confirms plan → Context Builder (populate all) → Advisory Board + Alignment Auditor (parallel) → Merge Feedback → Context Builder (revise) → Quality Gate → Context Builder (template cleanup + gap report)
```

Use when a new user dumps all their raw marketing context and wants the entire knowledge base set up from scratch. Includes content triage, user confirmation, template cleanup (removes placeholder files), and a comprehensive gap report saved as `_gap-report.md`.

### Pipeline 5: Quick Mode

```
[Optional] Context Builder → Asset Builder → Output (no review)
```

Skips the review cycle entirely. Use when speed matters more than polish and the user will review manually. Outputs are tagged as Draft tier.

### Pipeline 6: Performance Review

```
Performance Analyst (analyze) → Performance Analyst (identify patterns) → Context Builder (update KB) → Alignment Auditor (verify consistency)
```

Closes the feedback loop. Campaign performance data from `experiments/` feeds back into the knowledge base. Only Validated findings trigger KB updates.

### Key Design Decisions

**Parallel Review:** Advisory Board and Alignment Auditor evaluate on orthogonal axes (resonance vs. alignment). Running them simultaneously and merging feedback into a single revision pass:
- Gives the builder agent the full picture at once
- Prevents oscillation between resonance and alignment fixes
- Cuts review cycles in half vs. sequential review

**Advisory Board Reviews Knowledge:** Codified knowledge is the foundation for all downstream content. If positioning or personas don't resonate with real buyers, everything built on top will miss. Advisory Board validates this at the source.

**Feedback Merging:** The Pipeline Runner combines both reviewer reports into a unified constraint list, deduplicates overlapping feedback, resolves conflicts, and formats constraints as paste-ready instructions for the builder agent.

**Onboarding Pipeline:** New users can dump all their raw marketing context at once. The Context Builder triages inputs, identifies segments and competitors, presents a plan for user confirmation, populates everything in one pass, cleans up placeholder templates, and produces a comprehensive gap report. This removes the need for users to understand PMM Command Center structure before getting started.

**Templates are Disposable:** After onboarding, placeholder template folders and files are deleted. The Context Builder's skill definition contains all structural knowledge needed to create new segments, competitors, and proof points in the future — it can also reference existing populated files as examples.

**Quick Mode:** Not every output needs a full review cycle. Quick Mode lets users generate fast drafts tagged as Draft tier, with the understanding that they'll review manually before publishing.

**Performance Review Loop:** The system is data-driven. Campaign results flow back into the knowledge base through the Performance Analyst, ensuring positioning and messaging evolve based on real market feedback rather than assumptions.

---

## Quality Tiers

Every output is assigned a quality tier:

| Tier | Meaning | When |
|------|---------|------|
| **Draft** | Generated, not yet reviewed | Quick Mode output, or first pass before review |
| **Review** | Scored by Advisory Board + Alignment Auditor | After review cycle, scores below Launch-Ready thresholds |
| **Launch-Ready** | Passes both resonance >= 85 AND alignment >= 90 | After review cycle, meets both thresholds |

### Alignment Score Dimensions (Alignment Auditor)

- Positioning Alignment (0-20)
- Messaging Pillar Alignment (0-20)
- Persona Fit (0-15)
- Style & Voice Compliance (0-15)
- Claim Substantiation (0-15)
- Format & Technical Compliance (0-15)

### Iteration Limits

- Content Creation: max 3 review cycles
- Knowledge Codification: max 2 review cycles
- Knowledge Base Onboarding: max 2 review cycles

---

## Consolidated vs. Dropped Agents

The following agents from earlier designs have been consolidated into existing agents:

| Former Agent | Absorbed By | Rationale |
|-------------|-------------|-----------|
| Template Populator | Context Builder | Identical function — extracting from unstructured sources and populating templates |
| Competitive Intelligence Analyst | Context Builder | Context Builder already handles all competitive intel templates (overview, battlecard, objection handling, counter-narratives) |
| Content Optimizer | Asset Builder | Asset Builder already includes optimization, variant generation, and revision loops |
| Brief Builder | Asset Builder | Asset Builder now handles campaign brief and creative brief generation using `02-campaigns/` templates |

### Agents Added

The following agents were added to close gaps in the original system:

| Agent | Rationale |
|-------|-----------|
| **Performance Analyst** | Closes the feedback loop — without campaign data flowing back into the KB, positioning and messaging drift from market reality |
| **Competitor Watcher** | Competitive intel goes stale fast. Dedicated monitoring ensures battlecards and positioning stay current |
| **Segment Strategist** | Net-new segment identification and cross-segment positioning differentiation require dedicated strategic analysis |

---

## Technical Architecture

### Agent Structure

Each agent is defined in `product-knowledge-base/06-agents/skills/` and works in both **Cursor** (as Skills in `.cursor/skills/`) and **Claude Code** (as slash commands in `.claude/commands/`). Each agent spec includes:
- Clear I/O contract (what it accepts and produces)
- Role definition and capabilities
- Workflow and methodology
- Quality checklist
- NO handoff logic (that lives only in the Pipeline Runner)

### Knowledge Base Integration

Agents reference the `product-knowledge-base/` structure:
- `01-segment-context/` — Segment positioning, messaging, personas, market landscape
- `02-campaigns/` — Campaign folders with briefs, assets, and `{{campaign-template}}/`
- `03-prompts/` — Platform-specific content generators
- `04-style-guides/` — Writing principles and voice guidelines
- `05-sales-enablement/` — Competitive intelligence templates
- `07-proof-points/` — Case studies (approved quotes, metrics, competitive switch context) and data claims (substantiated proof points with sources and status)
- `experiments/` — A/B test results, campaign performance data (Performance Analyst reads/writes)
- `research/` — Market research, analyst reports, competitor changelog (Competitor Watcher writes, Segment Strategist reads)
- `integrations/` — Tool integration configs and setup guides

---

## Success Metrics

- **Time Saved:** Reduction in manual template filling and content creation
- **Resonance:** Advisory Board scores (buyer perspective) per persona
- **Alignment:** Alignment Auditor scores (PMM Command Center alignment)
- **First-Draft Quality:** Percentage of outputs that pass quality gate on first review cycle
- **Coverage:** Percentage of PMM Command Center templates populated
- **Feedback Loop Speed:** Time from campaign completion to knowledge base update
- **Competitive Currency:** Age of most recent competitor changelog entry
