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

# Getting More Artists to Apply

<div style="font-family: 'Raleway'; font-weight: 300; font-size: 1.0em; color: var(--body); margin-top: 14px; max-width: 820px;">A simpler way to spread the word about our open calls — and, for the first time, actually keep track of it.</div>

<div style="display: flex; gap: 8px; margin-top: 26px; flex-wrap: wrap; justify-content: center;">
  <span style="background: #ff6b1a18; border: 1px solid #ff6b1a33; border-radius: 20px; padding: 4px 14px; font-family: 'Outfit'; font-size: 0.55em; color: var(--a); font-weight: 400;">For the Not Real Art / Artsville team</span>
  <span style="background: #ff6b1a18; border: 1px solid #ff6b1a33; border-radius: 20px; padding: 4px 14px; font-family: 'Outfit'; font-size: 0.55em; color: var(--a); font-weight: 400;">Plain-English overview</span>
</div>

---

<!-- _class: bg-glow-orange -->

### Where We Stand

# We're Great at Running Calls. The Word Doesn't Get Out.

<div style="display: flex; gap: 16px; margin-top: 20px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--g); border-radius: 10px; padding: 18px 22px;">
    <div style="font-family: 'Outfit'; font-weight: 600; font-size: 0.9em; color: var(--g); margin-bottom: 8px;">What works</div>
    <div style="font-size: 0.8em; color: var(--body); line-height: 1.7;">We pick a theme, open the call, choose the work, and put on a great show. We do this well, every time.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--r); border-radius: 10px; padding: 18px 22px;">
    <div style="font-family: 'Outfit'; font-weight: 600; font-size: 0.9em; color: var(--r); margin-bottom: 8px;">What doesn't</div>
    <div style="font-size: 0.8em; color: var(--body); line-height: 1.7;">Telling artists the call is open. Today that's mostly one email to our own list — and not much else.</div>
  </div>
</div>

<div style="margin-top: 18px; background: var(--s); border: 1px solid var(--b); border-left: 2px solid var(--a); border-radius: 8px; padding: 15px 20px; font-size: 0.84em; color: var(--body); line-height: 1.6;">If only a small group hears about the call, only a small group applies. We're leaving the front door half-closed.</div>

---

<!-- _class: bg-dots -->

### Why It Matters

# More Artists Hear → More Artists Apply

<div style="font-size: 0.86em; color: var(--body); margin-top: 8px; max-width: 880px; line-height: 1.6;">The number of artists who apply is the single biggest thing we can grow. And it touches almost everything we care about:</div>

<div style="display: flex; gap: 14px; margin-top: 20px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.84em; color:var(--a); margin-bottom:6px;">A stronger show</div>
    <div style="font-size: 0.74em; color: var(--body); line-height: 1.6;">More applications means more great work to choose from.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.84em; color:var(--a); margin-bottom:6px;">A bigger community</div>
    <div style="font-size: 0.74em; color: var(--body); line-height: 1.6;">Every artist who applies is someone new in our world.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.84em; color:var(--a); margin-bottom:6px;">A better story</div>
    <div style="font-size: 0.74em; color: var(--body); line-height: 1.6;">"Hundreds applied from across the country" helps with grants and sponsors.</div>
  </div>
</div>

<div style="margin-top: 18px; font-size: 0.78em; color: var(--m); line-height: 1.55; text-align: center;">We already saw this work: when we paid to put a call in front of more people, a lot more people responded.</div>

---

<!-- _class: bg-glow-orange -->

### The Reality Today

# Scattered, Slow, and Nobody Wrote It Down

<div style="display: flex; gap: 14px; margin-top: 20px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.82em; color:var(--y); margin-bottom:6px;">Dozens of places</div>
    <div style="font-size: 0.74em; color: var(--body); line-height: 1.6;">There are <strong>60+ websites</strong> where artists look for open calls — and most are free to post on.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.82em; color:var(--y); margin-bottom:6px;">All in one person's head</div>
    <div style="font-size: 0.74em; color: var(--body); line-height: 1.6;">Posting is done one at a time — by one teammate who's learned where and how. There's no written process, no backup, and nothing to hand the next person.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.82em; color:var(--y); margin-bottom:6px;">No record</div>
    <div style="font-size: 0.74em; color: var(--body); line-height: 1.6;">Ask "did we post the new call to that site?" — and nobody can say for sure.</div>
  </div>
