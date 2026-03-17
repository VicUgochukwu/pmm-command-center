# Setup Guide

Get PMM Command Center running in about 10 minutes. After that, spend 30-60 minutes feeding in your marketing docs. By the end, you'll have a structured knowledge base that grounds every AI interaction in your actual strategy.

---

## Before You Start: Gather Your Docs

Spend 15 minutes pulling together your marketing context. You don't need everything — even 2-3 documents gets you a working knowledge base.

### The essentials

- [ ] **Positioning or messaging doc:** Core positioning, value prop, messaging framework. A rough strategy deck works.
- [ ] **Buyer/persona info:** Who you sell to, their pain points, how they buy. Persona decks, interview notes, sales team bullet points — all fine.
- [ ] **Competitive landscape:** Who you compete against and how you differentiate. Win/loss notes, competitor research, sales battle notes.

### Adds depth fast

- [ ] **Case study URL:** The page on your site where customer stories live (e.g., `yoursite.com/customers`). The AI finds and structures every story automatically.
- [ ] **Data claims:** Stats you use in marketing (e.g., "87% of customers saw X in 90 days"). Include sources when available.
- [ ] **Brand voice or style guide:** Tone docs, brand guidelines, writing principles. Even rough workshop notes help.
- [ ] **Sales feedback:** Win/loss reports, competitive notes, objection patterns, deal stage insights.
- [ ] **Campaign performance data:** Past campaign metrics, A/B test results, engagement data. This is what makes the feedback loop work.

### Don't worry about

- **Format:** Google Docs, PDFs, slide decks, text files, pasted Slack threads. All fine.
- **Organization:** The AI classifies and structures everything.
- **Completeness:** A rough first pass beats no context. The gap report tells you exactly what's missing.

---

## Step 1: Choose Your Tool

### Claude Code *(recommended)*

