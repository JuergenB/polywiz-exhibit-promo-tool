# Background & Context — Where This Came From

> **Purpose.** The [why](01-why-promote-open-calls.md) explains the motivation. This document explains the *origin and the history* — who asked for it, how it was incubated in the ideas-inbox, and what was already decided before this repo existed — so nobody re-litigates settled ground.

---

## 1. The people and brands

| Name | Role |
|---|---|
| **Scott Power** | CEO of Not Real Art / Arterial. Non-technical stakeholder. Asked to reactivate PressRanger; set the "≥1 press release/month" target; wants to explore PR-as-a-service for artists/galleries. |
| **Elise** | Owns artist outreach and the fundraising/PR surface. Proposed pilot owner for *evaluating* the engine against a real call. |
| **Juergen Berkessel (Polymash)** | Technical lead. Owns the engine extension (repository, generator, n8n, the PolyWiz category). Authored Idea 011. |

**Brands in scope:** **Not Real Art**, **Artsville USA**, and **Arterial** (parent org / Crewest Studio). *The Intersect* is a sibling brand on the same engine but **out of scope for open-call promotion** (it would point the same engine at subscriber growth instead).

## 2. The two triggers (June 2026)

This concept crystallized from two real conversations:

1. **A Scott ↔ Juergen email thread** about reactivating **PressRanger** — a media-database + outreach tool both had bought on an AppSumo lifetime deal and then forgotten. Scott's reaction when reminded:
   > *"Happy to start leveraging it… Given the low cost of it, it would be interesting to see if we can turn it into some kind of service or capability for artists or galleries. We just need to learn it and optimize it."*
   …with the honest caveat: *"I'm not sure how effective it is. We'll have to see."*

2. **The Thursday Open Call meeting** on exhibition promotion, which surfaced the three gaps (no repository, no owner, no cadence) and the "institutionalize the outreach" ask — *"we notify the right sources every time we launch a call, because our own email can't be it."*

## 3. The key reframe — from "adopt a tool" to "own an engine"

The concept **started** as "should we adopt PressRanger as our PR platform?" and deliberately **moved** to a stronger position:

> **Don't make any rented tool the spine.** Extend the promotion repository we already own into an owned press-release + announcement engine, and treat PressRanger as **one optional, swappable feed** (a journalist database), not the centerpiece.

