# What Should I Ask For? — the Lesko Help member needs assessment

A free, private needs-assessment tool for Lesko Help members. Members answer six
short questions about what's going on in their life, and get their **results:
one numbered ask per problem**, in priority order, each with

- **Say this on the phone** — the exact ask, in Matthew's
  "financial assistance, never grants" language
- **Federal help** — the national programs and how to apply
- **State & local help** — the finders (211, FindHelp, Community Action, state
  directories) pointed at the member's own state and ZIP
- **Go talk to a human** — the free counselor/mentor/caseworker whose job is
  this exact problem (HUD housing counselors, SCORE mentors, VSOs, Area
  Agencies on Aging, legal aid…)
- **In Lesko Help** — the community spaces and classes for that topic

Plus: an **"Other" box on every choice screen** (needs groups, urgency, and
about-you) so problems we didn't list still get their own numbered ask — typed
urgent items jump straight to the Today tier. Also: urgency triage (eviction
notice, shutoff, no food → **Today**), personal-situation boosters ("Because of who you are" — veteran,
single parent, 60+, tribal, rural, already-on-SNAP, etc.), free-text problems
in the member's own words, print, and copy-as-text. (Three tabs — The Quiz / My Results
/ Privacy. The quiz is one small page per topic — 15 topic pages drawn from
the community's Quick Guide spaces and Matthew's reports (home, bills, food &
everyday needs, health/dental/vision, family, seniors, veterans, disability,
work, business, nonprofit, cars, school, legal & safety, pets) with 49
pickable problems in total, plus 5 finishing pages — progress bar over all 20. A solid frame in the four
brand colors runs around the whole app.)

Priority tiers ride on the card suits:
**♥ Today · ♦ This week · ♠ This month · ♣ When you're steady.**

## Privacy model (same as the Credit Score Coach)

- Pure static HTML/JS — no backend, no accounts, no analytics.
- Answers and progress live only in the member's browser (`localStorage`).
- The tool never asks for SSN, account numbers, or contact info, and says so.
- An "Erase everything" button lives under **05 · Privacy**.

## Files

- `index.html` — the entire app (styles, data, logic). System fonts only, so
  nothing breaks inside a Mighty Networks iframe embed.

The program catalog lives in `index.html` inside the `NEEDS` array (one object
per problem card) and `FLAGS` (the because-of-who-you-are boosters). Each item
is `{ n: name, w: what you get, how, url, tel, only: "XX" }` — `{ZIP}` and
`{STATE}` are substituted from the member's answers, and `only` limits an item
to one state (e.g. California's smog-repair fund).

## Data currency

Program data verified **August 2026**. Deliberately excluded because they're
dead: ACP, federal Emergency Rental Assistance, LIHWAP, FEMA COVID funeral
assistance, IRS Direct File, the SAVE plan (members are pointed to the 2026
IDR/RAP changes instead). ACF links use the new `acf.gov` domain.

## Deploying & embedding

Live at **https://leskomemberassessment.netlify.app/** (Netlify, auto-deploys
from this repo — same setup as the Credit Score Coach).

Embed in a Mighty Networks space (Lesko Toolbox collection) with:

```html
<iframe
  src="https://leskomemberassessment.netlify.app/"
  title="What Should I Ask For? — Lesko Help member needs assessment"
  style="width:100%; height:90vh; min-height:900px; border:0; border-radius:16px; background:#faf6ec;"
  loading="lazy"
  allow="clipboard-write">
</iframe>
```

`allow="clipboard-write"` keeps the "Copy as text" button working inside the
iframe; the cream `background` avoids a white flash while it loads. Adjust
`height`/`min-height` to taste — the app scrolls inside the frame.
