# Research

Market research, analyst reports, industry data, and the competitor changelog. This is the raw intelligence layer that feeds into segment context (`01-segment-context/`) and competitive intel (`05-sales-enablement/`).

---

## Folder Structure

```
research/
├── README.md                              # You are here
├── competitor-changelog.md                # Running log of competitor moves (maintained by Competitor Watcher)
├── market-research/                       # Analyst reports and internal research
│   └── [report-name]-[date].md
├── industry-trends/                       # Industry trend data and analysis
│   └── [trend-topic]-[date].md
└── win-loss/                              # Win/loss analysis data
    └── [analysis-name]-[date].md
```

---

## What Goes Here

**Market Research Reports** -- Analyst reports (Gartner, Forrester, IDC, etc.) and internal research summaries. One file per report, named `[report-name]-[YYYY-MM].md`. Include key findings, implications for positioning, and segment-specific takeaways.

**Industry Trend Data** -- Macro trends, category shifts, and market dynamics that affect your positioning. The Segment Strategist agent references this data when identifying new segment opportunities.

**Competitor Changelog** -- A single running file (`competitor-changelog.md`) tracking competitor product launches, pricing changes, funding rounds, leadership changes, and strategic shifts. The **Competitor Watcher** agent maintains this file automatically. Entries are timestamped and tagged by competitor.

**Win/Loss Analysis** -- Structured analysis of closed deals. Captures why you won or lost, which competitors were involved, which personas drove the decision, and what messaging resonated or fell flat. Feeds into `05-sales-enablement/` battlecards and objection handling.

---

## How Agents Use This Folder

- **Competitor Watcher** -- Maintains `competitor-changelog.md` with ongoing competitive intelligence
- **Context Builder** -- References research when populating segment context and competitive intel
- **Segment Strategist** -- Uses market research and industry trends to identify new segment opportunities
- **Performance Analyst** -- Cross-references win/loss data with campaign performance from `experiments/`

---

## Cross-References

- `01-segment-context/` -- Segment positioning informed by market research
- `05-sales-enablement/` -- Competitive intelligence informed by competitor changelog and win/loss data
- `experiments/` -- Campaign performance data that complements win/loss analysis