This is the same principle as [Idea 009 — Arterial's Owned Platform](https://github.com/JuergenB/ideas-inbox/tree/main/ideas/009-arterial-owned-platform): **own the layer, rent only the commodity inputs.** 009 owns the *collection*; this owns the *promotion* around it. If a vendor changes pricing, data quality, or terms tomorrow, we swap the feed — not the engine. This reframe is settled; the PressRanger evaluation that follows it is *component due-diligence*, not a pitch to build the system around PressRanger.

## 4. The ideas-inbox — how this was incubated

This project did not appear from nowhere. It graduated out of a deliberate pipeline.

### What the ideas-inbox is
[`JuergenB/ideas-inbox`](https://github.com/JuergenB/ideas-inbox) is a **cross-project ideas inbox** for Arterial, Not Real Art, Artsville USA, and Polymash. Its job is to capture, research, and evaluate new ideas **before** they become their own projects. The lifecycle:

```
Capture → Research → Evaluate (GitHub issues, go/no-go) → Graduate (own repo + plan)
```

Each idea gets a numbered folder (`ideas/0NN-slug/`) with a `README.md` discussion paper at the root and subfolders for `research/`, `presentations/`, `docs/`, and `exports/`.

### The neighboring ideas that matter here
This concept sits in a lineage — several sibling ideas are direct dependencies or precedents:

| # | Idea | Relevance to this project |
|---|---|---|
| **007** | [PolyWiz Paid Ads Generation Engine](https://github.com/JuergenB/ideas-inbox/tree/main/ideas/007-polywiz-paid-ads-engine) | The paid-social engine this concept rides on. "Open Calls" is proposed as 007's pilot ad category. Filed as [polywiz-app#181](https://github.com/JuergenB/polywiz-app/issues/181). |
| **009** | [Arterial's Owned Platform](https://github.com/JuergenB/ideas-inbox/tree/main/ideas/009-arterial-owned-platform) | The "own the layer, don't rent the spine" thesis. 009 owns the collection; this owns the promotion. |
| **011** | [Owned Promotion & PR Engine (PressRanger as one input)](https://github.com/JuergenB/ideas-inbox/tree/main/ideas/011-pressranger-outreach-playbook) | **This project's direct parent.** Status reached *"Research & Discussion — recommend a scoped team pilot."* |

### What "graduating" means
The inbox README says ideas that pass evaluation "get their own repository and project plan." Idea 011 reached **Recommend Pilot**, so it graduates into **this repo**. The Idea 011 folder remains the historical record (research, deck, pricing analysis, the team proposal); this repo is where the *concept becomes a designed product.* The artifacts you see in [source-materials/](source-materials/) — the directory widget, the concept deck, the Perplexity brief — are exports carried over from that idea folder.

## 5. What was already decided in Idea 011 (don't re-litigate)

These are settled inputs to the design work, established during the idea's research phase:

- **The engine is PolyWiz**, not a new app and not Artwork Archive. (Grounded in an actual 2026-06-12 review of the `polywiz-app` and `artwork-archive` repos.)
- **"Open Call" is already a scaffolded PolyWiz campaign type** — defined in the schema but disabled (`ENABLED_CAMPAIGN_TYPES` excludes it; UI says "Coming soon"). The Firecrawl scraper already extracts `submissionDeadline` / `submissionUrl` / `eligibility`. Enabling *organic* open-call promotion is estimated at **~1 hour** (flip the flag + a few Airtable Generation Rules).
- **Press-release generation is a new output *format*** of PolyWiz's existing AI content gen — not a new app.
- **Paid ads are the real build** — already an epic, [polywiz-app#181](https://github.com/JuergenB/polywiz-app/issues/181) (~4–6 weeks, Phase 0 prerequisites blocking). Organic posting works today.
- **PressRanger is a feed, not the spine** — and comes with eyes-open caveats: noisy keyword-matched beats, patchy direct emails (one test: ~8 emails on a 100-contact export), occasionally stale data, deliverability risk if you blast from it. → Use it for *discovery*; keep a curated Airtable as system-of-record; send with discipline.
- **The wire is a commodity, not the bargain.** PressRanger's lifetime deal buys *zero* wire discount; the savings are entirely in the *software* (media DB + CRM + AI), which costs $3K–$40K/yr elsewhere. Shop the wire per release (EIN Presswire ~$149 / eReleases $399+ nonprofit / PressRanger Gold $399).

## 6. Phasing (from Idea 011)

- **Phase 1 — Open-call & exhibition promotion (now).** Stand up the repository, a first-pass press-release generator, codify the playbook, and run it live on the next open call (*Art of Resistance* is the natural candidate) — including a conservative **~$250 paid-social flight** to measure cost-per-submission for the first time. Owners: **Elise** (outreach/evaluation) + **Juergen** (build). Goal: hit the one-release-a-month cadence and measurably lift submissions.
- **Phase 2 — Fundraising (fall).** Same engine, pointed at donors/grant press once the financial-readiness/DAF groundwork lands.
- **Phase 3 — PR-as-a-service (optional).** PressRanger is white-label/reseller-ready; once the playbook works on ourselves, it could become a branded service for artists and galleries in the network. Scott's instinct — flagged, not committed.

## 7. The open ask (status as of graduation)

From Idea 011's "The Ask," these were the human decisions in flight:
1. **Reactivate PressRanger access** (Scott sharing the password; Juergen's Tier 3 account — 10 brands, 4,000 exports/mo — is enough to start now).
2. **Elise evaluates it against a real call**, not as an abstract tool review.
3. **Team review on a Thursday** to agree the playbook, the Airtable schema, and the first live test.

This repo picks up where that left off: turning the recommendation into a **designed tool concept**. The pieces still to be authored (use cases, user-centric tasks, integration designs, the operational checklist) are tracked in [concept/README.md](../concept/README.md).
