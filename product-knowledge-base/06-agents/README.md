# PMM Command Center Agent System

A team of specialized AI agents that amplify PMM work by automating knowledge codification, content generation, quality assurance, competitive monitoring, performance analysis, and strategic support.

## Quick Start

The agents are supported in both **Cursor** and **Claude Code**. See the relevant setup section below, then use the example prompts to get started.

### Example Usage

**Knowledge Base Onboarding (new users):**
```
"Set up my knowledge base with everything I've shared here"
```

**Knowledge Codification:**
```
"I have a positioning doc and persona deck — populate my SMB segment folder"
```

**Content Generation:**
```
"Generate 3 Meta ad variants for our Q1 SMB campaign targeting CFOs"
```

**Gap Filling:**
```
"Here's the missing persona research — update my knowledge base"
```

**Full Pipeline:**
```
"Here are my notes on the mid-market segment — codify it and create campaign assets"
```

**Quick Mode:**
```
"Quick mode — generate LinkedIn ads for our enterprise segment"
```

**Performance Review:**
```
"Review performance data from our Q1 SMB campaign and update the knowledge base"
```

## Available Agents

### Context Builder (Builder)
**Purpose:** Converts unstructured PMM knowledge into structured PMM Command Center templates

**Use When:**
- You're setting up your knowledge base for the first time (onboarding — dump everything)
- You have positioning docs, persona decks, or research to codify
- You need to populate segment context folders
- You want to create competitive intelligence files
- You have meeting notes or transcripts to structure
- You want to codify published case studies from a URL into structured proof point files
- You need to organize data claims with sources, strength ratings, and status tracking
- You're filling gaps identified in your gap report

### Asset Builder (Builder)
**Purpose:** Creates marketing content and briefs using PMM Command Center knowledge base as context

**Use When:**
- You need ads, emails, landing pages, or case studies
- You want to create campaign or creative briefs
- You want content aligned with segment positioning
- You need platform-specific content (Meta, LinkedIn, Google SEM)
- You need multiple variants for A/B testing

### Advisory Board (Reviewer)
**Purpose:** Acts as a brutally honest buying committee to validate that content AND codified knowledge resonate with real buyers

**Use When:**
- You want to know if content will resonate before going to market
- You need buyer perspective on campaign briefs or creative assets
- You want to validate that personas, positioning, or messaging match buyer reality
- You need proxy user testing before spending budget

### Alignment Auditor (Reviewer)
**Purpose:** Reviews content and knowledge for alignment with PMM Command Center positioning, messaging, and style guidelines

**Use When:**
- You want to check content alignment before publishing
- You need to validate brand consistency
- You want to audit segment context for completeness
- You're reviewing content from other team members

### Pipeline Runner (Coordinator)
**Purpose:** Coordinates the agent team into pipelines with parallel review, feedback merging, and quality gates

**Use When:**
- You have a higher-level goal that involves multiple agents
- You want quality-gated outputs (reviewed, revised, scored)
- You're running a full campaign workflow

### Performance Analyst (Analyst)
**Purpose:** Analyzes campaign performance, A/B test results, and messaging effectiveness to feed data-driven insights back into the knowledge base

**Use When:**
- You have campaign performance data to analyze
- You want to identify which messaging pillars are outperforming
- You need cross-campaign pattern analysis
- You want to update the knowledge base based on validated findings

### Competitor Watcher (Intelligence)
**Purpose:** Monitors and logs competitive moves — product launches, pricing changes, funding rounds, strategic shifts — into the research layer

**Use When:**
- You have new competitive intelligence to log
- You want to update the competitor changelog
- You need to flag competitive changes that affect positioning or battlecards
- You want to trigger updates to sales enablement materials

### Segment Strategist (Strategy)
**Purpose:** Identifies and evaluates new segment opportunities using market research, performance data, and competitive landscape analysis

