# Segment Context

Your product doesn't have one market — it has several. Each one has different buyers, different pain points, different competitors, and different reasons to choose you. This folder is where you codify that context, segment by segment.

Each segment gets its own folder with 4 files that together capture how you position, message, and sell to that audience. Once filled in, these become the source of truth that prompts, briefs, sales enablement, and content generation all reference.

---

## File Structure

```
01-segment-context/
├── {{segment-1}}/                         # Template folder — copy for each segment
│   ├── positioning-strategy-template.md
│   ├── messaging-framework-template.md
│   ├── buying-committee-template.md
│   └── market-landscape-template.md
│
├── smb/                                   # Example: first segment
│   ├── positioning-strategy.md
│   ├── messaging-framework.md
│   ├── buying-committee.md
│   └── market-landscape.md
│
└── enterprise/                            # Example: second segment
    └── ...
```

Each segment is completely independent. They share a product, but everything else — positioning, personas, messaging — is segment-specific.

---

## The 4 Files

**`positioning-strategy.md`** — The strategic source of truth. Your positioning strategy, competitive alternatives, differentiators, proof points, and narrative all live here. Every other file in the folder references this one. Start here. For codified proof points (case studies and data claims), see `07-proof-points/`.

**`messaging-framework.md`** — The copy execution layer. Translates your positioning into 3 messaging pillars with ready-to-use copy blocks: headlines, body copy, CTAs, email subject lines, and social posts.

**`buying-committee.md`** — The people layer. Maps the buying committee — who holds budget, who drives adoption internally, who can kill the deal on technical grounds — with role-specific pain points and messaging.

**`market-landscape.md`** — The operational layer. How deals actually progress, what kills them, GTM motion, channel strategy, and success metrics for this segment.

---

## How to Create a New Segment

Copy the `{{segment-1}}/` template folder, rename it (e.g., `smb/`, `enterprise/`), and populate the files. The fastest path is using the **Context Builder** agent (if you've set up `06-agents/`) or AI-assisted prompts — see the [Setup Guide](../../SETUP-GUIDE.md) for the exact approach.

If working manually, fill in this order:
1. `positioning-strategy.md` — strategic foundation
2. `buying-committee.md` — buying committee
3. `messaging-framework.md` — copy blocks
4. `market-landscape.md` — deal mechanics and GTM

Each template includes a **Quick Start Mode** (10-20 min) that captures the minimum viable context. Expand later.

**When to create a segment:** When buying behavior is meaningfully different — different personas, pain points, competitors, or GTM motion. Most products have 2-4 segments.
