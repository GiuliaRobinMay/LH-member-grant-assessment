# What Should I Ask For? — the Lesko Help call-sheet builder

A free, private needs-assessment tool for Lesko Help members. Members answer six
short questions about what's going on in their life, and the tool builds a
personal **call sheet**: a priority-ordered list of problems, each with

- **Say this on the phone** — the exact ask, in Matthew's
  "financial assistance, never grants" language
- **Federal help** — the national programs and how to apply
- **State & local help** — the finders (211, FindHelp, Community Action, state
  directories) pointed at the member's own state and ZIP
- **Go talk to a human** — the free counselor/mentor/caseworker whose job is
  this exact problem (HUD housing counselors, SCORE mentors, VSOs, Area
  Agencies on Aging, legal aid…)
- **In Lesko Help** — the community spaces and classes for that topic

Plus: an urgency triage (eviction notice, shutoff, no food → jumps to
**Today**), personal-situation boosters ("Because of who you are" — veteran,
single parent, 60+, tribal, rural, already-on-SNAP, etc.), free-text problems
in the member's own words, progress tracking, print, and copy-as-text.

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

## Deploying

Any static host works. To mirror the Credit Score Coach setup: create a
Netlify site from this repo (or GitHub Pages), then embed the URL in a
Mighty Networks space in the **Lesko Toolbox** collection.
