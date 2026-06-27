# 06 · Build vs. Integrate — The Open-Source Landscape

> **Purpose.** Given the [PressRanger deep-dive](05-pressranger-deep-dive.md) — and especially its headline finding that PressRanger offers **no programmatic feed** (CSV-export-only egress) — this doc answers the next question: if we want CRM-like outreach to *our own* list of journalists, contacts, and collaborators, do we **build our own thin version** or **assemble it from open-source building blocks**? It maps the GitHub/OSS landscape and lands a recommendation.
>
> GitHub searched via `gh` CLI on **2026-06-27**; star counts and licenses verified via `gh api`. "Last active" judged against that date.

---

## Takeaway (bottom line up front)

**Build a thin CRM on our existing stack (Next.js + Airtable + Claude + n8n). Do not fork a "PressRanger clone" (none usable exists), and do not adopt a heavyweight CRM.**

Three findings drive this:

1. **There is no forkable PressRanger.** Every PR-specific OSS repo is either an SEO-spam placeholder for a commercial wire service (0 stars, no code, no license), or a brand-new solo/hackathon "AI journalist outreach agent" (0–1 stars, days old, no license, no track record). Nothing is production infrastructure.
2. **PressRanger's real moat is its journalist *database* — which is proprietary and not our use case.** We're managing *our own* contacts, not licensing a 142k-row market database. That's a few Airtable tables, not a data-acquisition project. (The open journalist datasets that exist are tiny, stale, and the scrapers carry ToS / GDPR / CAN-SPAM risk — flagged throughout.)
3. **The two genuinely hard parts — AI drafting and email deliverability — aren't solved by PR-specific OSS.** Drafting is already our Claude strength (and our brand-voice-config rules mean a templated prompt beats any of these repos). Deliverability is solved by a transactional provider + DKIM/DMARC, not by an OSS tool (no usable warmup/reputation OSS exists).

The only OSS worth a *closer look* is reference material — patterns to study, not apps to adopt (see Recommendations).

---

## The landscape by category

### 1. PR / media-outreach CRM — *nothing forkable*
Almost nothing real. "Press release distribution" searches return ~15 repos, all 0 stars, mostly empty placeholders / WordPress-plugin mirrors for commercial wires. "AI journalist outreach" results are brand-new solo projects, no license, no traction.

