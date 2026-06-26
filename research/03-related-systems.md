# Related Systems — How the Pieces Fit

> **Purpose.** This concept is *not* a greenfield app. It's mostly the wiring-together and extension of systems that already exist. This document maps each system, what it does today, and the role it plays in the promotion engine — so design conversations start from an accurate picture, not assumptions.

---

## The one-diagram model

```
                         ┌─────────────────────────────────────────────┐
                         │        ARTWORK ARCHIVE (Airtable + n8n)      │
                         │  system-of-record + conversion source       │
                         │                                             │
                         │  • Open-call / Campaign records             │
                         │    (deadline, landing URL, eligibility)     │
                         │  • Submission status flow                   │
                         │    (Imported → Enriched → Accepted)         │
                         │  • + NEW promo tables: contacts, listing-   │
                         │    site & partner registry, assets          │
                         └───────────────┬─────────────────────────────┘
                                         │ feeds (an open-call record
                                         │ triggers a campaign; submission
                                         │ status = the conversion signal)
                                         ▼
   ┌──────────────┐  one feed   ┌─────────────────────────────────────┐
   │ PRESSRANGER  │────────────▶│            POLYWIZ (the ENGINE)      │
   │ journalist   │  arts-beat  │  URL → AI content → approval queue  │
   │ DB + pitch   │  contacts + │  → tapering schedule → Zernio publish│
   │ radar (owned)│  pitch radar│  (14 platforms), multi-brand        │
   └──────────────┘             │                                     │
                                │  • "Open Call" campaign type        │
                                │    (scaffolded, disabled — ~1hr on) │
                                │  • Press release = new output format│
                                │  • Paid ads = polywiz-app#181 epic  │
                                │  • Per-brand capability flags       │
                                └───────────────┬─────────────────────┘
                                                │ publishes / promotes
                                                ▼
              Press wire (shopped per release) · Free listing boards ·
              Artist email (own ESP) · Paid social (Meta + Pinterest) ·
              all pointed at ONE landing page, UTM-tagged
                                                │
                                                ▼
                                   📈 Submissions (measured: cost-per-submission)
```

**The principle:** PolyWiz is the **spine we own**. Everything else is either a system-of-record we own (Artwork Archive) or a **swappable commodity input** (PressRanger, wires, listing boards). If any input degrades, we swap the input — never the engine.

---

## PolyWiz — the engine

**Repo:** `polywiz-app` (`JuergenB/polywiz-app`) · **Prod:** polywiz.polymash.com

**What it is today:** a campaign generator for art exhibitions (a LateWiz fork + Zernio API + Airtable). It does **URL → AI-drafted content → approval queue → tapering schedule → publish across 14 platforms via Zernio**, multi-brand, with per-brand voice and API keys. It runs tapering ~6-month campaigns with an approval queue. Multi-brand: Not Real Art, Artsville USA.