**Use When:**
- You're considering entering a new market segment
- You want to evaluate segment viability and prioritization
- You need to differentiate positioning across segments
- You want data-backed recommendations on segment expansion

## How Agents Work Together

The Pipeline Runner coordinates all handoffs. Individual agents focus on their craft.

### Content Creation Pipeline
1. **(Optional) Context Builder** — Codifies raw context if needed
2. **Asset Builder** — Creates draft assets
3. **Advisory Board + Alignment Auditor** — Review the same draft simultaneously (parallel)
4. **Pipeline Runner** — Merges feedback into unified constraint list
5. **Asset Builder** — Revises with merged constraints
6. **Quality Gate** — Ship when resonance >= 85 AND alignment >= 90

### Knowledge Codification Pipeline
1. **Context Builder** — Populates templates from raw inputs
2. **Advisory Board + Alignment Auditor** — Review simultaneously (parallel)
3. **Pipeline Runner** — Merges feedback
4. **Context Builder** — Refines based on merged feedback
5. **Quality Gate** — Ship when thresholds met

### Full Campaign Pipeline
1. Run Knowledge Codification to completion
2. Run Content Creation using the codified context

### Knowledge Base Onboarding Pipeline
1. **Context Builder** — Triages all shared context (classifies content, identifies segments/competitors)
2. **Pipeline Runner** — Presents triage plan to user for confirmation
3. **Context Builder** — Populates all templates in one pass
4. **Advisory Board + Alignment Auditor** — Review simultaneously (parallel)
5. **Pipeline Runner** — Merges feedback
6. **Context Builder** — Refines, then cleans up placeholder template files
7. **Quality Gate** — Ship when thresholds met
8. **Context Builder** — Produces comprehensive gap report (`_gap-report.md`)

### Quick Mode Pipeline
Skips the review cycle for speed. Use when you need fast output and will review manually.
1. **Context Builder** (optional) — Codifies raw context if needed
2. **Asset Builder** — Creates assets in a single pass
3. No review cycle — output delivered directly

### Performance Review Pipeline
Data-driven feedback loop that updates the knowledge base based on real-world results.
1. **Performance Analyst** — Analyzes campaign data from `experiments/`
2. **Performance Analyst** — Identifies patterns and validated findings
3. **Context Builder** — Updates segment context, messaging, and proof points based on validated findings
4. **Alignment Auditor** — Verifies updates maintain consistency across the knowledge base

### Gap-Filling Follow-up
When user returns with missing context referenced in the gap report:
1. **Context Builder** — Fills specific gaps with new context
2. **Advisory Board + Alignment Auditor** — Targeted review of updated sections only
3. **Context Builder** — Updates `_gap-report.md` (marks resolved, surfaces remaining)

### Proof Points Integration
Asset Builder automatically checks `07-proof-points/case-studies/` for approved quotes and `07-proof-points/data-claims/data-claims.md` for substantiated claims when generating content. Alignment Auditor verifies that any claims or quotes in generated content trace back to these files.

### Why Parallel Review?
Advisory Board and Alignment Auditor evaluate on different axes — buyer resonance vs. PMM Command Center alignment. Running them in parallel and merging their feedback means the builder agent gets the full picture in one pass, preventing the oscillation that happens with sequential review.

## Agent Specifications

For detailed specifications, see:
- [Agent System Design](./AGENT-SYSTEM-DESIGN.md) — Complete system architecture
- [Pipeline Runner Skill](./skills/pipeline-runner/SKILL.md) — Pipeline definitions and coordination
- [Context Builder Skill](./skills/context-builder/SKILL.md) — Knowledge codification
- [Asset Builder Skill](./skills/asset-builder/SKILL.md) — Content and brief creation
- [Advisory Board Skill](./skills/advisory-board/SKILL.md) — Buyer resonance review
- [Alignment Auditor Skill](./skills/alignment-auditor/SKILL.md) — PMM Command Center alignment review
- [Performance Analyst Skill](./skills/performance-analyst/SKILL.md) — Campaign analysis and data-driven insights
- [Competitor Watcher Skill](./skills/competitor-watcher/SKILL.md) — Competitive intelligence monitoring
- [Segment Strategist Skill](./skills/segment-strategist/SKILL.md) — Segment opportunity evaluation

