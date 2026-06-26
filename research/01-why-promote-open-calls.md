# Why We Promote Open Calls — and Why It Matters

> **Purpose of this document.** This is the education piece. Before anyone designs a tool, everyone touching this project should share one mental model of *why* promoting open calls and exhibitions is worth building for — what an open call is, what "more submissions" actually buys us, and why our current approach leaves value on the table. Everything else in this repo (channels, systems, checklists) is downstream of the reasoning here.

---

## 1. What an open call is, in our context

An **open call** (a.k.a. call for artists / call for entries) is a public invitation for artists to submit work for a juried exhibition, prize, grant, or feature. For **Not Real Art** and **Artsville USA**, a typical call has:

- a **theme** (e.g. *Art of Resistance*),
- a **deadline**,
- **eligibility** rules (medium, geography, career stage),
- usually an **entry mechanism** and sometimes a fee or prize, and
- a **landing / submission page** we own (notrealart.com / artsvilleusa.com).

Critically: **we run our own calls and already own our submission platform.** We are not asking another platform to host our intake. That single fact shapes the entire strategy — we don't need a tool that *runs* calls; we need to *drive artists to the calls we already run*. The test for any promotion channel is **"own-URL vs. forced infrastructure," not "paid vs. free"**: does it let us post our own call and link artists back to *our* submission page?

## 2. The funnel — what "more submissions" is really about

An open call is the top of a funnel that produces nearly everything the organization values:

```
   Reach (people who see the call)
        │   ← this is the leaky step we don't actively work
        ▼
   Submissions (artists who enter)
        │
        ▼
   Selections / Exhibition (the curated show)
        │
        ▼
   Audience, press, sales, sponsors, community, mission impact
```

More submissions at the top is not vanity volume. It compounds into concrete outcomes:

- **Better shows.** A larger, more diverse submission pool means the jury selects from strength. Curation quality is bounded by what comes in the door.
- **A bigger, warmer community.** Every entrant is a relationship — a future newsletter subscriber, repeat entrant, advocate, or buyer. Non-selected artists who had a good experience come back and bring peers.
- **Stronger brand gravity.** Calls that visibly attract many artists signal legitimacy, which attracts *more* artists, press, and sponsors next time. The flywheel is real.
- **Press and sponsor leverage.** "We received N submissions from M countries" is a newsworthy, sponsor-friendly number — but only if N is large enough to be a story.
- **Mission and funding.** For a nonprofit, broad participation is not just marketing; it's evidence of public benefit. (See §6 — it ties directly to 501(c)(3) public-support requirements.)

The point: **submission volume is the lever, and reach is the part of the funnel we currently leave to chance.** We optimize production (intake, judging, the show) and barely touch demand generation.

## 3. The problem — we run calls, we don't promote them

We have built a strong *production* system (enrichment pipeline, submissions, judging, the collection). But outreach still runs almost entirely on **our own email list and personal contacts.** From the Thursday Open Call meeting, three gaps are explicit:

1. **No central repository for press / outreach contacts.** Venues, journalists, podcasts, and open-call sites live in people's heads and inboxes — not a shared, structured system. Knowledge walks out the door.
2. **No active owner.** Promotion is "whoever has time," which means it mostly doesn't happen. There's no accountable surface and no cadence.
3. **No press-release cadence.** Releases go out sporadically, not *before / on / after* each call and show. Scott's stated target is **at least one release a month** — we don't hit it.

The meeting put it bluntly:

> *"We notify the right sources every time we launch a call — because our own email can't be it. It's too weak or small."*

Translation: **our owned email list is real but small.** If reach stops at "blast our own list," the funnel starts narrow every single time. We are capping submissions at the size of an audience we already have, instead of manufacturing new reach for each call.

## 4. The evidence that promotion moves the number

This isn't theoretical. The organization already has a natural experiment: **the grant campaigns over-performed specifically because we ran Facebook ads to the landing pages** — not because of organic luck. When we deliberately bought targeted reach pointed at an aligned landing page, the numbers responded.

