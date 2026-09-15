# mmcia-web / inspo-web-plan

Agency marketing site for **Mi Mundo Con IA** (Samuel Ferrero).  
Contact-only conversion. **No public price catalog.**

## Potato Factory (Phase A done in-repo)

| Doc | Role |
|-----|------|
| `AGENTS.md` | Builder / Reviewer / Orchestrator |
| `FACTORY.md` | Lite loop |
| `FACTORY-FULL.md` | Path to 100% fidelity |
| `.cursor/rules/factory.mdc` | Cursor always-on rules |
| `.agents/product-marketing.md` | Positioning |
| `.agents/skills-local/pr-review` | Hashbrown checklist skill |

## Setup

```bash
git clone git@github.com:Glorthoron/mmcia-web.git  # or HTTPS URL after create
cd mmcia-web

# marketing skills (Agent Skills spec)
npx skills add coreyhaines31/marketingskills
# or: ln -s ../marketingskills/skills .agents/skills

# optional design MCP (Cursor)
# already in .cursor/mcp.json → inspo https://inspomcp.dev/api/mcp
```

Open folder in **Cursor**. Confirm MCP `inspo` green. Read `AGENTS.md` before coding.

## Branch policy

- `main` protected: PRs required
- Builder opens PR → Reviewer (Hashbrown) → merge
- Never ship multi-file features straight to main

## Status

Phase A (repo + rules + protection): **done** (public repo so free GitHub can enforce branch protection; private would need Pro).  
Site scaffold: not started (await domain/contact + go).

**Repo:** https://github.com/Glorthoron/mmcia-web