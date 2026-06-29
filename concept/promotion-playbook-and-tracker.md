# Brainstorm — From Reference Table to Promotion Playbook & Tracker

> **Status: brainstorm, not a design.** Captured from Juergen's 2026-06-29 brainstorm. Nothing here is decided or specced. It records the *shift in intent* for the tool and an honest feasibility read, so the thinking isn't lost. Pairs with [00-key-decisions.md](00-key-decisions.md) and the reference widget at [research/source-materials/directory-widget.index.html](../research/source-materials/directory-widget.index.html).

---

## The reframe

The Perplexity widget we already built is a **read-only reference + UTM link builder**. It lists the 66 channels, filters them, and generates tagged links — but it **stores nothing**: no favorites, no checklist, no log, no scraping. Refresh and it forgets.

The worry that prompted this: **a lookup table won't get used.** People will glance at it, then go do their own thing — fire off a hundred emails and posts by hand — and we'll have **no record** of what was done, where, or what came back. It's going to be messy.

So the intent shifts: from a **table you read** to a **worklist that does the busy-work and remembers everything.** The one-line description of what we actually want:

> **Tell it the exhibition → it pulls the open-call details → it hands you ready-to-paste text for each place we post → you post and tick it off → we can look back and see what got done.**

This is an **online playbook for promoting each open call** (and later, each exhibition) — that also **records what we're doing.**

## The operator's experience (Juergen's words, kept plain)

1. **Tell me the exhibition.**
2. **Look up everything that needs to be filled out** (for each place we submit to).
3. **Give me a playbook** (ready-to-use content per place).
4. **Keep track of what I've done.**
5. **Let me check off each one** as I complete it.
6. **Let me look afterward and see it being accomplished** (a record + responses).

## The features brainstormed

- **Favorites / shortlist.** Star ~10 open-call places we've actually decided to use, as an *additional, permanent filter*. Permanence lives in **Airtable** (not browser memory). Choose the go-to list once; it sticks.
- **Airtable as the repository of sites.** The 66-channel CSV becomes live Airtable rows (it's already import-shaped). Each row already carries the **"how to submit"** steps — the recipe for preparing content.
- **Scrape + prepare.** A button next to the URL field (today only used for UTM generation) that **scrapes the open-call URL** and **prepares the submission for each place** — i.e. "here's the exhibition, here's the open-call description," tailored to what each site needs.
- **Checklist + log.** A place to check off each submission ("yes, I did this one"), with a timestamp, who did it, and room to record the response later.
- **Review afterward.** A view/dashboard of what was done across the call — so promotion is visible and auditable, not invisible.

## Honest feasibility (the easy parts vs. the trap)

| Piece | Verdict |
|---|---|
| Rebuild the widget as a real app | **Easy** — it's ~800 lines, self-contained. |
| Airtable store for sites + **star ~10 favorites** | **Easy** — "favorite" is one checkbox field; persistence is free. |
| Paste open-call URL → **scrape** → **prepare tailored content per channel** | **Feasible, mostly already built** — PolyWiz already scrapes open calls (deadline / submission URL / eligibility) and generates copy; the per-channel "how to submit" field is the tailoring input. |
| **Checklist + log + review** | **Easy** — each (call × channel) is an Airtable row: status, who, when, notes, response. |
| **Auto-fill / auto-submit the third-party forms** | **The trap.** Most boards have **no API and no automation hook** — manual web forms, many behind logins/CAPTCHAs, all different. Auto-filling arbitrary forms is brittle browser-automation that breaks on any HTML change and often violates ToS. |

### The realistic MVP: assisted + tracked manual submission
Not full automation. The tool **prepares** the right text per place, gives **one-click copy** and **one-click open** of that site's form (human pastes + submits), then **records** it was done. That removes the "scattered / slow / untracked / messy" problem without sinking the project into per-site form-filling fragility. (A handful of boards *might* expose an API — worth checking the favorites specifically — but assume manual.)

## Why this is a better Phase 1 than the abstract "engine"

- It's **concrete** — the people doing the work can picture it and use it day one.
- It directly fixes the stated failure mode (**"won't get used / messy / no record"**).
- It **reuses** what we already own (PolyWiz scrape + AI; the CSV; Airtable).
- It quietly resolves an open design question: the **operational checklist *is* the user-facing surface** for Elise's team — a thin app over Airtable, with PolyWiz doing the scrape-and-prepare behind it. (Touches [Decision 1 (host)](00-key-decisions.md) and [Decision 6 (surface)](00-key-decisions.md): the surface is this tool; the engine behind it is still PolyWiz.)

## Open questions (for later, not now)

- One playbook for **open calls** first; **submissions/exhibitions** later — same shape?
- Where the app lives (thin standalone over Airtable, vs. a PolyWiz screen) — see [Decision 1](00-key-decisions.md).
- How "prepared content per channel" handles channels that need an **account/login** vs. instant forms.
- Whether favorites are per-brand (Not Real Art vs. Artsville) or shared.
- What "response tracking" captures (did they post it / did press reply / did submissions rise).

## How this threads into the presentation
This concrete "tell-it-the-exhibition, it preps everything, you tick the boxes" story is the **plain-English heart of the stakeholder deck** ([presentations/exhibit-promo-tool-stakeholders.md](../presentations/exhibit-promo-tool-stakeholders.md)) — far more graspable for non-technical folks than "engine + data hub." See that deck for the shareable version.
