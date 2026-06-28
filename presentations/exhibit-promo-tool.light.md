---
marp: true
theme: default
paginate: true
style: |
  @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@400;600;700;800&family=Inter:wght@300;400;500&display=swap');

  :root {
    --a: #e85d0c; --a2: #d14e00;
    --bg: #f8f8f8; --s: #ffffff; --b: #e0e0e0;
    --m: #999; --t: #1a1a1a;
    --g: #16a34a; --r: #dc2626; --y: #d97706;
    --blue: #0177c8; --body: #555; --label: #999;
  }

  * { font-family: 'Inter', 'Outfit', sans-serif; }

  section {
    background-color: #f8f8f8;
    background-image: radial-gradient(ellipse at 50% 50%, transparent 30%, rgba(0,0,0,0.025) 100%);
    color: var(--t); font-family: 'Inter', sans-serif; font-weight: 400;
    padding: 52px 68px; line-height: 1.5;
  }

  h1 { font-family: 'Outfit'; font-weight: 700; font-size: 2.1em; color: var(--t); letter-spacing: -0.02em; line-height: 1.1; margin: 0 0 4px; }
  h2 { font-family: 'Inter'; font-weight: 300; font-size: 1.15em; color: #777; margin: 0 0 18px; }
  h3 { font-family: 'Outfit'; font-weight: 600; font-size: 0.6em; color: var(--m); text-transform: uppercase; letter-spacing: 0.2em; margin: 0 0 4px; }
  strong { color: var(--a); font-weight: 500; }
  em { color: var(--t); font-style: italic; }

  section.lead { display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; }
  section.lead h1 { font-size: 2.6em; color: var(--t); }

  section::after { font-family: 'Outfit'; font-size: 0.6em; color: #ddd; }

  section.bg-glow { background-color: #f8f8f8; background-image: radial-gradient(ellipse at 50% 50%, transparent 25%, rgba(232,93,12,0.06) 100%), radial-gradient(ellipse at 0% 100%, rgba(22,163,74,0.04) 0%, transparent 50%); }
  section.bg-glow-orange { background-color: #f8f8f8; background-image: radial-gradient(ellipse at 50% 50%, transparent 25%, rgba(232,93,12,0.07) 100%); }
  section.bg-glow-green { background-color: #f8f8f8; background-image: radial-gradient(ellipse at 50% 50%, transparent 25%, rgba(22,163,74,0.06) 100%), radial-gradient(ellipse at 100% 0%, rgba(22,163,74,0.04) 0%, transparent 50%); }
  section.bg-glow-gold { background-color: #f8f8f8; background-image: radial-gradient(ellipse at 50% 50%, transparent 25%, rgba(217,119,6,0.06) 100%); }
  section.bg-dots { background-color: #f8f8f8; background-image: radial-gradient(ellipse at 50% 50%, transparent 25%, rgba(1,119,200,0.05) 100%), radial-gradient(circle, rgba(0,0,0,0.04) 1px, transparent 1px); background-size: auto, 24px 24px; }
  section.bg-grid { background-color: #f8f8f8; background-image: radial-gradient(ellipse at 50% 50%, transparent 25%, rgba(217,119,6,0.05) 100%), linear-gradient(rgba(0,0,0,0.04) 1px, transparent 1px), linear-gradient(90deg, rgba(0,0,0,0.04) 1px, transparent 1px); background-size: auto, 48px 48px, 48px 48px; }
  section.bg-hero { background-color: #f8f8f8; background-image: radial-gradient(ellipse at 50% 50%, transparent 20%, rgba(1,119,200,0.08) 100%); }

  header { text-align: right; padding: 0; margin: 0; }
  header img { margin: 0; }

  .tag { font-family: 'Outfit'; font-weight: 600; font-size: 0.55em; letter-spacing: 0.12em; text-transform: uppercase; padding: 3px 10px; border-radius: 4px; display: inline-block; }

  table { width: 100%; border-collapse: collapse; font-size: 0.6em; margin-top: 6px; }
  th { font-family: 'Outfit'; font-weight: 600; text-transform: uppercase; letter-spacing: 0.08em; font-size: 0.82em; color: var(--m); text-align: left; padding: 7px 12px; border-bottom: 1px solid var(--b); }
  td { padding: 8px 12px; border-bottom: 1px solid var(--b); color: var(--body); vertical-align: top; }
  tr:last-child td { border-bottom: none; }
  table, thead, tbody, tr, th, td { background: transparent !important; }

  .row:hover { background: #f0f0f0; }
  .row { transition: background 0.2s; border-radius: 6px; padding: 0 8px; }

  a { color: inherit; }
header: ''
footer: ''
---


<!-- _class: lead bg-hero -->
<!-- _paginate: false -->

<img src="https://raw.githubusercontent.com/JuergenB/polywiz-exhibit-promo-tool/main/presentations/polymash-logo.png" style="position: absolute; top: 34px; left: 44px; width: 52px; border-radius: 11px;" />

# The Exhibit Promo Tool

<div style="font-family: 'Raleway'; font-weight: 300; font-size: 0.98em; color: var(--body); margin-top: 14px; max-width: 820px;">A concept project to promote our open calls and exhibitions — and attract more submissions. This deck explains the project, what we already own, and the <strong>decisions to make before we build.</strong></div>

<div style="display: flex; gap: 8px; margin-top: 26px; flex-wrap: wrap; justify-content: center;">
  <span style="background: #ff6b1a18; border: 1px solid #ff6b1a33; border-radius: 20px; padding: 4px 14px; font-family: 'Outfit'; font-size: 0.55em; color: var(--a); font-weight: 400;">Concept · Pre-build</span>
  <span style="background: #ff6b1a18; border: 1px solid #ff6b1a33; border-radius: 20px; padding: 4px 14px; font-family: 'Outfit'; font-size: 0.55em; color: var(--a); font-weight: 400;">Graduated from Idea 011</span>
  <span style="background: #ff6b1a18; border: 1px solid #ff6b1a33; border-radius: 20px; padding: 4px 14px; font-family: 'Outfit'; font-size: 0.55em; color: var(--a); font-weight: 400;">Not Real Art · Artsville · Arterial</span>
</div>

---

<!-- _class: bg-dots -->

### What This Project Is

# A Concept, Graduated From the Ideas Inbox

<div style="font-size: 0.84em; color: var(--body); margin-top: 8px; max-width: 920px; line-height: 1.6;">The <a href="https://github.com/JuergenB/ideas-inbox">ideas-inbox</a> captures, researches, and evaluates ideas before they become projects. <a href="https://github.com/JuergenB/ideas-inbox/tree/main/ideas/011-pressranger-outreach-playbook">Idea 011 — Owned Promotion & PR Engine</a> reached <strong>"Recommend Pilot"</strong> — so it graduates here into its own concept repo to be designed properly.</div>

<div style="display: flex; gap: 12px; margin-top: 20px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--g); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.8em; color:var(--g); margin-bottom:6px;">✓ Done in this repo</div>
    <div style="font-size: 0.68em; color: var(--body); line-height: 1.6;">Background & education · the systems map · the 66-channel directory · a PressRanger product deep-dive · the build-vs-integrate analysis · a decision register</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--y); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.8em; color:var(--y); margin-bottom:6px;">◷ Still to come</div>
    <div style="font-size: 0.68em; color: var(--body); line-height: 1.6;">Use cases · user-centric tasks · the press-release / PressRanger integration design · the per-call promotion checklist — <em>all blocked on the key decisions</em></div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--m); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.8em; color:var(--m); margin-bottom:6px;">⊘ Not yet</div>
    <div style="font-size: 0.68em; color: var(--body); line-height: 1.6;">No code. No build. We are deliberately deciding <strong>what</strong> to build and <strong>where</strong> before writing any.</div>
  </div>
</div>

---

<!-- _class: bg-glow-orange -->

### Why We're Doing This

# We Run Open Calls — We Don't Promote Them

<div style="font-size: 0.84em; color: var(--body); margin-top: 8px; max-width: 900px; line-height: 1.6;">We're excellent at <em>running</em> open calls and exhibitions, and almost nothing promotes them beyond our own small email list. <strong>Submission volume is the lever</strong> — it compounds into better shows, a bigger community, press leverage, and nonprofit public support.</div>

<div style="display: flex; gap: 16px; margin-top: 18px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family: 'Outfit'; font-weight: 600; font-size: 0.82em; color: var(--a); margin-bottom: 6px;">No repository</div>
    <div style="font-size: 0.7em; color: var(--body); line-height: 1.6;">Press & outreach contacts live in inboxes and people's heads.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family: 'Outfit'; font-weight: 600; font-size: 0.82em; color: var(--a); margin-bottom: 6px;">No active owner</div>
    <div style="font-size: 0.7em; color: var(--body); line-height: 1.6;">Promotion is whoever-has-time — so it mostly doesn't happen.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family: 'Outfit'; font-weight: 600; font-size: 0.82em; color: var(--a); margin-bottom: 6px;">No PR cadence</div>
    <div style="font-size: 0.7em; color: var(--body); line-height: 1.6;">Releases go out sporadically — not before, on, and after each call.</div>
  </div>
</div>

<div style="margin-top: 16px; background: var(--s); border: 1px solid var(--b); border-left: 2px solid var(--g); border-radius: 8px; padding: 13px 18px; font-size: 0.76em; color: var(--body); line-height: 1.6;">The evidence it works: the grant campaigns over-performed because we ran <strong>Facebook ads to the landing pages</strong>. Open calls deserve the same treatment — measured, this time. <a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/01-why-promote-open-calls.md" style="color:var(--m);">→ research/01-why-promote-open-calls.md</a></div>

---

<!-- _class: bg-hero -->

### The Framing That Decides Everything

# It's Three Layers, Not One App

<div style="font-size: 0.82em; color: var(--body); margin-top: 8px; max-width: 900px; line-height: 1.55;">Most of the "which app do we build this on?" debate dissolves once you see this isn't one application — it's three layers, each with a different natural home.</div>

<div style="display: flex; gap: 14px; margin-top: 20px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--blue); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:700; font-size:0.92em; color:var(--blue); margin-bottom:6px;">Engine</div>
    <div style="font-size: 0.68em; color: var(--body); line-height: 1.6;">Content gen → approval → schedule → publish → paid ads.<br><span style="color:var(--g);">Already exists: <strong style="color:var(--g);">PolyWiz</strong></span></div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--a); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:700; font-size:0.92em; color:var(--a); margin-bottom:6px;">Data + CRM</div>
    <div style="font-size: 0.68em; color: var(--body); line-height: 1.6;">Contacts, pitches, coverage, registry, open-call & submission data.<br><span style="color:var(--g);">Partly exists: <strong style="color:var(--g);">Airtable</strong></span></div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--y); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:700; font-size:0.92em; color:var(--y); margin-bottom:6px;">Packaging</div>
    <div style="font-size: 0.68em; color: var(--body); line-height: 1.6;">Who it's for, how it's sold: internal · multi-brand · white-label.<br><span style="color:var(--y);">A choice — <strong style="color:var(--y);">not yet made</strong></span></div>
  </div>
</div>

<div style="margin-top: 16px; font-size: 0.76em; color: var(--m); line-height: 1.5; text-align: center;">"Which app" becomes "<strong style="color:var(--body); font-weight:600;">which layer goes where</strong>" — and only packaging is genuinely open.</div>

---

<!-- _class: bg-glow -->

### What We Already Own

# The Stack Is the Spine — We Rent Only Inputs

<div style="display: flex; gap: 10px; margin-top: 18px; align-items: stretch;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 14px 15px; text-align: center;">
    <div style="font-family:'Outfit'; font-weight:700; font-size:0.84em; color:var(--a);">PressRanger</div>
    <div style="font-size: 0.6em; color: var(--m); margin-top:5px;">owned feed — swappable</div>
    <div style="font-size: 0.62em; color: var(--body); line-height: 1.5; margin-top: 6px;">Journalist DB + pitch radar</div>
  </div>
  <div style="display:flex; align-items:center; color:var(--m); font-size:1.2em;">→</div>
  <div style="flex: 1.5; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--blue); border-radius: 10px; padding: 14px 15px; text-align: center;">
    <div style="font-family:'Outfit'; font-weight:700; font-size:0.84em; color:var(--blue);">PolyWiz</div>
    <div style="font-size: 0.6em; color: var(--m); margin-top:5px;">the engine — our spine</div>
    <div style="font-size: 0.62em; color: var(--body); line-height: 1.5; margin-top: 6px;">Gen · approval · schedule · publish (14 platforms) · ads</div>
  </div>
  <div style="display:flex; align-items:center; color:var(--m); font-size:1.2em;">←</div>
  <div style="flex: 1.2; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 14px 15px; text-align: center;">
    <div style="font-family:'Outfit'; font-weight:700; font-size:0.84em; color:var(--g);">Artwork Archive</div>
    <div style="font-size: 0.6em; color: var(--m); margin-top:5px;">Airtable system-of-record</div>
    <div style="font-size: 0.62em; color: var(--body); line-height: 1.5; margin-top: 6px;">Open-call records + submissions = conversion signal</div>
  </div>
</div>

<div style="display: flex; gap: 14px; margin-top: 16px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 12px 16px; font-size: 0.66em; color: var(--body); line-height: 1.55;"><strong>"Open Call" is already a scaffolded PolyWiz campaign type</strong> — disabled, ~1 hour to enable organic. Press release = a new output format. Paid ads = <a href="https://github.com/JuergenB/polywiz-app/issues/181">polywiz-app#181</a>.</div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 12px 16px; font-size: 0.66em; color: var(--body); line-height: 1.55;">Same principle as <a href="https://github.com/JuergenB/ideas-inbox/tree/main/ideas/009-arterial-owned-platform">Idea 009</a>: <strong>own the engine; rent only swappable inputs.</strong> <a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/03-related-systems.md" style="color:var(--m);">→ research/03-related-systems.md</a></div>
</div>

---

<!-- _class: bg-dots -->

### The Demand Layer

# 66 Verified Channels, Mostly Free & Unused

<div style="font-size: 0.8em; color: var(--body); margin-top: 6px; max-width: 900px; line-height: 1.55;">Before building anything, we mapped where to promote calls and find funding — every row drives artists back to <em>our own</em> submission page. <strong>43 of 66 are free.</strong></div>

<div style="display: flex; gap: 11px; margin-top: 16px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 13px 14px;">
    <div style="font-family:'Outfit'; font-weight:700; font-size:1.35em; color:var(--g);">24</div>
    <div style="font-size: 0.58em; color: var(--m); line-height:1.3; margin-top:3px;">Fundraising / grants / donor</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 13px 14px;">
    <div style="font-family:'Outfit'; font-weight:700; font-size:1.35em; color:var(--a);">18</div>
    <div style="font-size: 0.58em; color: var(--m); line-height:1.3; margin-top:3px;">Open-call listings</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 13px 14px;">
    <div style="font-family:'Outfit'; font-weight:700; font-size:1.35em; color:var(--blue);">15</div>
    <div style="font-size: 0.58em; color: var(--m); line-height:1.3; margin-top:3px;">Media / PR amplifiers</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 13px 14px;">
    <div style="font-family:'Outfit'; font-weight:700; font-size:1.35em; color:var(--y);">6</div>
    <div style="font-size: 0.58em; color: var(--m); line-height:1.3; margin-top:3px;">Partner orgs / councils</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 13px 14px;">
    <div style="font-family:'Outfit'; font-weight:700; font-size:1.35em; color:var(--a2);">3</div>
    <div style="font-size: 0.58em; color: var(--m); line-height:1.3; margin-top:3px;">Paid-ads channels</div>
  </div>
</div>

<div style="margin-top: 14px; background: var(--s); border: 1px solid var(--b); border-left: 2px solid var(--a); border-radius: 8px; padding: 12px 18px; font-size: 0.7em; color: var(--body); line-height: 1.55;">Each row carries an action URL, cost, self-service level, effort — and a ready-made <strong>UTM slug</strong> so every promoted link is attributable. <a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/04-channel-directory.md" style="color:var(--m);">→ research/04-channel-directory.md</a> <a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/arts-master-resource.csv" style="color:var(--m);">· arts-master-resource.csv</a></div>

---

<!-- _class: bg-glow-orange -->

### The Reality Check on PressRanger

# It Can't Be a Live Feed — CSV Export Only

<div style="font-size: 0.82em; color: var(--body); margin-top: 8px; max-width: 900px; line-height: 1.6;">PressRanger's media database + CRM + AI would cost <strong>$3K–$40K/yr</strong> elsewhere, and we own it on a lifetime deal. But for <em>integrating</em> it, the deep-dive surfaced a hard constraint:</div>

<div style="display: flex; gap: 16px; margin-top: 18px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--r); border-radius: 10px; padding: 16px 20px;">
    <div style="font-family: 'Outfit'; font-weight: 600; font-size: 0.8em; color: var(--r); margin-bottom: 6px;">No API · No Zapier · No webhooks</div>
    <div style="font-size: 0.7em; color: var(--body); line-height: 1.6;">The only integration is a Claude MCP server — and it exposes <strong>only your own companies + draft releases</strong>, never the contact database.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--y); border-radius: 10px; padding: 16px 20px;">
    <div style="font-family: 'Outfit'; font-weight: 600; font-size: 0.8em; color: var(--y); margin-bottom: 6px;">Egress = manual CSV, tier-capped</div>
    <div style="font-size: 0.7em; color: var(--body); line-height: 1.6;">~4,000 records/mo on our Tier 3. So integration is a <strong>periodic batch ETL</strong> — export → Airtable import — not a live sync.</div>
  </div>
</div>

<div style="margin-top: 16px; background: var(--s); border: 1px solid var(--b); border-left: 2px solid var(--g); border-radius: 8px; padding: 13px 18px; font-size: 0.76em; color: var(--body); line-height: 1.6;">Plus noisy keyword-matched beats and patchy emails (one test: <strong>8 of 100</strong> contacts had an email). Use it for <strong>discovery</strong>; own the CRM ourselves. <a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/05-pressranger-deep-dive.md" style="color:var(--m);">→ research/05-pressranger-deep-dive.md</a></div>

---

<!-- _class: bg-glow-green -->

### Build vs. Integrate

# No Clone to Fork — Build Thin on Our Stack

<div style="font-size: 0.82em; color: var(--body); margin-top: 8px; max-width: 900px; line-height: 1.6;">A full GitHub sweep found <strong>no forkable PressRanger</strong> — only SEO-spam repos and zero-star hackathon agents. PressRanger's moat is its <em>journalist database</em>, which is proprietary and <em>not our use case</em>: we manage our <strong>own</strong> contacts.</div>

<div style="display: flex; gap: 14px; margin-top: 18px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 15px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.78em; color:var(--g); margin-bottom:6px;">Recommendation</div>
    <div style="font-size: 0.68em; color: var(--body); line-height: 1.6;">Build a <strong>thin CRM on Next.js + Airtable + Claude + n8n</strong>: Contacts · Pitches · Coverage · Registry. Keep PressRanger as a swappable discovery feed.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 15px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.78em; color:var(--blue); margin-bottom:6px;">Don't over-build</div>
    <div style="font-size: 0.68em; color: var(--body); line-height: 1.6;">Adopting a heavyweight CRM (Twenty, EspoCRM) adds a second datastore, auth, and self-host burden to replace what Airtable already does. <strong>Simplicity first.</strong></div>
  </div>
</div>

<div style="margin-top: 14px; font-size: 0.72em; color: var(--m); line-height: 1.5; text-align: center;">Revisit <a href="https://github.com/twentyhq/twenty">Twenty</a> only if we outgrow Airtable. <a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/06-build-vs-integrate-and-oss-landscape.md" style="color:var(--m);">→ research/06-build-vs-integrate-and-oss-landscape.md</a></div>

---

<!-- _class: bg-grid -->

### The Decisions Before We Build

# Seven Questions — One of Them Is the Root

<div style="font-size: 0.82em; color: var(--body); margin-top: 8px; max-width: 900px; line-height: 1.6;">Before use cases or schemas, the team (Scott · Elise · Juergen) has to answer a set of architectural & strategic questions. Most of them lean the same way — <strong>except one, which everything else hangs on.</strong></div>

<div style="margin-top: 18px; background: var(--s); border: 1px solid var(--b); border-left: 2px solid var(--y); border-radius: 10px; padding: 18px 22px;">
  <div style="font-family:'Outfit'; font-weight:700; font-size:1.0em; color:var(--y); margin-bottom:8px;">The root question — Decision 5</div>
  <div style="font-size: 0.86em; color: var(--t); line-height: 1.6;">Are we building <strong style="color:var(--t); font-weight:600;">a tool</strong> (internal, promote our own calls) — or <strong style="color:var(--t); font-weight:600;">a product</strong> (white-label PR-as-a-service for other arts orgs)?</div>
  <div style="font-size: 0.72em; color: var(--m); line-height: 1.55; margin-top: 8px;">Almost every other decision reads "lean X if internal, lean Y if product." Answer this first and the rest resolve.</div>
</div>

<div style="margin-top: 14px; font-size: 0.72em; color: var(--m); line-height: 1.5; text-align: center;">Full reasoning, options, and tradeoffs → <a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/concept/00-key-decisions.md" style="color:var(--body); font-weight:600;">concept/00-key-decisions.md</a></div>

---

<!-- _class: bg-glow -->

### Decision 1 — Where the Engine Lives

# PolyWiz "Campaign Type" — Not a New App

<div style="display: flex; gap: 14px; margin-top: 18px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--g); border-radius: 10px; padding: 16px 18px;">
    <span class="tag" style="background:#22c55e12; color:var(--g); border:1px solid #22c55e22;">Lean ✓</span>
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.84em; color:var(--t); margin-top:10px;">PolyWiz campaign type</div>
    <div style="font-size: 0.66em; color: var(--body); line-height: 1.55; margin-top: 6px;">It already <em>is</em> the engine. "Open Call" is scaffolded; press release = new output format; ads = #181.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.84em; color:var(--m); margin-top:2px;">Artwork Archive utility</div>
    <div style="font-size: 0.66em; color: var(--body); line-height: 1.55; margin-top: 6px;">Holds the data — but has <strong>no</strong> AI gen, publishing, or ads. Building here = rebuilding PolyWiz. It's a <em>data</em> home.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.84em; color:var(--m); margin-top:2px;">Standalone PR app</div>
    <div style="font-size: 0.66em; color: var(--body); line-height: 1.55; margin-top: 6px;">Cleanest separation — and the right shell <em>if</em> we go white-label. Otherwise it duplicates the engine we own.</div>
  </div>
</div>

<div style="margin-top: 16px; background: var(--s); border: 1px solid var(--b); border-left: 2px solid var(--a); border-radius: 8px; padding: 13px 18px; font-size: 0.74em; color: var(--body); line-height: 1.6;"><strong>Data + CRM layer</strong> → a cleanly-namespaced Airtable (the Artwork Archive base). "Artwork Archive as a CRM utility" is true for the <em>data</em>, not the <em>engine</em>.</div>

---

<!-- _class: bg-glow-gold -->

### Decision 5 — The Strategic Fork

# Internal Tool, or White-Label SaaS?

<div style="font-size: 0.8em; color: var(--body); margin-top: 6px; max-width: 900px; line-height: 1.55;">Scott's instinct: <em>"turn it into some kind of service for artists or galleries."</em> And PressRanger is already white-label/reseller-ready — so a service could be largely <strong>resell + our playbook + our brand.</strong></div>

<div style="display: flex; gap: 14px; margin-top: 16px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 15px 17px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.8em; color:var(--m); margin-bottom:6px;">A · Internal only</div>
    <div style="font-size: 0.64em; color: var(--body); line-height: 1.55;">Smallest build, fastest value. Leaves the revenue instinct on the table.</div>
  </div>
  <div style="flex: 1.15; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--g); border-radius: 10px; padding: 15px 17px;">
    <span class="tag" style="background:#22c55e12; color:var(--g); border:1px solid #22c55e22;">Lean ✓</span>
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.8em; color:var(--t); margin-top:8px;">B · Internal now, product-ready</div>
    <div style="font-size: 0.64em; color: var(--body); line-height: 1.55; margin-top:5px;">Prove the playbook on ourselves first; keep data portable + brands agnostic. Low-regret. Most of the "keep-open" work our rules already mandate.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 15px 17px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.8em; color:var(--m); margin-bottom:6px;">C · White-label day one</div>
    <div style="font-size: 0.64em; color: var(--body); line-height: 1.55;">Pays the multi-tenant + billing + support cost <strong>before</strong> the playbook is proven. High risk.</div>
  </div>
</div>

<div style="margin-top: 14px; font-size: 0.7em; color: var(--m); line-height: 1.5; text-align: center;">Review alongside <a href="https://github.com/JuergenB/ideas-inbox/tree/main/ideas/004-multi-tenant-curator-platform">Idea 004 (Multi-Tenant)</a> + <a href="https://github.com/JuergenB/ideas-inbox/tree/main/ideas/009-arterial-owned-platform">Idea 009 (Owned Platform)</a> — white-label PR may belong with those.</div>

---

<!-- _class: bg-grid -->

### Decisions at a Glance

# Seven Leans — All Gated by the Root

<table>
<thead><tr><th>#</th><th>Decision</th><th>Lean</th><th>Gated by</th></tr></thead>
<tbody>
<tr><td>1</td><td>Engine host</td><td><strong>PolyWiz campaign type</strong></td><td>#5</td></tr>
<tr><td>2</td><td>Data / CRM host</td><td><strong>Airtable — Artwork Archive base, namespaced</strong></td><td>#5</td></tr>
<tr><td>3</td><td>One product or two</td><td><strong>Two layered capabilities</strong></td><td>#5</td></tr>
<tr><td>4</td><td>Multi-brand vs. multi-tenant</td><td><strong>Multi-brand now, tenant-ready</strong></td><td>#5</td></tr>
<tr><td>5</td><td>Internal vs. white-label</td><td><strong style="color:var(--y);">Internal now, product-ready — THE ROOT</strong></td><td>—</td></tr>
<tr><td>6</td><td>User surface (Elise)</td><td><strong>Reuse PolyWiz + Airtable; no new app yet</strong></td><td>#5</td></tr>
<tr><td>7</td><td>PressRanger role</td><td><strong>Swappable discovery feed</strong></td><td>settled</td></tr>
</tbody>
</table>

<div style="margin-top: 14px; font-size: 0.74em; color: var(--m); line-height: 1.5; text-align: center;">Answer #5 — even as "tool for now, revisit after Phase 1" — and 1–4 + 6 resolve to these leans.</div>

---

<!-- _class: bg-glow-green -->

### The Recommendation

# The Low-Regret Path

<div style="display: flex; flex-direction: column; gap: 11px; margin-top: 16px;">
  <div class="row" style="background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 13px 20px; display:flex; gap:16px; align-items:flex-start;">
    <div style="font-family:'Outfit'; font-weight:700; color:var(--a); font-size:1.1em;">1</div>
    <div style="font-size: 0.74em; color: var(--body); line-height: 1.55;"><strong>Build the engine capability in PolyWiz</strong> — enable "Open Call," add press-release output, wire the #181 ads pilot. Reversible — it's our engine either way.</div>
  </div>
  <div class="row" style="background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 13px 20px; display:flex; gap:16px; align-items:flex-start;">
    <div style="font-family:'Outfit'; font-weight:700; color:var(--a); font-size:1.1em;">2</div>
    <div style="font-size: 0.74em; color: var(--body); line-height: 1.55;"><strong>Build the thin CRM/registry in a clean Airtable</strong> — Contacts · Pitches · Coverage · Registry. Brand-agnostic, portable — lifts into a tenant base later if needed.</div>
  </div>
  <div class="row" style="background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 13px 20px; display:flex; gap:16px; align-items:flex-start;">
    <div style="font-family:'Outfit'; font-weight:700; color:var(--a); font-size:1.1em;">3</div>
    <div style="font-size: 0.74em; color: var(--body); line-height: 1.55;"><strong>Run Phase 1 on one real call</strong> (<em>Art of Resistance</em>) with a ~$250 paid flight — and measure <strong>cost-per-submission</strong> for the first time.</div>
  </div>
  <div class="row" style="background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 13px 20px; display:flex; gap:16px; align-items:flex-start;">
    <div style="font-family:'Outfit'; font-weight:700; color:var(--a); font-size:1.1em;">4</div>
    <div style="font-size: 0.74em; color: var(--body); line-height: 1.55;"><strong>Defer the white-label decision</strong> until that data exists — then decide tool-vs-product with evidence.</div>
  </div>
</div>

<div style="margin-top: 14px; font-size: 0.72em; color: var(--m); line-height: 1.5; text-align: center;">Every step delivers internal value <em>and</em> is a prerequisite for the product version. Deferring costs nothing.</div>

---

<!-- _class: bg-dots -->

### Read the Full Thinking

# Where Everything Lives

<div style="display: flex; gap: 14px; margin-top: 16px;">

<div style="flex: 1;">
<div style="font-family:'Outfit'; font-weight:600; font-size:0.58em; color:var(--a); text-transform:uppercase; letter-spacing:0.1em; margin-bottom:6px;">Research (the why & what exists)</div>
<div style="font-size: 0.64em; color: var(--body); line-height: 1.9;">
<a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/01-why-promote-open-calls.md">01 · why promote open calls</a><br>
<a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/02-background-and-context.md">02 · background & context</a><br>
<a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/03-related-systems.md">03 · related systems</a><br>
<a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/04-channel-directory.md">04 · channel directory</a> <a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/arts-master-resource.csv" style="color:var(--m);">(+ CSV)</a><br>
<a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/05-pressranger-deep-dive.md">05 · PressRanger deep-dive</a><br>
<a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/06-build-vs-integrate-and-oss-landscape.md">06 · build-vs-integrate landscape</a>
</div>
</div>

<div style="flex: 1;">
<div style="font-family:'Outfit'; font-weight:600; font-size:0.58em; color:var(--y); text-transform:uppercase; letter-spacing:0.1em; margin-bottom:6px;">Concept (the decisions & design)</div>
<div style="font-size: 0.64em; color: var(--body); line-height: 1.9;">
<a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/concept/00-key-decisions.md">00 · key decisions</a> <span style="color:var(--m);">← start here</span><br>
— use cases <span style="color:var(--m);">(to come)</span><br>
— user-centric tasks <span style="color:var(--m);">(to come)</span><br>
— PressRanger integration <span style="color:var(--m);">(to come)</span><br>
— promotion checklist <span style="color:var(--m);">(to come)</span>
</div>
</div>

<div style="flex: 1;">
<div style="font-family:'Outfit'; font-weight:600; font-size:0.58em; color:var(--blue); text-transform:uppercase; letter-spacing:0.1em; margin-bottom:6px;">Upstream lineage</div>
<div style="font-size: 0.64em; color: var(--body); line-height: 1.9;">
<a href="https://github.com/JuergenB/ideas-inbox/tree/main/ideas/011-pressranger-outreach-playbook">Idea 011</a> — this concept's parent<br>
<a href="https://github.com/JuergenB/ideas-inbox/tree/main/ideas/007-polywiz-paid-ads-engine">Idea 007</a> — paid-ads engine<br>
<a href="https://github.com/JuergenB/ideas-inbox/tree/main/ideas/009-arterial-owned-platform">Idea 009</a> — own-the-layer<br>
<a href="https://github.com/JuergenB/ideas-inbox/tree/main/ideas/004-multi-tenant-curator-platform">Idea 004</a> — multi-tenant<br>
<a href="https://github.com/JuergenB/polywiz-app/issues/181">polywiz-app#181</a> — ads epic
</div>
</div>

</div>

---

<!-- _paginate: true -->

# Sources & References
## Clickable — evidence behind this deck

<div style="font-size: 0.6em; line-height: 1.5;">

**This project (repo docs)** — <a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool">github.com/JuergenB/polywiz-exhibit-promo-tool</a> · the [research/](https://github.com/JuergenB/polywiz-exhibit-promo-tool/tree/main/research) folder (01–06) and [concept/00-key-decisions.md](https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/concept/00-key-decisions.md) carry full per-claim sources + confidence flags.

**Parent idea & lineage** — <a href="https://github.com/JuergenB/ideas-inbox/tree/main/ideas/011-pressranger-outreach-playbook">Idea 011 (Owned Promotion & PR Engine)</a> · <a href="https://github.com/JuergenB/ideas-inbox/tree/main/ideas/007-polywiz-paid-ads-engine">007 paid-ads</a> · <a href="https://github.com/JuergenB/ideas-inbox/tree/main/ideas/009-arterial-owned-platform">009 owned platform</a> · <a href="https://github.com/JuergenB/ideas-inbox/tree/main/ideas/004-multi-tenant-curator-platform">004 multi-tenant</a> · <a href="https://github.com/JuergenB/polywiz-app/issues/181">polywiz-app#181 ads epic</a>.

**PressRanger — features, no-API finding, data quality** — <a href="https://pressranger.com/pages/pr-software">pressranger.com/pages/pr-software</a> · <a href="https://pressranger.com/docs">docs (Claude-MCP-only integration)</a> · <a href="https://appsumo.com/products/press-ranger/reviews/">AppSumo reviews (8-of-100 emails; keyword beats)</a>. Full teardown: research/05.

**Wire & software pricing** — <a href="https://www.einpresswire.com/pricing">EIN Presswire ~$149</a> · <a href="https://www.ereleases.com/causewire/">eReleases CauseWire (nonprofit)</a> · <a href="https://www.prezly.com/academy/pr-newswire-pricing">PR Newswire $1,500–3,000</a> · <a href="https://prowly.com/magazine/cision-vs-meltwater/">Cision / Meltwater / Prowly estimates</a>.

**OSS build-vs-integrate** — <a href="https://github.com/twentyhq/twenty">Twenty CRM</a> · <a href="https://github.com/growthenginenowoslawski/coldoutboundskills">coldoutboundskills</a> · <a href="https://github.com/awdeorio/mailmerge">mailmerge</a>. Full landscape + verdicts: research/06.

**Master channel directory (66 verified)** — live build: <a href="https://arterial-art-exhibition-promotion-resources.pplx.app/">arterial-art-exhibition-promotion-resources.pplx.app</a> · data: <a href="https://github.com/JuergenB/polywiz-exhibit-promo-tool/blob/main/research/arts-master-resource.csv">research/arts-master-resource.csv</a>.

</div>

<p style="font-size: 0.6em; color: var(--m); margin-top: 12px;">Pricing & capability claims current June 2026 — verify before quoting. AppSumo tier figures flagged low-confidence; re-verify on the live listing. Full URLs, retrieval dates, and high/medium/low confidence flags live in the verification sections of <strong style="color: var(--body); font-weight: 600;">research/05</strong> and <strong style="color: var(--body); font-weight: 600;">research/06</strong>.</p>

---

<!-- _class: lead bg-hero -->

<img src="https://raw.githubusercontent.com/JuergenB/polywiz-exhibit-promo-tool/main/presentations/polymash-logo.png" style="position: absolute; top: 34px; left: 44px; width: 52px; border-radius: 11px;" />

# One Question Unblocks the Rest

<div style="font-size: 0.85em; color: var(--body); margin-top: 12px; max-width: 880px; line-height: 1.6;">We already own the engine, the data hub, and the feed. The research is done; the decisions are framed. The single thing standing between "questions" and "design" is one answer: <strong>are we building a tool, or a product?</strong></div>

<div style="margin-top: 22px; font-size: 0.72em; color: var(--m);">Answer that, and I can start the use-cases, schema, and integration design. — Juergen Berkessel, Polymash</div>
