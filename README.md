# What Should I Ask For? — the Lesko Help member needs assessment

A private clarity tool for Lesko Help members. Matthew's rule is **one
problem = one call sheet** — but most members can't yet name their problems.
This quiz does exactly one thing: it walks them through every topic the
community covers, helps them recognize *"oh — this is my problem, and that,
and that,"* and hands back **their list: every problem named, in priority
order — each with a ready-to-copy question in the member's own voice**
("I'm in Maryland (ZIP 21201). About me: Single parent · Veteran. I'm
behind on rent and afraid of eviction — where can I get help?"). Location
and who-they-are are baked into every question automatically.

It deliberately does **not** give answers, program directories, phone
numbers, or scripts — that's the community's job, later. Every row carries
the same three-step proposal:

- **copy the question** and paste it in the **Questions Channel**,
- **read the quick guide** for that problem (every quiz option mirrors a
  posted community guide),
- **bring it to a Call Sheet Class** — where one problem becomes one call
  sheet.

The quiz: **15 topic pages that mirror the community's guide spaces
one-for-one** (home & housing, bills/debt/money, food & everyday needs,
health care, family, seniors, veterans, disability, work & career,
business, nonprofit, cars & transportation, school, taxes, legal & safety)
with 86 pickable problems, an **"Other" box on every screen**, urgency
triage (eviction notice, shutoff, no food → **Today**), who-you-are flags
(veteran, single parent, 60+, tribal, rural…) that become a *"say who you
are, every time you ask"* note, free-text problems in the member's own
words, print, and copy-as-text. Plus 5 finishing pages — progress bar over
all 20. Three tabs: The Quiz / My List / Privacy. A solid frame in the four
brand colors runs around the whole app.

Priority tiers ride on the card suits — sequence words, never time
promises: **♥ Do this first · ♦ Then work on these · ♠ After that ·
♣ When you're steady.**

Copy notes (per Giulia): never call it *free* (members pay for the
community), never call it a *grant quiz* (it asks about problems, not
grants), the list promises only clarity — not "who to call" or "what to
say" — and don't route members to the AI Grant Researcher from here; the
Questions Channel, the quick guides and Call Sheet Classes are the doors.

## Privacy model (same as the Credit Score Coach)

- Pure static HTML/JS — no backend, no accounts, no analytics.
- Answers and the list live only in the member's browser (`localStorage`).
- The tool never asks for SSN, account numbers, or contact info, and says so.
- An "Erase everything" button lives under **03 · Privacy**.

## Files

- `index.html` — the entire app (styles, data, logic). System fonts only, so
  nothing breaks inside a Mighty Networks iframe embed.

The catalog lives in `index.html`: `NEEDS` (one object per problem),
`GUIDES` (every posted community guide URL, harvested via the community
MCP — each problem's `comm` references its guide), `PAGES`, and `FLAGS`.
Note: `NEEDS` entries still carry full `say`/`fed`/`local`/`human`/`tip`
call-sheet data, verified August 2026 — it is **deliberately not rendered**
in this app. It's the raw material for the later call-sheet step, so don't
delete it.

## Data currency

Program data in the (unrendered) call-sheet fields verified **August
2026**. Dead programs excluded: ACP, federal Emergency Rental Assistance,
LIHWAP, FEMA COVID funeral assistance, IRS Direct File, the SAVE plan.
ACF links use the new `acf.gov` domain.

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