</div>

<div style="margin-top: 18px; background: var(--s); border: 1px solid var(--b); border-left: 2px solid var(--r); border-radius: 8px; padding: 15px 20px; font-size: 0.82em; color: var(--body); line-height: 1.6;">So it's scattered, it's slow, and we can't see what got done. Good effort just disappears.</div>

---

<!-- _class: bg-hero -->

### The Idea

# One Simple Helper That Does the Busy-Work

<div style="font-size: 0.92em; color: var(--body); margin-top: 14px; max-width: 860px; line-height: 1.65;">What if one simple web page took the tedious part off your plate <em>and</em> remembered everything?</div>

<div style="margin-top: 22px; background: var(--s); border: 1px solid var(--b); border-left: 2px solid var(--blue); border-radius: 10px; padding: 20px 26px;">
  <div style="font-size: 0.95em; color: var(--t); line-height: 1.7;">You tell it the <strong style="color:var(--t); font-weight:600;">exhibition</strong>. It looks up <strong style="color:var(--t); font-weight:600;">everywhere we should post</strong>, writes the <strong style="color:var(--t); font-weight:600;">words for each place</strong>, and keeps a <strong style="color:var(--t); font-weight:600;">checklist of what's done</strong>.</div>
</div>

<div style="margin-top: 18px; font-size: 0.8em; color: var(--m); line-height: 1.55; text-align: center;">Think of it as a really good assistant who never forgets a step — not a robot that does it all without you.</div>

---

<!-- _class: bg-grid -->

### How It Would Work

# Five Simple Steps

<div style="display: flex; flex-direction: column; gap: 10px; margin-top: 14px;">
  <div class="row" style="background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 12px 20px; display:flex; gap:16px; align-items:center;">
    <div style="font-family:'Outfit'; font-weight:700; color:var(--a); font-size:1.1em; min-width: 20px;">1</div>
    <div style="font-size: 0.78em; color: var(--body); line-height: 1.5;"><strong>Pick the exhibition.</strong> Paste the link to the open call.</div>
  </div>
  <div class="row" style="background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 12px 20px; display:flex; gap:16px; align-items:center;">
    <div style="font-family:'Outfit'; font-weight:700; color:var(--a); font-size:1.1em; min-width: 20px;">2</div>
    <div style="font-size: 0.78em; color: var(--body); line-height: 1.5;"><strong>It pulls in the details</strong> — title, deadline, description — automatically.</div>
  </div>
  <div class="row" style="background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 12px 20px; display:flex; gap:16px; align-items:center;">
    <div style="font-family:'Outfit'; font-weight:700; color:var(--a); font-size:1.1em; min-width: 20px;">3</div>
    <div style="font-size: 0.78em; color: var(--body); line-height: 1.5;"><strong>It hands you ready-to-use words</strong> for each place we post to — already worded to fit that site.</div>
  </div>
  <div class="row" style="background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 12px 20px; display:flex; gap:16px; align-items:center;">
    <div style="font-family:'Outfit'; font-weight:700; color:var(--a); font-size:1.1em; min-width: 20px;">4</div>
    <div style="font-size: 0.78em; color: var(--body); line-height: 1.5;"><strong>You post it, then tick it off.</strong> One click to copy, one click to open the site.</div>
  </div>
  <div class="row" style="background: var(--s); border: 1px solid var(--b); border-radius: 9px; padding: 12px 20px; display:flex; gap:16px; align-items:center;">
    <div style="font-family:'Outfit'; font-weight:700; color:var(--g); font-size:1.1em; min-width: 20px;">5</div>
    <div style="font-size: 0.78em; color: var(--body); line-height: 1.5;"><strong>Anyone can look later</strong> and see exactly what was done.</div>
  </div>