| Repo | Stars | License | Last active | Stack | Relevance |
|---|---:|---|---|---|---|
| [AlphaRex-pixel/Autonomous-Outreach-Agent](https://github.com/AlphaRex-pixel/Autonomous-Outreach-Agent) | 0 | none | 2026-06 | Jupyter / OpenAI Agents | Reference only — toy PR-pitch agent. No license = unusable. |
| [mikiiiss/Ai-Journal](https://github.com/mikiiiss/Ai-Journal) | 0 | none | 2025-12 | Python | Reference — vector-matches journalists↔companies + LLM pitch gen. Conceptually closest; no license, stale. |
| [JhonsonAyalew/MediaWire-Press-Intelligence-Desk](https://github.com/JhonsonAyalew/MediaWire-Press-Intelligence-Desk) | 1 | none | 2026-06 | Python | Avoid — bundles a journalist scraper (ToS/legal flag); no license. |
| [Marcone1983/G-Press](https://github.com/Marcone1983/G-Press) | 0 | none | 2025-12 | TypeScript | Avoid — bundles a scraped "7000+ journalist" DB; legal risk. |
| [awesomedirectory/awesome-pr-tools](https://github.com/awesomedirectory/awesome-pr-tools) | 0 | Other | 2026-05 | Markdown | Reference (market map) — curated list of PR SaaS / journalist DBs / HARO platforms. Note: almost all *proprietary*, not OSS. |

### 2. Journalist / media databases — *proprietary; open scrapers are legally risky*
The valuable databases are proprietary (Muck Rack, Cision, Prowly, JournalistDB ~142k). Open datasets are tiny and stale; scrapers raise **ToS + GDPR/CCPA** concerns. For our own-list use case this is moot — we store *our* contacts, not a market DB.

| Repo | Stars | License | Last active | Relevance |
|---|---:|---|---|---|
| [APEGS/journalistDatabase](https://github.com/APEGS/journalistDatabase) | 0 | MIT | 2025-01 | Reference — small open CSV of journalists, MIT/reusable but tiny & unmaintained. |
| madisonhindo / vinitshah24 journalist-database | 0 | none | 2019–20 | Avoid — old class projects, no value. |

> ⚠️ **Legal flag:** storing scraped/guessed journalist emails and emailing them implicates GDPR / CAN-SPAM / CASL and platform ToS. Get sign-off before any scraping/enrichment path. For own-list outreach, skip this entirely.

### 3. HARO / source-request aggregators — *all closed SaaS*
The source-request platforms (Connectively/ex-HARO, Qwoted, Help a B2B Writer, Featured, SourceBottle) are closed. Only relevant OSS is one Claude-skill that scrapes Qwoted.

| Repo | Stars | License | Last active | Relevance |
|---|---:|---|---|---|
| [Bomx/qwoted-seo-backlinks-skill](https://github.com/Bomx/qwoted-seo-backlinks-skill) | 75 | none | 2026-05 | Reference (caveats) — Claude skill: find PR opportunities on Qwoted + draft pitches. Good *pattern* ("agent watches source requests → drafts pitch"); no license + scrapes a SaaS (ToS flag). |

If inbound source-request monitoring matters, the realistic path is an **n8n flow polling an official feed/API** where one exists — or just using PressRanger's own pitch radar, which we already own.

### 4. Cold-email / outreach sequencing — *richest category, but generic (not PR)*
The strong repos are *mechanism* (mail-merge, sequencing, AI drafting), not press-specific. Includes a 2026 wave of MIT-licensed Claude "outbound skills" that fit our AI stack.

| Repo | Stars | License | Last active | Relevance |
|---|---:|---|---|---|
| [growthenginenowoslawski/coldoutboundskills](https://github.com/growthenginenowoslawski/coldoutboundskills) | 429 | MIT | 2026-05 | **Strong reference** — MIT Claude skills for cold email (grade campaigns, export prospect searches). Repurposable patterns for press pitches on our Claude stack. |
| [oneshot-agent/oneshot-gtm](https://github.com/oneshot-agent/oneshot-gtm) | 453 | MIT | 2026-06 | Reference — agentic GTM loop w/ CLI + local dashboard. Architecture reference; sales-shaped. |
| [awdeorio/mailmerge](https://github.com/awdeorio/mailmerge) | 171 | MIT | 2026-06 | **Use directly (mechanism)** — simple, maintained, MIT CLI mail-merge w/ templating + SMTP. Could power the *send* step. (Deliverability is your SMTP's job — no warmup.) |
| [iPythoning/b2b-sdr-agent-template](https://github.com/iPythoning/b2b-sdr-agent-template) | 131 | MIT | 2026-06 | Reference — 10-stage AI-SDR pipeline w/ cron. Over-built for us; good sequencing/cron ideas (maps to n8n). |
| [eracle/OpenOutreach](https://github.com/eracle/OpenOutreach) | 2,255 | Other | 2026-06 | Avoid as base — LinkedIn automation (ToS risk); wrong channel for press. |

> **Deliverability note:** none of these handle SMTP warmup, domain reputation, SPF/DKIM/DMARC, or bounce/complaint handling — and no usable OSS for that exists. For a nonprofit pitching its *own* low-volume list, a transactional provider (Postmark / SES / Resend) + proper DKIM/DMARC is the right answer. (This intersects our existing deliverability work — see problems/001 in the ideas-inbox.)

### 5. General CRM frameworks to build on — *only Twenty fits our stack*
| Repo | Stars | License | Last active | Relevance |
|---|---:|---|---|---|
| [twentyhq/twenty](https://github.com/twentyhq/twenty) | ~51,800 | Other (custom) | 2026-06 | **Only serious "adopt a CRM" option for a TS/Node/AI shop.** "Designed for AI," very active; existing MIT n8n nodes ([shodgson/n8n-nodes-twenty](https://github.com/shodgson/n8n-nodes-twenty)) + MCP servers. But it's a Salesforce-alternative — Postgres-backed, heavy to self-host vs. Airtable. **Verify the custom license before any commercial-ish use.** |
| [espocrm/espocrm](https://github.com/espocrm/espocrm) | ~3,082 | AGPL-3.0 | 2026-06 | Reference for *data-model/workflow design* only — PHP/AGPL is off-stack. Steal the schema thinking. |
| [monicahq/monica](https://github.com/monicahq/monica) | ~24,809 | AGPL-3.0 | 2026-04 | Reference — "personal CRM," relationship-journaling shape (wrong for campaign outreach); PHP/AGPL off-stack. |

### 6. Press-release / AI pitch generation — *build it yourself*
Weakest OSS category — every result is a 0–3★ demo, mostly no license. The best (an [AWS sample multi-agent generator](https://github.com/aws-samples/sample-press-release-generator-with-genai-agents), 3★) only *demonstrates a pattern*. **This is exactly what our Claude integration already does best** — a templated prompt + per-brand voice config + Airtable contact context beats all of them.

### 7. Contact enrichment / email finding — *legally risky; skip for own-list*
Real OSS exists ([email-sleuth](https://github.com/buyukakyuz/email-sleuth) 409★ MIT/Rust; [MailFinder](https://github.com/mishakorzik/MailFinder) 566★ GPL; [EmailFinder](https://github.com/Josue87/EmailFinder) 421★ GPL) but all are OSINT email-*guessing* / search-scraping — ToS, privacy, and deliverability concerns. For emailing our own contacts, we don't need this.

---

## Recommendations

### Worth a closer look (reference, not adoption)
1. **[twentyhq/twenty](https://github.com/twentyhq/twenty)** — the *only* adopt-a-CRM option that fits our stack, and only if the contact model outgrows Airtable (thousands of contacts, multi-user RBAC, complex pipelines). Already has n8n + MCP integration. Verify license first.
2. **[coldoutboundskills](https://github.com/growthenginenowoslawski/coldoutboundskills)** — best reference for AI-drafting + campaign-grading *patterns* on a Claude-native stack. Mine it; don't adopt wholesale (sales-shaped).
3. **[awdeorio/mailmerge](https://github.com/awdeorio/mailmerge)** — clean OSS reference for the *send/merge* step if we don't route through a transactional provider via n8n.
4. **[espocrm](https://github.com/espocrm/espocrm)** — study its contact/segment/activity schema; don't run it.
5. **[awesome-pr-tools](https://github.com/awesomedirectory/awesome-pr-tools)** — the market map for deciding which proprietary journalist DB (if any) we'd ever pay for.

### The honest build-vs-integrate call
**Build a thin CRM on Next.js + Airtable + Claude + n8n.** Adopting Twenty/EspoCRM/Mautic is a net complexity increase — a second datastore (Postgres/MySQL), a second auth/permissions system, self-hosting + upgrade burden, and AGPL/custom-license obligations — to replace something Airtable already does well at our scale. Per our **Simplicity First** rule, that's over-building for a small nonprofit's own-list use case.

**Recommended shape (thin build on existing stack):**
- **Airtable** = system of record: *Contacts* (beat / outlet / segment tags), *Campaigns*, *Pitches* (status: drafted → sent → replied → covered), *Coverage*. This is the same Artwork Archive base extension already proposed in [03-related-systems.md](03-related-systems.md).
- **Next.js (App Router)** = admin/UI surface + API routes; multi-brand via existing brand config.
- **Claude** = pitch / press-release drafting, brand voice injected from per-brand config (not hardcoded), contact context pulled from Airtable.
- **n8n** = send orchestration via a transactional provider, reply/bounce capture, follow-up sequencing, and any source-request polling — using native Airtable nodes.

### Where PressRanger still fits (integrate *and* build — not either/or)
The two options aren't exclusive. The pragmatic architecture:
- **Keep PressRanger as an owned *discovery* tool** — its journalist/podcast database + pitch radar are a real asset we already paid for. Use it to *find* arts-beat contacts.
- **Get them out the only way it allows** — periodic **manual CSV export within our tier cap** (Tier 3 ≈ 4,000/mo) → import to Airtable. There is no live feed (see [05](05-pressranger-deep-dive.md)); accept the batch ETL.
- **Own the CRM, drafting, sending, and tracking ourselves** — the thin Airtable + Claude + n8n build above. This is where the durable, portable value lives, and it survives if PressRanger's data disappoints or its terms change.

That's the [Idea 009](https://github.com/JuergenB/ideas-inbox/tree/main/ideas/009-arterial-owned-platform) principle again: **own the engine; rent only the swappable inputs.** PressRanger is a (cheap, already-owned) input — not the system.

### Searches that came up empty (stated honestly)
- HARO/source-request aggregators: no usable OSS app (one no-license Qwoted-scraping skill).
- SMTP warmup / deliverability: nothing usable in OSS.
- Maintained OSS press-release/pitch generators: none above toy scale.
- Open journalist databases: only tiny, stale CSVs; scrapers carry ToS/privacy risk.

*Star counts/licenses verified via `gh api` / `gh search` on 2026-06-27. Repos marked "Other"/custom (Twenty) returned `NOASSERTION` from the GitHub license API — read the actual LICENSE before any reuse.*