Chat with Claude in your browser at [claude.ai](https://claude.ai) or in the [desktop app](https://claude.ai/download). No coding experience needed.

Continue to [Setting Up with Claude Code](#setting-up-with-claude-code).

### Cursor

Desktop app with a file tree — watch files get created and edited in real time. One terminal command during setup, then it's all chat.

[Download Cursor →](https://cursor.sh), then continue to [Setting Up with Cursor](#setting-up-with-cursor).

---

## Setting Up with Cursor

### Step 2: Install Cursor

1. Go to [cursor.sh](https://cursor.sh) and download
2. Install (drag to Applications on Mac, run installer on Windows)
3. Open Cursor

### Step 3: Clone the Repo

1. Get the repo URL from your GitHub fork
2. In Cursor: `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows), type `Git: Clone`
3. Paste the URL, pick a folder, click **Select Repository Location**
4. Click **Open** when prompted

You should see `product-knowledge-base/` in the sidebar.

### Step 4: Activate the Agents

1. Open the terminal: `` Ctrl+` `` or **Terminal → New Terminal**

   **Windows:** If terminal shows PowerShell or CMD, switch to Git Bash via the dropdown next to `+` in the terminal panel.

2. Paste this and press Enter:

```bash
mkdir -p .cursor/skills && cd .cursor/skills && for name in context-builder asset-builder advisory-board alignment-auditor pipeline-runner performance-analyst competitor-watcher segment-strategist; do ln -sf "../../product-knowledge-base/06-agents/skills/$name" "$name"; done && echo "Agents activated!"
```

3. You should see `Agents activated!`. Quit Cursor (`Cmd+Q` on Mac) and reopen it.

That's the only time you need the terminal.

### Step 5: Share Your Docs

1. Open chat: `Cmd+L` (Mac) / `Ctrl+L` (Windows)
2. Drag your files into the chat
3. Type:

```
Set up my knowledge base with everything I've shared here
```

**Continue to [What Happens Next →](#what-happens-next)**

---

## Setting Up with Claude Code

### Step 2: Get the Repo on GitHub

Fork or create your repo on GitHub. Your knowledge base lives here.

If you don't have a GitHub account, [sign up here](https://github.com/signup) (free).

### Step 3: Open in Claude

**Browser (claude.ai):**

1. Go to [claude.ai](https://claude.ai)
2. Connect GitHub: **Settings → Integrations → GitHub**
3. Start a new chat and attach your repo. Claude reads `CLAUDE.md` automatically and activates the full agent system

**Desktop app:**

1. Download the [Claude desktop app](https://claude.ai/download)
2. Connect GitHub in Settings
3. Open a new chat and attach your repo

> **Terminal user?** Install with `npm install -g @anthropic-ai/claude-code` (requires [Node.js 18+](https://nodejs.org)), clone your repo, run `claude` from inside the repo folder. `CLAUDE.md` loads automatically.

### Step 4: Share Your Docs

Drag files into chat or paste content directly. Then:

```
Set up my knowledge base with everything I've shared here
```

You can also invoke agents directly with slash commands:

- `/context-builder populate my SMB segment from this doc`
- `/asset-builder write 3 LinkedIn ads for our mid-market segment`
- `/pipeline-runner run a full content pipeline for our enterprise segment`
- `/performance-analyst analyze Q4 campaign results and recommend KB updates`
- `/competitor-watcher check for updates on [competitor name]`
- `/segment-strategist evaluate our enterprise positioning against market trends`

**Continue to [What Happens Next →](#what-happens-next)**

---

## What Happens Next

After you share your docs, the agents will:

1. Show a **triage plan** — what they found (segments, competitors, case studies). Confirm or adjust before they build.
2. **Build your knowledge base** — structured files for every segment, competitor, persona, and proof point. Files land in the right folders: `positioning-strategy.md`, `messaging-framework.md`, `buying-committee.md`, `market-landscape.md` for segments; `competitor-overview.md`, `battlecard.md`, `objection-handling.md`, `counter-narratives.md` for competitors.
3. **Run dual review** — Advisory Board checks buyer resonance, Alignment Auditor checks brand consistency.
4. Deliver a **gap report** — what's missing, why it matters, who on your team likely has it, and what you can generate right now.

**Case studies:** Share a case study URL and the agents will visit every story on that page and create structured files automatically.

### Adding context over time

When you have new material:

```
Here's the missing buyer persona research, please update my knowledge base
```

### Closing the feedback loop

After campaigns run, share performance data:

```
/performance-analyst Here are the Q1 campaign results [attach data]. Analyze what worked and recommend updates to our knowledge base.
```

The Performance Analyst identifies which messaging resonated, which segments responded, and what needs adjusting — then recommends specific KB updates. This is what turns PMM Command Center from a one-time setup into a system that gets sharper over time.

---

## Share with Your Team

### Option A: Claude Projects *(easiest)*

Upload your `product-knowledge-base/` files to a [Claude.ai](https://claude.ai) Project and invite teammates. No setup on their end.

**Limitation:** Files don't auto-sync. Re-upload when you update the knowledge base.

---

### Option B: GitHub MCP *(live sync)*

Connects Claude directly to your GitHub repo. Updates sync automatically.

**Best for:** Teams that update the knowledge base frequently.

#### Claude.ai (web) or Claude Desktop

**Settings → Integrations** → connect GitHub. Done.

#### Claude Code (terminal)

1. Create a GitHub Personal Access Token at [github.com/settings/tokens](https://github.com/settings/tokens) with `repo` scope
2. Connect:

```bash
export GITHUB_PERSONAL_ACCESS_TOKEN=ghp_yourtokenhere
claude mcp add github-kb -s user -- npx -y @modelcontextprotocol/server-github
```

---

### Option C: Clone the repo

For teammates using Cursor. They clone your fork's URL and follow the [Cursor setup steps](#setting-up-with-cursor), skipping the fork step.

---

## Troubleshooting

### Cursor

**Activation command failed**
- Copy the entire command — it's long, scroll right to get all of it
- Make sure you're in the terminal panel, not the chat
- Windows: use Git Bash, not PowerShell or CMD

**Agents not responding**
- Quit and reopen Cursor after activation. Agents load on startup only
- Check that `.cursor/skills` exists (toggle hidden files: `Cmd+Shift+.` on Mac)
- Be explicit: "Using the Context Builder, set up my knowledge base with these files"

### Claude Code

**GitHub repo not connecting**
- Verify GitHub is connected: **Settings → Integrations → GitHub**
- Make sure you're attaching your fork, not someone else's repo

**Agents not activating**
- The repo must be attached to the conversation. Claude reads `CLAUDE.md` at the repo root to activate the agent system
- Be explicit: "Using the Context Builder, set up my knowledge base with these files"

**`npm install` failed (terminal users)**
- Check Node.js version: `node --version` (needs 18+). Get it from [nodejs.org](https://nodejs.org)
- Mac: restart terminal after installing Node.js
- Run `claude` from inside the repo directory

### General

**Performance Analyst not finding data**
- Campaign data should be in `experiments/` or shared directly in chat
- Include context: date ranges, channels, segments targeted

**Quality scores seem off**
- Quality tiers are contextual, not fixed rubrics. Resonance and alignment scores depend on how complete your knowledge base is. A thin KB produces less reliable scores. Fill gaps first.
