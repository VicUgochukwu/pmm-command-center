# Integrations

Tool integration configs, MCP server setups, API connection templates, and tool-specific activation guides. This folder makes PMM Command Center portable across different AI tools and development environments.

---

## Folder Structure

```
integrations/
├── README.md                              # You are here
├── mcp-server-config.md                   # MCP server configuration for GitHub live sync
├── claude-projects-setup.md               # Claude Projects setup checklist
├── cursor-skills-activation.md            # Cursor skills activation instructions
└── {{integration-template}}.md            # Template for adding new tool integrations
```

---

## What Goes Here

**MCP Server Configuration** -- GitHub live sync setup so your knowledge base stays current across tools. Includes server config JSON, environment variables, and troubleshooting.

**Claude Projects Setup** -- Step-by-step checklist for connecting your knowledge base to Claude Projects. Covers repo attachment, agent auto-routing verification, and slash command testing.

**Cursor Skills Activation** -- Instructions for symlinking agent skills into `.cursor/skills/`, verifying activation, and testing each agent in Cursor.

**New Integration Template** -- Standard template for documenting any new tool integration: prerequisites, setup steps, verification, and known limitations.

---

## How to Add a New Integration

1. Copy `{{integration-template}}.md` and rename it to `[tool-name]-setup.md`
2. Fill in the setup steps, prerequisites, and verification checklist
3. Test the integration end-to-end before marking it complete

---

## Cross-References

- `06-agents/` -- Agent specifications that integrations activate
- `06-agents/skills/` -- Skill definitions that get linked into tool-specific locations
- `CLAUDE.md` (repo root) -- Auto-routing config that Claude Projects and Claude Code use