The obvious inference: **open calls deserve the same multi-channel treatment** — press + free listings + email + paid social, all pointed at one registration URL, all tagged so we can measure. We have proof the lever works in one context (grants) and we simply haven't pulled it for open calls.

And much of the reach is **free and unused.** Artists actively *go looking* for calls on aggregator boards — EntryThingy, ArtCallEntry, Artwork Archive, ArtConnect, Fractured Atlas — and amplifier media run free opportunity roundups (Hyperallergic's tips line, Colossal's opportunities column). These cost nothing and capture *existing intent* — artists who are already searching for calls like ours. We just aren't posting to most of them today. (The full verified directory is [04-channel-directory.md](04-channel-directory.md).)

## 5. Two kinds of demand — and why you need both

A useful frame for the whole strategy: promotion channels either **harvest existing intent** or **manufacture new intent**.

| | Harvest existing intent | Manufacture new intent |
|---|---|---|
| **Channels** | Free listing boards, our email list, journalist pitches, SEO | Paid social (Meta + Pinterest), retargeting |
| **Who it reaches** | Artists already searching; our warm audience | Artists who weren't looking yet but fit |
| **Cost** | Mostly free / owned | Per-call ad spend (~$150–$300 flights) |
| **Ceiling** | Bounded by how many are already searching + our list size | Bounded by budget and audience size — *expandable* |

Harvesting is necessary but self-limiting: it can only capture demand that already exists. **Paid social is the part that grows the top of the funnel beyond our current reach** — and it's the lever the grant campaigns proved. The two compound: a paid open-call campaign captures entries now, *plus* newsletter signups from non-submitters, *plus* a retargeting pool that makes the **next** call cheaper. Promotion isn't a cost per call; it's an audience asset that accrues.

## 6. Why this matters extra for a nonprofit

For Arterial / Not Real Art as a 501(c)(3), broad participation is more than marketing. Public charities must demonstrate **broad public support** (the public-support test — meaningful backing from many individuals, not a handful of large donors). A disciplined, repeatable outreach engine that consistently brings in many artists and many small supporters is therefore a **compliance and sustainability asset**, not just a growth tactic. The same engine that lifts submissions in the spring repoints at **donors and grant press** in the fall — same machine, different objective.

## 7. Why build a tool instead of "just trying harder"

The gaps in §3 are not effort problems; they're **systems problems.** "Promote more" fails the same way every good intention fails without infrastructure:

- It depends on a person having time → it doesn't happen.
- Knowledge isn't captured → every campaign restarts from scratch.
- Nothing is measured → we can't tell what worked, so we can't improve.

A tool fixes the systemic causes: it makes promotion **repeatable** (the same playbook fires for every call), **owned** (contacts and history live in a repository we control), and **measurable** (every link is tagged, so we finally learn our **cost-per-submission** — a number we have *never* measured because we've never run the spend deliberately).

And we don't need to build it from nothing. **We already own most of the engine** — PolyWiz already turns a URL into approved, scheduled, multi-platform content and even has a *scaffolded "Open Call" campaign type sitting disabled.* The build is mostly *enabling and extending* what exists, plus plugging in cheap commodity inputs we already own (PressRanger). That's what makes this high-leverage: large outcome, small marginal build. The architecture is laid out in [03-related-systems.md](03-related-systems.md).

---

## The thesis in one line

> We are excellent at *running* open calls and poor at *promoting* them; promotion is a solvable **systems** problem; the engine to solve it is one we already own; and the payoff — more submissions, a compounding audience, press leverage, and nonprofit public support — touches nearly everything the organization cares about.

---

### Sources for the claims here
The "three gaps," the "our email is too weak/small" quote, the one-release-a-month target, and the "Facebook-ads-to-landing-pages over-performed" evidence all come from the **Thursday Open Call meeting** and the June 2026 Scott ↔ Juergen email thread, as captured in [Idea 011](https://github.com/JuergenB/ideas-inbox/tree/main/ideas/011-pressranger-outreach-playbook). The free-listing and amplifier channels are verified in [04-channel-directory.md](04-channel-directory.md) and the underlying [arts-master-resource.csv](arts-master-resource.csv).
