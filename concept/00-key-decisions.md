# 00 · Key Decisions Before We Design or Build

> **Purpose.** Before use cases, schemas, or code, a set of **architectural and strategic questions** has to be answered — because the answers change *what we build* and *where it lives*. This document is my thinking, laid out as a decision register: each question, the real options, the tradeoffs, my lean, and what would change the answer. **These are the team's decisions to make** (Scott, Elise, Juergen) — I'm framing them and recommending, not settling them. Status flags: 🔴 Open · 🟡 Leaning · 🟢 Settled upstream (in [Idea 011](https://github.com/JuergenB/ideas-inbox/tree/main/ideas/011-pressranger-outreach-playbook) / research).

> **Read the research first:** [why](../research/01-why-promote-open-calls.md) · [systems map](../research/03-related-systems.md) · [PressRanger deep-dive](../research/05-pressranger-deep-dive.md) · [build-vs-integrate](../research/06-build-vs-integrate-and-oss-landscape.md). Several decisions below are already half-answered there.

---

## The framing that dissolves half the argument: it's three layers, not one app

Most of the "PolyWiz vs. Artwork Archive vs. standalone" debate comes from treating this as **one application**. It isn't. It's **three layers**, and each has a different natural home:

| Layer | What it is | Already exists? | Natural home |
|---|---|---|---|
| **Engine** | URL/record → AI content (release, pitch, social) → approval → schedule → publish → paid ads | **Yes — PolyWiz** | PolyWiz |
| **Data + CRM** | Contacts, segments, pitches, coverage tracking, listing-site & partner registry, open-call records, submission/conversion data | **Partly — Airtable** (open-call + submission data already in Artwork Archive; contacts/CRM are new) | Airtable (system-of-record) |
| **Packaging** | Who it's for and how it's sold: internal tool · multi-brand · white-label product | **No — a choice** | TBD (Decision 5) |

Once you separate these, the host-app question stops being "which one app" and becomes "which layer goes where" — and the answers are much less contested. **The engine is PolyWiz; the data lives in Airtable; the only genuinely open strategic question is packaging.** Everything below follows from this.

---

## Decision 1 — Where does the ENGINE live? 🟡 Leaning PolyWiz

The user's framing: *Artwork Archive as a CRM utility, PolyWiz as a "Campaign Type," or a standalone PR app parallel to what we have.*

| Option | What it means | For | Against |
|---|---|---|---|
| **A. PolyWiz "Campaign Type"** | Enable the scaffolded "Open Call" type; press release = new output format; ads = [polywiz-app#181](https://github.com/JuergenB/polywiz-app/issues/181) | Engine already exists (gen → approval → schedule → publish on 14 platforms); "Open Call" is ~1hr to enable organic; per-brand flags exist; ads epic already filed | PolyWiz becomes more than "social campaigns" — scope creep risk; PR/CRM surface isn't a natural fit for its current UI |
| **B. Artwork Archive as a CRM utility** | Build the promo/CRM features into the art-data app | It already holds open-call records + submission/conversion data; it's the Airtable hub | It has **no** AI gen, no publishing, no ads, and only an export-utility UI. Building the engine here = **rebuilding PolyWiz inside it.** It's a *data* home, not an *engine* home |
| **C. Standalone PR app** | A new app parallel to PolyWiz/Artwork Archive | Cleanest separation; most freedom; the obvious shell *if* white-label is the goal (Decision 5) | Duplicates the engine PolyWiz already is (content gen, approval, scheduling, Zernio publish, ads). Highest build cost, most maintenance surface |

**My lean: A (PolyWiz as a Campaign Type) for the engine — but explicitly as a *capability*, not by absorbing CRM into PolyWiz.** PolyWiz *is* the engine already; B and C both mean rebuilding it. This is settled-ish upstream (Idea 011 grounded it in a real repo review). **What would change it:** if Decision 5 commits to a **near-term white-label product**, option C (standalone) becomes the stronger shell and PolyWiz becomes a service it calls. So **Decision 1 is downstream of Decision 5** — don't finalize it first.

## Decision 2 — Where does the DATA + CRM layer live? 🟡 Leaning Airtable SoR (Artwork Archive base)

[research/06](../research/06-build-vs-integrate-and-oss-landscape.md) already lands the build-vs-integrate call: **build a thin CRM on Airtable**, don't adopt a heavyweight CRM, don't fork a (nonexistent) PressRanger clone. Remaining sub-question — *which* Airtable:

| Option | For | Against |
|---|---|---|
| **Extend the Artwork Archive base** | Open-call records + submission/conversion data already live there → contacts/pitches/coverage sit next to the data ad-optimization needs; one art-data hub | Couples promotion to the art-pipeline base; scope/permissions creep |
| **New dedicated "Promotion" base** | Clean separation; portable; easy to hand to Elise; trivial to extract later for white-label | A second base to sync open-call records into (linked-record or n8n bridge) |
| **Inside PolyWiz's own datastore** | Co-located with the engine | PolyWiz is Airtable-backed already but is *campaign* data, not a media CRM; muddies its schema |

**My lean: extend the Artwork Archive base for Phase 1** (the conversion signal co-location is worth it, and it's the established art-data hub), **but keep the new promo tables cleanly namespaced** so they could be lifted into a dedicated base if white-label happens. This is the "Artwork Archive as a CRM utility" reading — true for the **data** layer, *not* the engine layer. **What would change it:** a firm white-label decision pushes toward a dedicated base from the start (cleaner tenant isolation later).

## Decision 3 — One product, or two capabilities? 🟡 Leaning two layered capabilities

Idea 011 bundles two things that have different natural homes:

1. **Open-call / exhibition *promotion*** — content gen + multi-channel distribution + paid social. → **PolyWiz capability** (Decision 1).
2. **Media-contact *CRM / outreach*** — relationships, pitches, coverage, the journalist registry. → **Airtable-backed utility** (Decision 2), drafting via Claude, sending via n8n/ESP.

**My lean: treat them as two layered capabilities over shared data, not one monolithic "PR app."** They share the contact + landing-page + open-call records but have different surfaces and cadences. This is what makes "standalone" unnecessary in Phase 1 — neither capability needs its own app; each extends something we own. **What would change it:** white-label packaging (Decision 5) would re-bundle them into one product shell.

## Decision 4 — Multi-brand, multi-tenant, or both? 🔴 Open (and consequential)

These are **not** the same thing and the distinction drives the architecture:

- **Multi-brand** = *our* brands (Not Real Art, Artsville USA, Arterial, partners) under *our* control. **PolyWiz already does this** with per-brand boolean flags + per-brand voice/keys. Near-zero marginal cost.
- **Multi-tenant** = *other organizations* as isolated customers (their data, auth, billing, support never crossing ours). A different, heavier architecture — and only needed if Decision 5 goes white-label.

| Option | Build cost | When it's right |
|---|---|---|
| **Multi-brand only** | ~Free (exists in PolyWiz) | Internal tool; the Phase-1 default |
| **Multi-brand now + multi-tenant-ready data model** | Low (naming/schema discipline) | Hedge — keeps white-label cheap to reach later |
| **Full multi-tenant now** | High (isolation, auth, billing, support) | Only if white-label is a committed near-term goal |

**My lean: multi-brand now, multi-tenant-*ready* (not multi-tenant-*built*).** Our [no-hardcoded-brand-identity rule](../research/02-background-and-context.md) already forces brand-agnostic prompts/config — that *is* most of the multi-tenant-ready discipline, for free. Don't pay the full tenancy tax before there's a validated service and a real external customer signal. **Dependency:** entirely gated by Decision 5.

## Decision 5 — Internal tool, or white-label SaaS for arts-org PR? 🔴 Open — THE strategic fork

This is the decision everything else hangs on. Scott's instinct (from the email thread): *"turn it into some kind of service or capability for artists or galleries."* And PressRanger itself is **already white-label / reseller-ready** — meaning a "PR-as-a-service" offering could be **largely PressRanger-resell + our playbook + our brand**, with far less platform build than a from-scratch SaaS.

| Option | What it is | For | Against / cost |
|---|---|---|---|
| **A. Internal tool only** | We promote our own calls; never sold | Smallest build; fastest to value; matches Phase-1 | Leaves Scott's revenue instinct on the table |
| **B. Internal now, extract product later** *(optionality)* | Build internal, keep data portable + brands agnostic, extract a product **if** the playbook proves out | Low-regret; validates on ourselves first (you can't sell a PR service you haven't run); keeps the door open cheaply | Requires discipline now (clean schema, brand-agnostic prompts) — most of which our rules already mandate |
| **C. White-label from day one** | Build for external orgs immediately | Maximizes the product bet | Pays multi-tenant + billing + support + sales cost **before** the playbook is proven; high risk |

**My lean: B — internal now, deliberately product-*ready*, white-label as Phase 3 optionality.** Rationale: (1) you cannot credibly sell arts-org PR-as-a-service until you've run the playbook on your own calls and have the cost-per-submission numbers — Phase 1 *is* the proof. (2) The cheap-to-keep-open moves (portable Airtable schema, brand-agnostic prompts, multi-brand config) are things our own rules already require. (3) If the bet proves out, **PressRanger's white-label mode + our playbook may be most of the product** — re-evaluate "build a SaaS platform" then, possibly as a thinner offering than a full build.

**This connects to two sibling ideas — review them before deciding:** [Idea 004 — Multi-Tenant Curator Platform](https://github.com/JuergenB/ideas-inbox/tree/main/ideas/004-multi-tenant-curator-platform) (the multi-tenant architecture question, already being thought about elsewhere) and [Idea 009 — Arterial's Owned Platform](https://github.com/JuergenB/ideas-inbox/tree/main/ideas/009-arterial-owned-platform) (own-the-layer thesis). White-label PR may belong *with* those, not as a separate product.

## Decision 6 — Primary user surface (who operates it, and where)? 🔴 Open

**Elise** owns outreach/evaluation. She needs a surface that doesn't require engineering. Options for Phase 1:

| Option | For | Against |
|---|---|---|
| **Reuse what exists** — PolyWiz UI for campaigns + Airtable (Interfaces) for the CRM/registry | Zero new app; ships now | Two surfaces to learn; some context-switching |
| **A thin new admin** unifying campaigns + CRM | One pane of glass | New build; premature before the workflow is proven |

**My lean: reuse PolyWiz UI + Airtable Interfaces for Phase 1; only build a unified surface if real friction shows.** Matches Simplicity First and lets Elise evaluate against a real call immediately. **What would change it:** white-label (Decision 5) eventually needs a polished, client-facing surface — but that's Phase 3.

## Decision 7 — PressRanger's role boundary 🟢 Settled in research

Already answered in [05](../research/05-pressranger-deep-dive.md) / [06](../research/06-build-vs-integrate-and-oss-landscape.md): **PressRanger is a swappable *discovery* feed, not the spine.** No API → batch CSV export → Airtable. Own the CRM/drafting/sending ourselves. **One open sub-question tied to Decision 5:** if we go white-label, PressRanger's reseller mode could *be* a large part of the offering — so its role expands from "feed" to "product component." Flag, don't decide yet.

---

## Decisions at a glance

| # | Decision | Lean | Status | Gated by |
|---|---|---|---|---|
| 1 | Engine host | **PolyWiz campaign type** | 🟡 | Decision 5 |
| 2 | Data/CRM host | **Airtable (Artwork Archive base), cleanly namespaced** | 🟡 | Decision 5 |
| 3 | One product or two | **Two layered capabilities over shared data** | 🟡 | Decision 5 |
| 4 | Multi-brand vs. tenant | **Multi-brand now, tenant-*ready*** | 🔴 | Decision 5 |
| 5 | Internal vs. white-label | **Internal now, product-ready, white-label = Phase 3** | 🔴 | — (the root) |
| 6 | User surface | **Reuse PolyWiz + Airtable; no new app yet** | 🔴 | Decision 5 |
| 7 | PressRanger role | **Swappable discovery feed** | 🟢 | (expands if 5 → white-label) |

**The pattern is obvious once tabulated: Decision 5 (internal vs. white-label) is the root.** Almost everything else is "lean X if internal, lean Y if white-label." So the team's first question isn't "which app" — it's **"are we building a tool, or a product?"**

## The low-regret path (my recommendation)

If the team wants to move without resolving the product bet today, this sequence keeps every door open at minimal cost:

1. **Build the engine capability in PolyWiz** (enable "Open Call," add press-release output, wire the #181 ads pilot). Reversible — it's our engine either way.
2. **Build the thin CRM/registry in a cleanly-namespaced Airtable** (Contacts · Pitches · Coverage · Listing/Partner Registry), brand-agnostic by our existing rules. Portable — lifts into a dedicated/tenant base later if needed.
3. **Run Phase 1 on one real call** (*Art of Resistance*), measure **cost-per-submission** for the first time.
4. **Defer the white-label decision** until that data exists — then decide tool-vs-product with evidence, reviewing Ideas 004 + 009 alongside.

Every step delivers internal value *and* is a prerequisite for the product version anyway — so we lose nothing by deferring Decision 5, and we'd be foolish to make it before the playbook is proven.

## Other open questions (the "etc.")

Smaller but real — to resolve during design, not blocking:
- **Sending infrastructure / deliverability** — own ESP vs. transactional provider (Postmark/SES/Resend) + DKIM/DMARC; never blast from PressRanger. (Intersects ideas-inbox `problems/001` deliverability work.)
- **Measurement & attribution** — the UTM convention (already in the [channel directory](../research/04-channel-directory.md)) → how cost-per-submission actually gets computed and reported.
- **Scope boundary** — Phase 1 open-call promotion only? Or include exhibition launches and the fall fundraising pivot in the same data model from the start?
- **Ownership & maintenance** — who owns the engine extension vs. the CRM operation long-term (Juergen builds; Elise operates — but maintenance/SLA?).
- **Naming / positioning** — "Arterial PR engine" (internal) vs. a product name (only matters if Decision 5 → white-label).
- **Data ownership / portability guarantees** — already a principle (own the spine); make it an explicit schema/export requirement.

---

### What I need from the team to move from "questions" to "design"
The single unblock is **Decision 5**: *tool or product?* Answer that (even as "tool for now, revisit after Phase 1") and Decisions 1–4 and 6 resolve to their leans above, and I can start the use-cases / schema / integration design in [concept/](README.md) with confidence.