</div>

---

<!-- _class: bg-glow-green -->

### Your Shortlist

# Pick Your Go-To Places Once

<div style="font-size: 0.86em; color: var(--body); margin-top: 8px; max-width: 880px; line-height: 1.6;">There are dozens of places — you don't need all of them. <strong>Bookmark the ones we actually use</strong> (maybe ten, maybe more), and the helper focuses on those every time. No re-deciding for every call.</div>

<div style="display: flex; gap: 14px; margin-top: 20px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 18px 22px;">
    <div style="font-family: 'Outfit'; font-weight: 600; font-size: 0.85em; color: var(--t); margin-bottom: 8px;">⭐ Your shortlist</div>
    <div style="font-size: 0.76em; color: var(--body); line-height: 1.7;">The places you trust and use. The helper shows these first, every single call.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 18px 22px;">
    <div style="font-family: 'Outfit'; font-weight: 600; font-size: 0.85em; color: var(--m); margin-bottom: 8px;">The rest, still there</div>
    <div style="font-size: 0.76em; color: var(--body); line-height: 1.7;">The full list stays available when you want it — but it's out of your way day to day.</div>
  </div>
</div>

<div style="margin-top: 18px; font-size: 0.78em; color: var(--m); line-height: 1.55; text-align: center;">Choose your go-to list once; it sticks — for everyone, on every call.</div>

---

<!-- _class: bg-glow-orange -->

### Let's Be Honest

# It Won't Magically Fill Out Every Website

<div style="font-size: 0.86em; color: var(--body); margin-top: 8px; max-width: 880px; line-height: 1.6;">Most of these websites need a person to paste the words in and click "submit" — that's just how they're built. We're not promising a robot that does it all on its own.</div>

<div style="display: flex; gap: 16px; margin-top: 20px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--g); border-radius: 10px; padding: 18px 22px;">
    <div style="font-family: 'Outfit'; font-weight: 600; font-size: 0.85em; color: var(--g); margin-bottom: 8px;">What it does</div>
    <div style="font-size: 0.76em; color: var(--body); line-height: 1.7;">Writes the words for you, hands them over ready to paste, opens the right page, and writes down that you did it.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--m); border-radius: 10px; padding: 18px 22px;">
    <div style="font-family: 'Outfit'; font-weight: 600; font-size: 0.85em; color: var(--m); margin-bottom: 8px;">What you still do</div>
    <div style="font-size: 0.76em; color: var(--body); line-height: 1.7;">Paste and click submit. Seconds per site, instead of starting from a blank page each time.</div>
  </div>
</div>

<div style="margin-top: 18px; font-size: 0.8em; color: var(--m); line-height: 1.55; text-align: center;">Less robot, more <strong style="color:var(--body); font-weight:600;">really good assistant</strong>.</div>

---

<!-- _class: bg-glow-green -->

### The Payoff

# For the First Time, We Can See Our Own Work

<div style="display: flex; gap: 14px; margin-top: 20px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.82em; color:var(--g); margin-bottom:6px;">A written-down way to do it</div>
    <div style="font-size: 0.76em; color: var(--body); line-height: 1.6;">The steps live in the tool — so anyone can do it, and it's not stuck in one person's head.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.82em; color:var(--g); margin-bottom:6px;">A real record</div>
    <div style="font-size: 0.76em; color: var(--body); line-height: 1.6;">Every post ticked off — what we did on each site, who did it, and when. "Yes, done on sites 1, 2, 3."</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-radius: 10px; padding: 16px 18px;">
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.82em; color:var(--g); margin-bottom:6px;">See what actually works</div>
    <div style="font-size: 0.76em; color: var(--body); line-height: 1.6;">Each place gets its own unique, trackable link — so we can finally tell which ones really send artists our way.</div>
  </div>
</div>

