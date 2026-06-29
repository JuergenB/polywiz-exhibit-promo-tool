# Concept — Design Work (To Be Authored With the User)

> **Status: mostly placeholders.** The [research/](../research/) folder establishes the *why* and *what exists*. This folder holds the *what we'll build* — and the design docs are **intentionally not written yet.** The exception is the decision register below, which frames the strategic questions that must be answered *before* design.

## 💡 Brainstorm captured: [promotion-playbook-and-tracker.md](promotion-playbook-and-tracker.md)
The shift from a *read-only reference table* to an *operational playbook + tracker* — "tell it the exhibition → it preps the content per place → you post & tick it off → we can see what got done." Includes the honest feasibility read (assisted + tracked manual submission is easy; auto-filling third-party forms is the trap). This is the plain-English heart of the [stakeholder deck](../presentations/exhibit-promo-tool-stakeholders.md).

## ▶ Start here: [00-key-decisions.md](00-key-decisions.md)
The architectural & strategic decisions that gate everything else — **which app this is built on (PolyWiz campaign type vs. Artwork Archive CRM utility vs. standalone), multi-brand vs. multi-tenant, and internal tool vs. white-label SaaS.** My thinking is documented there with options, tradeoffs, and leans. **The root question is Decision 5: tool or product?** — answering it unblocks the rest. The planned design docs below should not be written until the key decisions (at least Decision 5) are made.

---

## Planned documents *(blocked on [00-key-decisions.md](00-key-decisions.md))*

### 1. `use-cases.md` — Use cases & scenarios *(awaiting user input)*
The concrete situations the tool must serve. To capture:
- [ ] The promotion scenarios end-to-end (open call opens → exhibition announced → exhibition live; grant campaign; org milestone).
- [ ] Per-brand differences (Not Real Art vs. Artsville USA vs. Arterial; The Intersect explicitly out / repointed).
- [ ] Phase-1 (open-call promotion) vs. Phase-2 (fundraising) vs. Phase-3 (PR-as-a-service) scope boundaries.
- [ ] What's explicitly out of scope.

### 2. `user-tasks.md` — User-centric tasks & roles *(awaiting user input)*
Who does what, framed as jobs-to-be-done — not features.
- [ ] **Elise** (outreach/evaluation owner): find & reach arts journalists/podcasts/partners; evaluate against a real call; run the playbook.
- [ ] **Juergen** (build/ops): repository extension, generator, n8n hooks, the PolyWiz "Open Calls" category.
- [ ] **Scott** (stakeholder): cadence visibility (≥1 release/month), go/no-go.
- [ ] Each task: trigger → steps → what "done" looks like → which system it touches.

### 3. `press-release-and-pressranger-integration.md` — Press releases + PressRanger integration *(awaiting user input — research now done)*
The design for the two integrations the user flagged specifically. **Grounded by [research/05](../research/05-pressranger-deep-dive.md) + [research/06](../research/06-build-vs-integrate-and-oss-landscape.md):**
- [ ] **Press-release generation** as a new PolyWiz output format: input (open-call record) → draft (release + artist-email + social) → approval → distribution tiering (owned / EIN ~$149 / PressRanger Gold $399 / eReleases nonprofit).
- [ ] **PressRanger as a feed — constrained by reality:** there is **no API / Zapier / webhook**; the only data egress is **manual CSV export, tier-capped** (~4,000/mo on our Tier 3). So the integration is a **periodic batch ETL** (export → Airtable import), *not* a live sync. Design accordingly: discovery in PressRanger → CSV → curate into the Airtable *Journalists/Media* registry → our own CRM/sending; use PressRanger's pitch radar for inbound.
- [ ] **Build-vs-integrate decision captured:** build a **thin CRM on Next.js + Airtable + Claude + n8n** (no forkable OSS exists; no heavyweight CRM needed). PressRanger stays a swappable discovery input. See [research/06](../research/06-build-vs-integrate-and-oss-landscape.md).
- [ ] The "Ideas archive" linkage the user referenced — how this connects back to the ideas-inbox record and any idea-archive workflow.
- [ ] Eyes-open guardrails: noisy keyword-matched beats, ~8-emails-per-100 export reality, deliverability (transactional provider + DKIM/DMARC, not blasting from PressRanger).

### 4. `promotion-checklist.md` — The per-exhibition / per-open-call checklist *(awaiting user input + existing draft)*
The repeatable SOP — the operational heart. A **v1 draft already exists upstream** and should be adapted here:
**[Idea 011 → docs/playbook-exhibition-promotion.md](https://github.com/JuergenB/ideas-inbox/blob/main/ideas/011-pressranger-outreach-playbook/docs/playbook-exhibition-promotion.md)**
- [ ] The three press moments (Open Call Opens · Exhibition Announced · Exhibition Live) as actionable checklists.
- [ ] The decision tree (which levers by campaign type: grant / open call / exhibition / event / milestone).
- [ ] Distribution tiering rules (don't overspend the wire).
- [ ] Measurement: UTMs on every link → submissions-per-channel → cost-per-submission.
- [ ] Standing infrastructure to build once (repository tables, registry, landing-page convention, n8n hooks).

### 5. `ideas-inbox-integration.md` — Ideas inbox in the loop *(awaiting user input)*
How the ongoing idea/feedback flow ties in.
- [ ] How new promotion ideas, feedback, and the "ideas archive" feed this project.
- [ ] The graduation linkage back to [Idea 011](https://github.com/JuergenB/ideas-inbox/tree/main/ideas/011-pressranger-outreach-playbook).

---

## How to use this folder

When the user provides background on any section, create the corresponding `.md` here, ground it in their input, and cross-link to the relevant [research/](../research/) docs. Until then these remain **named placeholders, not commitments.** Nothing in `concept/` is built or decided yet.
