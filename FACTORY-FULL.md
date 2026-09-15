# FACTORY-FULL.md — 100% Potato Factory fidelity (MMCIA)

Lite (`FACTORY.md` / `AGENTS.md`) = **pattern**.  
Full = **pattern + dedicated bots + repo plugin + PR automation + cloud coding harness**.

You cannot get 100% by only adding MCP to Cursor. MCP is tools; Potato is **org + loop**.

---

## Fidelity scorecard (this machine, 2026-09-16)

| Potato piece | Status now | To reach 100% |
|--------------|------------|---------------|
| Steve (orchestrator, no build) | **Partial** — hermes-chief / Jefe | Dedicated SOUL: never writes app code; only dispatches |
| Tater (builder) | **Partial** — any Cursor/Claude session | Fixed builder identity + “use cloud agents going forward” + project agent for long context |
| Hashbrown (review-only) | **Partial** — playbook / 2nd pass | Dedicated profile/bot: **only** reviews PRs Tater opens; cannot implement |
| P-Stack as **repo plugin** | **Partial** — AGENTS.md + `.agents/skills` | Real plugin install in repo (Cursor rules + Claude marketplace / team kit) so **every** agent inherits |
| Skills in repo | **Yes** — marketingskills + product-marketing | Keep; add engineering review skill |
| Grok = light harness only | **Policy only** | Enforce in Steve/Tater SOULs; spikes never land on main |
| Serious code in Cursor | **Policy only** | Tater always opens repo in Cursor; cloud agent optional but default for heavy PRs |
| PR → channel → review → merge | **Missing** | GitHub repo + branch protection + bot/webhook → Ops/Slack/Telegram → Hashbrown → merge gate |
| Dr. Eggbot team kit | **Profile exists** (`dr-eggbot`) | Run install kit: profiles Tater/Hashbrown + rules + cloud connect |
| No false “done” | **Doc only** | CI + required reviewer; merge blocked without Hashbrown approve |
| Scaffolding bar | **In plan** | Enforced in Hashbrown checklist |

**Lite ≈ 40–50% fidelity.**  
**100% = every row green with automation, not vibes.**

---

## Target architecture (faithful clone of the *pattern*)

```
Samuel / Steve (hermes-chief or Grok “Steve”)
        │  “dile a Tater que…”
        ▼
   Tater (builder)
        │  Cursor local and/or Cursor cloud agent
        │  branch + code + tests
        │  opens PR
        ▼
   GitHub PR ──notify──► Ops channel (Slack or Telegram)
        │
        ▼
   Hashbrown (reviewer only)
        │  approve / request changes
        ▼
   merge (protected main) → deploy (Vercel)
```

Grok Bot: prototype HTML / coordination only.  
Never: Grok Bot as production coding harness.

---

## Build order (do this, in order)

### Phase A — Repo is the source of truth (1 session) — **DONE 2026-09-16**

1. ✅ Repo: https://github.com/Glorthoron/mmcia-web (public; private protection needs Pro)
2. ✅ Docs: `AGENTS.md`, `FACTORY*.md`, plans, product-marketing
3. ✅ `.cursor/rules/factory.mdc` + MCP inspo; ruleset `main-factory` (PR required); protection + CI `no-price-leak`
4. ✅ `.agents/skills-local/pr-review` + PR template  
   Marketingskills: install via `npx skills add` (not committed symlink)  
   **Solo caveat:** required approvals = 0 until Phase B Hashbrown account; then set to 1
### Phase B — Named bots (Grok and/or Hermes profiles)

| Bot | SOUL hard rules |
|-----|-----------------|
| **Steve** | Orchestrate only. May open issues. May say “Tater: …”. Must not edit site source. |
| **Tater** | Build only in Cursor harness. Opens PRs. After milestone: prefer cloud agents. Never merge own PR. |
| **Hashbrown** | Review only PRs from Tater. No feature branches for product work. Output: approve / changes requested. |

Optional: wire Grok Bot clones with those names (window extraction playbook) **or** Hermes profiles `tater` / `hashbrown` / keep Steve = chief.

### Phase C — Cursor cloud as Tater’s muscle

1. Cursor account with **Cloud Agents** enabled.
2. Tater standing order: *use cloud agents going forward* for multi-file work.
3. Optional **Project agent** with repo index for long context.
4. MCP (Inspo) in **project** `.cursor/mcp.json` — already started; cloud must be verified once (open cloud run, confirm tools list).

### Phase D — Control plane (PR → review)

Minimum faithful (no Slack required):

```text
PR opened → GitHub Action comments checklist
         → notifies Telegram/Hermes Ops (you already have gateway patterns)
         → Hashbrown session gets PR URL
         → Hashbrown posts review via gh api
         → main merges only if review = APPROVED
```

Closer to booth (Slack):

- Slack app in workspace
- GitHub → Slack PR channel
- Automation: “Hashbrown review this PR”
- Merge on green + approve

### Phase E — Dr. Eggbot kit

One-time: dr-eggbot installs team kit (skills, P-Stack-equivalent rules, cloud connect).  
Don’t block the lander on Eggbot if B–D are done manually once.

### Phase F — Prove the loop once (the “day 2 live factory”)

Run a **tiny** change end-to-end:

1. Steve: “Tater, add /contacto stub”  
2. Tater: branch + PR  
3. Channel ping  
4. Hashbrown: review  
5. Merge  
6. Smoke  

If that works, fidelity is real. Docs without that loop ≠ 100%.

---

## What “100%” does **not** mean

- Owning Lauren’s `shipbythursday` org or domain  
- Copying their Slack workspace  
- Renaming for cosplay without branch protection  
- MCP alone  

---

## Decision for Samuel

| Level | When |
|-------|------|
| **Stay lite** | Ship lander fast; manual PR+review |
| **Full factory** | You want ongoing multi-agent engineering org |

If **full**: next concrete build is **Phase A** (GitHub repo + branch protection + cursor rules) then **Phase B** (Tater/Hashbrown profiles). Say which level and we execute A without waiting on the lander content.