## Using with Claude Code

Agents load automatically — no setup required beyond connecting your repo.

1. Open [claude.ai](https://claude.ai) or the [Claude desktop app](https://claude.ai/download)
2. Connect your GitHub account (**Settings → Integrations**) and attach your forked repo
3. Start using it. Claude reads the `CLAUDE.md` at the repo root automatically and routes your requests to the right agent.

> **Using the terminal CLI?** Install with `npm install -g @anthropic-ai/claude-code`, clone the repo, and run `claude` from inside the folder. Same agent system, same auto-routing.

**How auto-routing works:** When you make a request, Claude reads `CLAUDE.md`, identifies the appropriate agent, reads that agent's `SKILL.md`, and executes. No manual configuration needed.

**Explicit invocation with slash commands:**
```
/context-builder set up my knowledge base with everything I've shared here
/asset-builder generate 3 Meta ad variants for our SMB segment targeting CFOs
/advisory-board review these LinkedIn ads for buyer resonance
/alignment-auditor check this landing page for brand alignment
/pipeline-runner run a full content creation pipeline for our enterprise campaign
/performance-analyst analyze Q1 campaign results and identify patterns
/competitor-watcher log these competitive updates to the changelog
/segment-strategist evaluate the healthcare vertical as a new segment
```

**On parallel review:** Pipeline Runner pipelines call for Advisory Board and Alignment Auditor to run simultaneously. In Claude Code, they run sequentially in the same session — the feedback merging and quality gating work identically.

---

## Using with Cursor

Agents are Cursor Skills. To activate them in your project:

1. Ensure you have a `.cursor` folder in your project root.
2. Copy or symlink each folder from `product-knowledge-base/06-agents/skills/` into `.cursor/skills/`:
   - `context-builder`
   - `asset-builder`
   - `advisory-board`
   - `alignment-auditor`
   - `pipeline-runner`
   - `performance-analyst`
   - `competitor-watcher`
   - `segment-strategist`

**Example (macOS/Linux):** From project root:
```bash
mkdir -p .cursor/skills && cd .cursor/skills && for name in context-builder asset-builder alignment-auditor advisory-board pipeline-runner performance-analyst competitor-watcher segment-strategist; do ln -sf "../../product-knowledge-base/06-agents/skills/$name" "$name"; done && cd ../..
```

## Tips for Best Results

1. **Be Specific:** Include segment name, persona, campaign context
2. **Provide Context:** Share campaign briefs, segment context, or relevant docs
3. **Reference PMM Command Center:** Agents work best when the knowledge base is populated
4. **Trust the Pipeline:** The orchestrated pipeline ensures both buyer resonance AND PMM Command Center alignment
5. **Populate Knowledge First:** Content quality is only as good as the underlying segment context
6. **Use Quick Mode When Appropriate:** Skip review cycles for fast iteration when you'll review manually
7. **Feed Back Performance Data:** Use the Performance Review pipeline to keep the knowledge base grounded in real-world results

## Troubleshooting

**Agent not activating?**
- Be explicit about what you want (e.g., "populate segment context" vs. "help with segment")
- Check that skills are copied/linked into `.cursor/skills/`
- Check that relevant PMM Command Center files exist

**Content not aligned?**
- Ensure segment context files are populated
- Use Alignment Auditor to identify specific alignment issues

**Content doesn't resonate?**
- Use Advisory Board to get buyer perspective
- Review buying-committee.md — personas may need updating

**First draft not hitting quality bar?**
- Ensure the knowledge base is well-populated before generating content
- The pipeline quality depends on the foundation — garbage in, garbage out
