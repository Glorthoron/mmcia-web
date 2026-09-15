# FACTORY.md — Potato Factory applied to this lander

Source pattern: Lauren “Potato Factory” (Tater build / Hashbrown review / Steve orchestrate).
Adapted to MMCIA fleet — not a clone of Galaxy/shipbythursday infra.

## Why

Separating **build** and **review** stops false “done”.
Chat orchestrates; **Cursor/Claude** writes.
Skills and rules live **in the repo**.

## Loop for this project

1. **Orchestrator** (hermes-chief): updates plan, opens ticket/PR intent, does not code the site.
2. **Optional spike**: throwaway HTML in chat/Grok — never the production tree.
3. **Builder**: works on branch in this repo (or `mmcia-web` app dir once scaffolded).
4. **PR**: small, described against OMH-PLAN.
5. **Reviewer**: Hashbrown-lite only — approve / request changes.
6. **Merge** only after review OK.
7. **Verify**: contact works; grep no prices; build OK.

## Mapping

| Potato | Here |
|--------|------|
| Tater | Cursor / Claude Code builder |
| Hashbrown | 2nd agent or Herdr review playbook |
| Steve | hermes-chief / Jefe |
| P-Stack in repo | `AGENTS.md` + `.agents/skills` + product-marketing.md |
| Dr. Eggbot | optional bootstrap; not required for v1 |
| Slack control plane | optional PR→Ops later |

## Explicitly out of scope for v1 lander (lite)

- Cursor cloud agents mandatory
- Full Slack automation of shipbythursday
- Renaming bots Tater/Hashbrown in Grok
- ship-to-main without PRs

For **100% Potato fidelity** (bots + cloud + PR control plane), see **`FACTORY-FULL.md`**.
Lite = pattern. Full = pattern + automation + dedicated roles.

## Definition of done (factory)

A change is done when:

1. PR exists  
2. Reviewer passed checklist in `AGENTS.md`  
3. Merged  
4. Smoke: contact + no price leak  

Builder saying “finished” is **not** done.