<div style="margin-top: 18px; background: var(--s); border: 1px solid var(--b); border-left: 2px solid var(--g); border-radius: 8px; padding: 15px 20px; font-size: 0.84em; color: var(--body); line-height: 1.6;">Same effort — but organized, shared, remembered, and no longer dependent on one person.</div>

---

<!-- _class: bg-glow-gold -->

### Where We'd Start

# Try It on One Real Call

<div style="display: flex; gap: 16px; margin-top: 20px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--a); border-radius: 10px; padding: 18px 22px;">
    <span class="tag" style="background:#ff6b1a15; color:var(--a); border:1px solid #ff6b1a33;">Small first step</span>
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.88em; color:var(--t); margin-top:10px;">One call, start to finish</div>
    <div style="font-size: 0.76em; color: var(--body); line-height: 1.6; margin-top: 6px;">We pick the next open call (<em>The Art of Resistance</em>) and run it through the helper from start to finish.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--g); border-radius: 10px; padding: 18px 22px;">
    <span class="tag" style="background:#22c55e12; color:var(--g); border:1px solid #22c55e22;">What we learn</span>
    <div style="font-family:'Outfit'; font-weight:600; font-size:0.88em; color:var(--t); margin-top:10px;">Did it make the day easier?</div>
    <div style="font-size: 0.76em; color: var(--body); line-height: 1.6; margin-top: 6px;">Did the call reach more artists? Was the work less of a chore? We find out before committing to more.</div>
  </div>
</div>

<div style="margin-top: 18px; font-size: 0.8em; color: var(--m); line-height: 1.55; text-align: center;">Small first step, real learning, no big commitment.</div>

---

<!-- _class: bg-glow -->

### A Couple of Things to Talk About

# Two Open Questions — Nothing Decided Yet

<div style="font-size: 0.84em; color: var(--body); margin-top: 8px; max-width: 900px; line-height: 1.6;">As we shape this, there are two questions for the team. Neither needs an answer today — they just help us decide what to build.</div>

<div style="display: flex; gap: 16px; margin-top: 18px;">
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--a); border-radius: 10px; padding: 18px 22px;">
    <div style="font-family: 'Outfit'; font-weight: 600; font-size: 0.88em; color: var(--t); margin-bottom: 8px;">A helper of its own — or part of PolyWiz?</div>
    <div style="font-size: 0.74em; color: var(--body); line-height: 1.65;">PolyWiz is the tool we already use to create and schedule our posts. Should this open-call helper be a <strong>small, standalone tool</strong> that does just this one job — or should it live <strong>inside PolyWiz</strong>? A separate tool keeps PolyWiz simple and focused; building it in keeps everything in one place.</div>
  </div>
  <div style="flex: 1; background: var(--s); border: 1px solid var(--b); border-top: 2px solid var(--blue); border-radius: 10px; padding: 18px 22px;">
    <div style="font-family: 'Outfit'; font-weight: 600; font-size: 0.88em; color: var(--t); margin-bottom: 8px;">Just for us — or for other art groups too?</div>
    <div style="font-size: 0.74em; color: var(--body); line-height: 1.65;">Do we build this <strong>only for ourselves</strong> — or also as something we could one day <strong>offer other galleries and art organizations</strong>?</div>
  </div>
</div>

<div style="margin-top: 16px; font-size: 0.8em; color: var(--m); line-height: 1.6; text-align: center;">We can start small and decide both as we go — building it well keeps every door open.</div>

---

<!-- _class: lead bg-hero -->

<img src="https://raw.githubusercontent.com/JuergenB/polywiz-exhibit-promo-tool/main/presentations/polymash-logo.png" style="position: absolute; top: 34px; left: 44px; width: 52px; border-radius: 11px;" />

# Tell It the Exhibition. It Does the Rest.

<div style="font-size: 0.92em; color: var(--body); margin-top: 14px; max-width: 860px; line-height: 1.65;">It writes the words. You paste and tick the boxes. And — for the first time — we can look back and see exactly what we did to get more artists to apply.</div>

<div style="margin-top: 22px; font-size: 0.8em; color: var(--m);">Let's try it on one call.</div>
