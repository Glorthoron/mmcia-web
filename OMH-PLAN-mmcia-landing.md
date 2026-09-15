# OMH Plan — Web agencia MMCIA (contacto + SEO/GEO)

**Status:** draft v3 — agency + Potato Factory lite  
**Conversion:** contact only  
**Forbidden on-site:** service menu with prices, SKU grid, public rate cards  
**Engineering:** see `AGENTS.md` + `FACTORY.md` (builder ≠ reviewer ≠ orchestrator)

---

## 1. Goals

1. Web que **promocione a Samuel / Mi Mundo Con IA como agencia-operadora**.
2. Tráfico y citas desde **buscadores + LLMs** → confianza → **contacto**.
3. Diseño con **Inspo**; marketing ops con **marketingskills** (ai-seo, site-architecture, copywriting, …).

## 2. Non-goals

- Catálogo de servicios + precios online.
- Checkout / Whop embeds / “elige tu plan”.
- Landing productizada EXPRESS/297 con tarifas (eso es comercial offline).
- Implementación hasta “go” de Samuel.

## 3. Positioning (from `.agents/product-marketing.md`)

Agencia que **monta y opera sistemas de agentes e IA** para pymes que ya venden.  
CTA único: **hablar**.  
Prueba: método, stack, criterio — no menú de packs.

## 4. Site architecture (marketingskills / site-architecture)

Tipo: **hybrid agency + content** (no SaaS pricing tree).

```
/                     Home — quién + para quién + CTA contacto
/trabajo              Casos / forma de trabajar (sin precios)
/sobre                Samuel + marca MMCIA
/blog                 Hub contenido (SEO + GEO)
/blog/[slug]          Artículos answer-first
/contacto             Form + email + (opcional) booking
/for-ai               Hechos planos para LLMs (sin tarifas)
/llms.txt             Índice máquina
/privacy  /legal
```

**Nav L1:** Inicio · Trabajo · Sobre · Blog · Contacto  
**No nav:** Precios · Servicios$ · Planes

Internal links: blog → contacto; home proof → trabajo; for-ai → about/contacto.

## 5. Page jobs

| Page | Job | Primary CTA |
|------|-----|-------------|
| Home | 5s: qué es + para quién + confianza | Contactar |
| Trabajo | Cómo operamos (gabinete, Hermes, n8n) | Contactar |
| Sobre | Persona/marca | Contactar |
| Blog index | Temas de autoridad | Leer → Contactar |
| Post | Responder query + E-E-A-T | Contactar al final |
| Contacto | Fricción mínima | Enviar |
| for-ai | Citabilidad LLM | Link contacto |

## 6. Design (Inspo — keep)

- Macro: **bento-grid** o **split-studio** (agency/editorial).
- Light paper + grotesk; CTA ink pills; no purple AI.
- Exemplar gravity: brevo-class clarity, not SaaS pricing tables.
- Hero: identidad + promesa de resultado operativo + CTA contacto (no “ver planes”).

DESIGN.md v0 tokens remain valid; **remove pricing components** from contract.

## 7. Copy rules (marketingskills / copywriting + cro)

- Clarity > clever.
- One primary action sitewide: contact.
- Benefits in customer language (“dejas de operar a mano el caos”).
- No fake stats; no invented client logos.
- CTA copy: “Cuéntame tu cuello de botella” / “Escribir a Samuel” — not “Ver precios”.

## 8. SEO (seo-audit mindset)

- Technical: fast static/SSG, indexable HTML, sitemap, canonical, hreflang only if multi-lang later.
- On-page: H1/H2 = questions operators ask (agentes IA negocio, automatizar pyme, Hermes/n8n ops…).
- Content hub: 6–12 cornerstone posts before scale.
- Schema: `Organization`, `Person`, `WebSite`, `BlogPosting`, `ContactPage`, `FAQPage` where real FAQs exist — **not** `Offer` price lists.

## 9. AI SEO / GEO (marketingskills / ai-seo)

**Google AIO:** people-first E-E-A-T; no separate “AI only” spam pages.  
**ChatGPT/Perplexity/Claude:** extractable structure + machine files.

Must-ship:

1. `/for-ai` — plain facts: who, what, for whom, geography, how to contact, what we don’t sell as self-serve.
2. `/llms.txt` (+ optional `llms-full.txt`) pointing to for-ai, about, best posts, contact.
3. Answer blocks 40–60 words under key H2s.
4. FAQ real (objeciones de contratar agencia), not pricing FAQ.
5. Same entity strings everywhere (Organization name).
6. Third-party mentions (X, Whop brand presence) consistent — no conflicting public price tables elsewhere that contradict “no public rates”.

**Target query classes (examples, ES):**

- “agencia automatización IA España”
- “montar agentes IA en mi negocio”
- “consultor Hermes n8n”
- “operar growth con agentes”

## 10. Contact system

- Form fields: nombre, email, web/negocio, “qué te frena” (textarea), optional budget band **private** (not shown as packages).
- Mailto fallback + anti-spam.
- Optional: calendar link later — not required v1.
- Success state: human reply expectation (e.g. 24–48h laborables).

## 11. Tooling in this project

| Tool | Path / role |
|------|-------------|
| marketingskills | `vendor/marketingskills` + `.agents/skills` → 50 skills |
| product context | `.agents/product-marketing.md` |
| Inspo MCP | hermes `mcp.inspo` + `~/Projects/inspo` |
| Plan docs | this folder |

Hermes-chief also has symlinks under `skills/marketing-skills/*`.

## 12. Acceptance criteria

- [x] marketingskills installed and linked into project
- [x] product-marketing.md = agency, no public prices
- [x] IA sin /pricing ni catálogo
- [ ] Samuel confirms name/domain/contact channel
- [ ] Explicit **go** to build

## 13. Potato Factory lite (engineering)

| Role | Actor | Job |
|------|--------|-----|
| Orchestrator | hermes-chief / Jefe | Scope, “tell builder…”, accept plan — **no site code** |
| Builder | Cursor / Claude Code | Branch + implement + open PR |
| Reviewer | Hashbrown-lite (Herdr / 2nd agent) | PR only — never build |

Rules locked in `AGENTS.md` / `FACTORY.md`:

- Grok/chat = light harness; Cursor = serious code
- Skills in repo (`.agents/skills`, product-marketing.md)
- No ship-to-main multi-file dumps; PR → review → merge
- “Done” ≠ builder claim; done = merge after review + smoke
- v1 scaffolding: survive tomorrow, extensible, not overcooked

## 14. Implementation handoff (after go)

1. **Orchestrator** confirms domain/contact + go.
2. **Builder** scaffolds SSG on branch (Astro/Next — one choice).
3. Builder applies Inspo tokens + agency pages only (no pricing).
4. Builder uses marketingskills: copywriting home/about/contact; ai-seo on for-ai + posts; schema without Offer prices.
5. **PR** with checklist from `AGENTS.md`.
6. **Reviewer** greps prices, checks plan fit, build.
7. Merge → smoke: contact works; `llms.txt` live; Lighthouse.

## 15. Risks

| Risk | Mitigation |
|------|------------|
| Accidental price leak from old draft | v3 plan; reviewer grep `€`, `297`, `/mes` |
| Thin “about me” only | Content hub required for SEO/GEO |
| LLM asks for prices | for-ai: engagement after conversation |
| False “done” from single agent | Factory: builder ≠ reviewer |
| Chat codes production tree | AGENTS.md harness split |