**Why it's the engine (not a thing we build):**
- **"Open Call" is already a scaffolded campaign type** — defined in the schema but disabled (`ENABLED_CAMPAIGN_TYPES` excludes it; UI says "Coming soon"). The Firecrawl scraper already extracts `submissionDeadline` / `submissionUrl` / `eligibility`, and the prompt composer already injects deadline context. **Enabling organic open-call promotion ≈ 1 hour** (flip the flag + add a few Airtable Generation Rules for submission CTAs).
- **Press-release generation = a new output format** of the existing AI content gen — not a new app.
- **Per-brand capability flags already exist** (e.g. `lnkBioEnabled` on the Brands table). "Open Calls" becomes the same kind of per-brand toggle — Artsville / Not Real Art on; The Intersect off (or repointed at subscriber growth).
- **Paid ads are the genuine build** — filed as the [polywiz-app#181](https://github.com/JuergenB/polywiz-app/issues/181) epic (~4–6 weeks; Phase 0 prerequisites blocking). Organic posting works today; conversion-optimized ad spend code does not yet exist. Pinterest is already wired for organic.

**Its role here:** generate the release + artist-email + social copy from an open-call record, route through approval, publish on a deadline-aware tapering schedule, and (once #181 lands) run the paid flight.

> ⚠️ **Project guardrail (from memory):** *Never modify generation prompts during live testing.* If quality drops, revert immediately. Any prompt work for open-call content happens off the live path.

## Artwork Archive — system-of-record & conversion source (NOT the engine)

**Repo:** `artwork-archive` (`JuergenB/artwork-archive`) · Epic #74 · uses the `polymash-nextjs-airtable-boilerplate`.

**What it is today:** an **n8n + Airtable intake → enrich → export** pipeline (its only UI is an export utility — Phase C pivoted the export pipeline from n8n to a Next.js TypeScript app; n8n remains for intake/enrichment). It holds the **open-call records** (Campaigns table: deadline, landing-page URL, exhibition details) and the **submission conversion data** (status flow Imported → Enriched → Accepted).

**Why it is *not* the engine:** it has **no** AI content generation, no social/ads publishing, and no promo UI. Building the promo engine here would mean a second app duplicating PolyWiz. **It feeds PolyWiz; it isn't the engine.**

**Its role here:** the **art-data hub.** It's where the open-call records live (triggering PolyWiz campaigns) and where the new promo tables belong — *Press Releases*, *Announcement Playbook*, *Journalists/Media*, *Listing-Site & Partner Registry*, *Artist List segments*, *Campaign Assets*. The **submission status is the conversion signal** that ad optimization needs.

## PressRanger — one plugged-in feed (owned, cheap, swappable)

**What it is:** a media-database + outreach tool, bought by both Scott and Juergen on an **AppSumo lifetime deal** (then forgotten). It's really **two products in one box**:

1. **Media DB + CRM + AI pitch engine — the half we value.** ~500K journalist profiles, ~150K publishers, ~200K podcasts, searchable by beat/topic/location; built-in CRM; AI that drafts releases/pitches and builds target lists; HARO-style pitch radar; CSV export; multiple brand workspaces. This lane costs **$3K–$40K/yr** elsewhere (Prowly ~$3,100, Cision ~$10–15K, Meltwater ~$15–40K+). **We own it outright.**
2. **A pay-per-release wire — a commodity, *not* the bargain.** $299 Premium / $399 Gold, **not discounted by our subscription** (free accounts pay the same). EIN Presswire (~$149) is cheaper for comparable syndication; eReleases ($399+) gives real PR Newswire reach at nonprofit rates.

**Owned capacity:** Juergen's account is **AppSumo Tier 3** — 10 brands, 4,000 contact exports/mo, pitch notifications, custom media rooms. Enough to run Phase 1 without resolving Scott's tier.

**Eyes-open caveats:** noisy keyword-matched beats (false positives), patchy direct emails (one test: ~8 emails on a 100-contact export), occasionally stale data, deliverability risk if you blast from the tool.

**Its role here:** **discovery only** — pull arts-beat contacts into the Airtable registry, use the inbound pitch radar. Curate in Airtable (our source-of-truth); blast the artist list from our own ESP, not from PressRanger. **Swappable** if its data disappoints.

## Zernio — the publishing rail

The social-scheduling API PolyWiz already publishes through (14 platforms; Pinterest wired for organic). Formerly "Late." It's the existing distribution mechanism — no new integration needed for organic; paid is the #181 build.

## The ideas-inbox — where this was incubated

**Repo:** `ideas-inbox` (`JuergenB/ideas-inbox`). The capture→research→evaluate→graduate pipeline this concept came through. See [02-background-and-context.md](02-background-and-context.md) §4. Relevant lineage: **Idea 007** (paid-ads engine), **Idea 009** (own-the-layer thesis), **Idea 011** (this concept's parent). This repo is Idea 011, graduated.

---

## Summary table — own vs. rent

| System | Own / Rent | Role | Swappable? |
|---|---|---|---|
| **PolyWiz** | Own | The engine — content gen, approval, schedule, publish, ads | ❌ the spine |
| **Artwork Archive (Airtable)** | Own | System-of-record: open-call + submission data + promo tables | ❌ the data hub |
| **Zernio** | Rent (API) | Publishing rail (14 platforms) | ⚠️ replaceable rail |
| **PressRanger** | Own (lifetime) | Journalist-DB feed + pitch radar (discovery) | ✅ yes — one feed |
| **Press wires** (EIN / eReleases / PR Gold) | Pay-per-use | Distribution, shopped per release by story tier | ✅ yes — per release |
| **Listing boards & partners** | Mostly free | Where we register calls to harvest intent | ✅ yes — many |

The design job ahead is to make the **own** column a real, usable tool — and keep the **rent** column at arm's length so any single vendor change costs us a config edit, not a rebuild.
