# The Channel Directory — Where We Promote & Fund

> **Purpose.** This is the field guide to [`arts-master-resource.csv`](arts-master-resource.csv): the verified, US-focused directory of **66 channels** for promoting our own open calls and exhibitions and finding funding. It answers the operational question behind the whole concept: *once we decide to promote a call, where exactly do we post it?*

---

## What the data is

A team-refreshed, source-verified master list, originally built by **Perplexity Computer** (live page visits, not memory) and refreshed by the team. Action URLs were verified **2026-06-12**, with additional call-listing platforms added & verified **2026-06-18/25**. It's structured to be **Airtable-import-ready** — this CSV is the seed for the *Listing-Site & Partner Registry* table that lives in the Artwork Archive base.

**66 channels · 15 columns each.**

### The organizing test: own-URL vs. forced infrastructure
Every listing channel here passes one test — **it lets us post our own call and link artists back to *our* submission page** (notrealart.com / artsvilleusa.com). We are not handing intake to anyone else. The filter is *"own-URL vs. forced infrastructure," not "paid vs. free."* (See [why §1](01-why-promote-open-calls.md).)

## The five workstreams

| Count | Workstream | What it's for |
|---:|---|---|
| **24** | **Fundraising/Grants/Donor** | Phase-2 funding destinations — grant discovery, donor platforms, giving days. The fall campaign's target list. |
| **18** | **Open-Call Listing** | The core Phase-1 boards where artists *go looking* for calls. Post here to harvest existing intent. |
| **15** | **Media/PR Amplifier** | Press/editorial outlets that run opportunity roundups or take tips (Hyperallergic, Colossal, Create! Magazine, Booooooom…). |
| **6** | **Partner Org/Council** | Arts orgs & councils (NYFA, Americans for the Arts, Artist Communities Alliance, state/regional councils). |
| **3** | **Paid-Ads Channel** | Paid placement — including **Google Ad Grants (free $10k/mo** for eligible nonprofits). |

## What each row tells you (the 15 columns)

| Column | Why it matters for the tool |
|---|---|
| **Name** | Channel name. |
| **Workstream** | One of the five above — the primary filter/segment. |
| **What it is** | One-line description of the channel. |
| **Action URL** | The exact page where you post/submit a call. |
| **Cost (to organizer)** | What *we* pay to list — **43 of 66 are free** (or free at our usage tier). |
| **Self-service level** | How much friction to post: *Instant web form* (11) → *Account required* (30) → *Email/pitch required* (10) → *Manual review/approval* (rest). Drives effort estimates. |
| **How to submit a call** | Step-by-step posting instructions — the operational gold for a checklist or automation. |
| **Effort/time** | Rough effort to post. |
| **Audience/reach** | Who sees it / how big. |
| **Geography** | Global / US-national / regional. |
| **Best for** | Call types this channel suits (open call, exhibition, grant…). |
| **Cadence fit** | One-off post vs. recurring. |
| **Notes/gotchas** | Caveats, fee thresholds, confirmations. |
| **utm_source (lowercase slug)** | **The handshake with PolyWiz** — a ready-made UTM source slug per channel, so every promoted link is attributable by channel and we can measure cost-per-submission. |
| **Source URL & date verified** | Provenance + verification date. |

## How the tool will use this

The directory is not just a reference doc — it's a **functional input** to the engine:

1. **As the registry table.** Imported into Airtable, it becomes the *Listing-Site & Partner Registry* that the [playbook](../concept/README.md) reads — each open call's checklist is generated from "which of these channels apply."
2. **As the UTM dictionary.** The `utm_source` slug column means every channel has a stable tag. PolyWiz builds the tagged landing link per channel; analytics roll up **submissions by channel** → the cost-per-submission number we've never had.
3. **As a prioritized worklist.** Default sort = **Free + Instant self-service + Low effort on top.** That's the "Quick-Start Shortlist" — the handful of free, instant boards to hit for *every* call before spending a dollar.

## The interactive version

A self-contained HTML widget over this exact data lives at [`source-materials/directory-widget.index.html`](source-materials/directory-widget.index.html) — filterable/sortable table, a Quick-Start Shortlist, a Fall-Campaign funding view, and a **live UTM link builder** (paste a landing URL → each row auto-fills its tagged submit link, organic vs. paid). It's a working prototype of the "registry + UTM builder" behavior the real tool would internalize. A team-refreshed hosted copy was published at `arterial-art-exhibition-promotion-resources.pplx.app`.

## Caveats on the data

- **Cost & self-service reflect the organizer's action** (posting a call), recorded only from what was visible on each page. *"confirm"* means it couldn't be confirmed from the page.
- **Pricing was current as of June 2026** — verify before quoting or spending.
- It's **US-focused** by design (our audience), though many channels are global.

---

### Related
- The **why** these channels matter: [01-why-promote-open-calls.md](01-why-promote-open-calls.md) §4–5 (free listings harvest existing intent; paid manufactures new intent).
- The **systems** that consume this data: [03-related-systems.md](03-related-systems.md) (Artwork Archive registry table + PolyWiz UTM handshake).
- Full source URLs & retrieval dates for every channel: the `Source URL & date verified` column in the CSV, plus Idea 011's `research/sources.md` and `research/submission-platforms.md`.
