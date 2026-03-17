# Experiments

The heart of PMM Command Center's data-driven approach. This folder tracks A/B test results, campaign performance, and messaging effectiveness. Every experiment produces structured data that feeds back into positioning, messaging, and content decisions.

---

## Folder Structure

```
experiments/
├── README.md                              # You are here
├── [campaign-name]-[YYYY-MM-DD].md        # One file per experiment/campaign
├── [campaign-name]-[YYYY-MM-DD].md
└── ...
```

**Naming convention:** `[campaign-name]-[YYYY-MM-DD].md` where the date is the experiment start date.

---

## What Goes Here

Each file captures a single experiment or campaign performance report:

- **Experiment setup** -- Hypothesis, variants tested, audience, channels, duration
- **Raw results** -- Impressions, clicks, conversions, cost metrics per variant
- **Analysis** -- Statistical significance, winning variant, segment-specific insights
- **Confidence tier** -- How much weight to give the findings (see below)
- **Action items** -- What to update in the knowledge base based on results

---

## Confidence Tiers

Not all data is created equal. Every experiment is tagged with a confidence tier:

| Tier | Criteria | How to Use |
|------|----------|------------|
| **Preliminary** | Small sample, short duration, single channel | Directional only -- do not update positioning based on this alone |
| **Emerging** | Moderate sample, multiple channels or repeated pattern | Worth incorporating into messaging tests and briefs |
| **Validated** | Large sample, statistically significant, replicated across segments or campaigns | Update segment context, messaging pillars, and proof points |

Confidence tiers are progressive. A Preliminary finding that replicates becomes Emerging. An Emerging finding that holds across segments becomes Validated.

---

## Cross-Campaign Pattern Analysis

The **Performance Analyst** agent looks across experiment files to identify patterns:

- Which messaging pillars consistently outperform
- Which personas respond to which proof points
- Which channels work best for which segments
- Seasonal or timing patterns in campaign performance

These patterns feed back into `01-segment-context/` and `03-prompts/` to improve future content.

---

## How Agents Use This Folder

- **Performance Analyst** -- Saves experiment reports here, runs cross-campaign analysis, identifies patterns
- **Asset Builder** -- References past experiment results when generating new variants (builds on what worked)
- **Context Builder** -- Updates segment context when Validated findings warrant positioning or messaging changes
- **Segment Strategist** -- Uses performance data to evaluate segment viability and prioritization

---

## Cross-References

- `01-segment-context/` -- Positioning and messaging updated based on Validated findings
- `02-campaigns/` -- Campaign briefs that define what gets tested
- `03-prompts/` -- Content generators refined based on what performs best
- `research/` -- Win/loss data that complements campaign performance
