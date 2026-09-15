## 2026-09-15 — Agency pivot + marketingskills

### Done
1. Cloned `https://github.com/coreyhaines31/marketingskills` → `~/Projects/marketingskills`.
2. Linked into `~/Projects/inspo-web-plan`:
   - `.agents/skills` → 50 marketing skills
   - `vendor/marketingskills`
3. Symlinked skills into hermes-chief `skills/marketing-skills/`.
4. Wrote `.agents/product-marketing.md` (agency, contact CTA, **no public prices**).
5. Rewrote `OMH-PLAN-mmcia-landing.md` + `task_plan.md` + `findings.md` for agency site IA (home/trabajo/sobre/blog/contacto/for-ai; no /pricing).

### Next
- Samuel: dominio + email/contacto + go
- Then implement SSG with Inspo visuals + marketingskills copy/ai-seo

## 2026-09-16 — Potato Factory → web plan

### Done
1. Applied Potato Factory brief to agency lander (lite, not Galaxy 1:1).
2. Added `AGENTS.md` — Orchestrator / Builder / Reviewer; PR loop; no price-leak checklist.
3. Added `FACTORY.md` — Tater/Hashbrown/Steve → Cursor/Herdr/hermes-chief.
4. OMH plan → **v3** (factory handoff §13–15).
5. `task_plan.md` + `findings.md` updated.

### Next
- Samuel: dominio + email + **go**
- Builder: branch scaffold only after go (no main dump)

## 2026-09-16 — Cursor MCP for project agents

### Done
1. Confirmed user-level `~/.cursor/mcp.json` already has **inspo** (`https://inspomcp.dev/api/mcp`).
2. Added project-level `inspo-web-plan/.cursor/mcp.json` (same inspo server) so opening this folder in Cursor loads MCP in-repo.
3. Note: marketingskills are **Agent Skills** (`.agents/skills`), not MCP — Cursor picks them up via skills path / AGENTS.md, separate from MCP tools.

### How Samuel enables
- Cursor → open folder `~/Projects/inspo-web-plan`
- Settings → MCP → ensure inspo shows green / enabled
- Agent/Composer chat: tools like `recommend`, `get_design_system` appear when MCP connected
- Restart Cursor if MCP list empty after first open

## 2026-09-16 — Potato Factory 100% fidelity path

### Done
1. Wrote `FACTORY-FULL.md`: scorecard lite vs full; build order Phases A–F.
2. Clarified: MCP ≠ full factory; need Tater/Hashbrown/Steve + repo plugin + PR→channel→review→merge + optional cloud agents.
3. Linked from `FACTORY.md` to full path.

### Next (if Samuel chooses full)
- Phase A: GitHub repo + branch protection + `.cursor/rules`
- Phase B: profiles/bots Tater + Hashbrown
- Then prove one tiny PR loop live

## 2026-09-16 — Phase A executed

### Done
1. GitHub repo **public** `https://github.com/Glorthoron/mmcia-web` (private branch protection needs Pro; public = free enforce).
2. Initial commit factory docs + Cursor rule + MCP + Hashbrown skill + gitignore (no jefe blobs / vendor symlink).
3. `.cursor/rules/factory.mdc` alwaysApply.
4. `.agents/skills-local/pr-review` + `.github/PULL_REQUEST_TEMPLATE.md`.
5. CI `factory-gate.yml` job `no-price-leak`.
6. Branch protection on `main`: 1 approving review, dismiss stale, enforce admins, no force/delete, required check `no-price-leak`.

### Next
- Phase B when Samuel says go: Tater + Hashbrown profiles/bots
- Prove one tiny PR loop (Phase F mini)
