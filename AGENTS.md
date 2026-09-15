# AGENTS.md — MMCIA agency lander (Potato Factory lite)

This repo builds the **agency marketing site** for Mi Mundo Con IA.
Read `.agents/product-marketing.md` and `OMH-PLAN-mmcia-landing.md` before any change.

## Roles (do not collapse)

| Role | Who (this fleet) | Allowed | Forbidden |
|------|------------------|---------|-----------|
| **Orchestrator** (Steve) | hermes-chief / Jefe de gabinete | Scope, priorities, “tell builder X”, accept/reject plan | Writing production site code, marking “done” without review |
| **Builder** (Tater) | Cursor or Claude Code on this repo | Code, commits on branches, open PRs, run tests/build | Self-approving merge; inventing public prices |
| **Reviewer** (Hashbrown) | Second agent / Herdr Hashbrown-lite | Review PRs only: correctness, plan fit, no price leak | Implementing features; rewriting the whole PR as builder |

If you are unsure which role you are: **default = Builder**, and do not merge your own PR.

## Harness split

1. **Grok Bot / chat** = light harness: briefs, HTML spikes, orchestration text.
2. **Cursor / Claude Code** = serious coding harness: this repo, PRs, tests.
3. Orchestrator chat **never** replaces the coding harness for real work.

## Skills live in the repo

- Marketing: `.agents/skills` → marketingskills (symlink)
- Product context: `.agents/product-marketing.md`
- Design refs: Inspo MCP + plan Inspo section
- Any agent on this repo inherits these paths — do not keep critical skills only in a personal chat profile

## Git / PR loop (mature path)

```
brief (orchestrator) → branch → builder implements → PR
  → reviewer (Hashbrown-lite) → fix if needed → merge
```

Rules:

- No ship-to-main for multi-file features (the “2000-line PR dump” anti-pattern).
- PRs stay small and reviewable (“survive tomorrow” scaffolding first).
- “Done” = **merged after review**, not “builder said finished”.
- Optional later: PR comment/notify → Ops channel (same idea as PR→Slack).

## Product constraints (hard)

- Agency promo site; **CTA = contact only**
- **No** public service catalog with prices
- **No** `/pricing`, rate cards, Offer JSON-LD with amounts
- Before merge, reviewer greps public routes for price-like leaks (`€`, `297`, `/mes`, `USD` packs)

## Scaffolding bar (v1)

Ship the thinnest extensible site:

- `/` `/trabajo` `/sobre` `/blog` `/contacto` `/for-ai` `/llms.txt` `/privacy`
- SSG (Astro or Next — pick one, stick to it)
- Contact form works
- Inspo visual system (light paper, grotesk, no purple AI slop)

Not v1: CMS full, multi-locale, Whop embeds, cloud-agent requirement.

## Commands (when scaffold exists)

```bash
# install / dev / build — fill after scaffold
pnpm install   # or npm
pnpm dev
pnpm build
```

## Reviewer checklist (Hashbrown)

- [ ] Matches OMH plan (agency, contact CTA, no pricing pages)
- [ ] No public prices/catalog in HTML/copy
- [ ] Contact path present
- [ ] `for-ai` + `llms.txt` if claimed in PR
- [ ] No secrets in repo
- [ ] Build passes if CI/local build exists
