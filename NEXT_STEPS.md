# WhollyFare® — Next Steps Master List
### As of 2026-06-02 | Session recap: national scale confirmed, WhollyCare defined, job situation understood

---

## Context That Changes Everything

Tim's company is mid-restructure. CFO-driven. Survived round 1. Round 2 is likely in 2-4 months.
This is not a hobby anymore — it's a timeline. Every session from here has a job to do:
**move the investor conversation forward, or generate Sentir Consulting revenue.** Nothing else.

---

## THE ONE RULE

Fix before you add. The end-to-end loop must work before anything new goes in.
If a pilot friend can't use WhollyFare without Tim holding their hand, the pilot data is worthless.

---

## Priority 1 — End-to-End Test (Task #54) — DO THIS FIRST

**The full weekly loop, unassisted:**
1. Admin → upload PDF circular → Claude Vision extracts → preview → save
2. Admin → Kroger pull (or confirm platform items already loaded)
3. This Week → plan generates with real sale prices
4. Review & Approve → approve/swap/skip works correctly
5. Shopping List → items organized by store, quantities correct
6. Ledger → Found Money recorded, net of trip costs shown

**Known risk areas to probe:**
- Plan generation when platform_flyer_items exist but household_id is missing
- Shopping list quantity pooling (was fixed — verify it held)
- Sunday Buy-Off HTML rendering (was fixed — verify)
- Ledger net vs. gross math when trip costs are zero
- Recipe steps loading (Haiku API call — confirm model ID is `claude-haiku-4-5-20251001`)

Do this in Charlottesville, using the real app at share.streamlit.io.
If something breaks, fix it before touching anything else.

---

## Priority 2 — National Demo Tab (Admin page, Tab 6)

**The investor demo pitch: switch zip codes in real-time, show 5 cities, generate a multi-metro report.**

Build order:
1. New tab `🌎 National Demo` in `ui/pages/11_Admin.py`
2. **Section 1 — Market Loader:** One row per metro with pre-filled location IDs, "Pull API" button, status badges (✓ API / ✓ PDFs / ⚠ missing), and suggested PDF stores with clickable flyer URLs
3. **Section 2 — Per-Market Dashboard:** 5-card grid after data loads — items count, categories, top 3 sale items, last-pulled timestamp
4. **Section 3 — Generate National Report:** One button → multi-metro PDF with holding company grouping and 🟢/🟡/🔴 brand score indicators → downloads as `whollyfare_national_demo_YYYY-MM-DD.pdf`

**Confirmed Kroger location IDs (already wired in store_directory.py):**

| Metro | Banner | Location ID |
|---|---|---|
| Charlottesville VA | Kroger | `02900359` |
| Charlotte NC | Harris Teeter | `09700205` |
| Denver CO | King Soopers | `62000115` |
| Chicago IL | Marianos | `53100503` |
| Los Angeles CA | Ralphs | `70300022` |

Also: Food 4 Less (LA, Kroger value banner) = `70400770` — add as 16th banner, add LA store entry.

**PDF stores to manually upload per market (Tim does this day-of demo):**
See `INVESTOR_DEMO_BRIEF.md` in this repo for full list with URLs.

---

## Priority 3 — Market Intelligence PDF Upgrade

Upgrade `app/core_logic/market_intelligence_report.py`:
- Group report by **holding company** (Kroger Co., Ahold Delhaize, Albertsons Cos., etc.)
- Per-brand scores within each holding company
- Visual indicators: 🟢 beating portfolio avg + market avg / 🟡 mixed / 🔴 lagging
- Multi-metro version: accept list of metros, one section per metro, summary comparison at end
- Downloads as: `whollyfare_national_demo_YYYY-MM-DD.pdf`

---

## Priority 4 — Admin User Management UI

Currently Tim runs SQL to promote pilot users: `UPDATE profiles SET tier = 'meal_planner' WHERE email = '...';`

Build a simple admin tab (or subtab in existing Admin page):
- Text input: enter email address
- Dropdown: select tier (free / meal_planner / health_guard / full_table)
- Button: "Update tier"
- Table: show all profiles with email, tier, created_at, trial status

This is needed before Tim can onboard pilot households without touching Supabase directly.

---

## Priority 5 — Pilot Onboarding

Before Tim hands WhollyFare to a pilot friend, they need to be able to:
1. Create an account
2. Set up their household (members + dietary needs)
3. Add their local stores in Grocer Hub
4. Understand that Tim loads the weekly circulars (they don't)
5. Generate their first plan
6. Get to the Shopping List

Options:
- In-app walkthrough (tooltip-style or modal sequence)
- Printed one-pager PDF that Tim gives them
- Both

At minimum: a one-pager. Tim should be able to hand it to someone and leave the room.

---

## Priority 6 — Sentir Consulting Revenue (TIME-SENSITIVE)

**This is now urgent.** 2-4 month window before potential job change.

What Sentir Consulting sells: AI strategy and implementation consulting.
What it needs to generate revenue: a live pipeline.

Action items:
- Update sentir-solutions.com with current positioning (reflects new portfolio)
- WhollyFare as proof of concept / "what we build for clients"
- Direct outreach list — who in Tim's network needs AI strategy right now?
- Case study framing: "We built a national grocery pricing platform in 8 weeks with one developer and an AI system."
- LinkedIn should quietly reflect Sentir Solutions as active (not just side project)

---

## Priority 7 — Tonight's Dinner Polish (`0_This_Week.py`)

Primary daily retention mechanic. People come back because they're cooking.
Add:
- Cook time estimate
- Ingredient count
- "Already made this?" toggle (marks meal as completed, won't re-suggest)
- Clearer route to the full recipe steps in Recipe Library

---

## Priority 8 — Supabase Plan Persistence

Plans are lost on browser refresh — session-only today.
Production path: save to `meal_plans` + `meal_plan_meals` on generation.
This is required before pilot households use it unsupervised (their plan will vanish if they close the tab).

---

## Priority 9 — Contact Form Email

Gmail App Password setup for the contact form in Help & FAQ.
Goes in Streamlit Cloud secrets: `CONTACT_EMAIL_USER` + `CONTACT_EMAIL_PASS`.
Generate at: myaccount.google.com → Security → App passwords (requires 2FA).

---

## Git State Note

Every session starts with this check:

```
cd C:\Users\timhi\Documents\GitHub\Whollyfare\Whollyfare-Website
del /F /Q .git\index.lock
rmdir /S /Q .git\rebase-merge
git add -A
git commit -m "2026-06-02: [description]"
```

The `.git\rebase-merge` directory keeps appearing empty but Windows-held.
Run `rmdir /S /Q` from cmd before every commit session. It's empty — safe to remove.

---

## WhollyCare — Parked, Vision Locked

**Free. No subscription. No advertising. Non-negotiable.**

Blueprint is written: `Sentir_Consulting/whollycare-app/WHOLLYCARE_BLUEPRINT.md`

Build after WhollyFare Series A. The combination — earns on groceries, gives away health advocacy — is the character argument for investors.

Note: Sentir_Consulting directory is NOT a git repo. WhollyCare blueprint is saved locally but not committed. Fix: run `git init` in that directory, or move the file somewhere that IS tracked.

---

## Sentir Solutions Portfolio (Locked)

| Brand | What it is | Status |
|---|---|---|
| WhollyFare® | Grocery price optimization + meal planning | Active pilot, Phase 1 |
| WhollyBare™ | Personal care & beauty — ingredient-transparent, honest pricing (CVS, Walgreens, Ulta) | Blueprint only |
| WhollyPaws™ | Pet food + supplies optimization | Blueprint only |
| WhollyWare™ | Household non-perishables | Blueprint only |
| WhollyCare® | Free health advocacy platform | Blueprint written, not yet built |

---

## The Demo Script (when you walk into the room)

~4 minutes. No slides.

1. Open app → Account → zip = `22901` (Charlottesville) → Grocer Hub shows local stores + live prices
2. Switch zip to `28201` (Charlotte) → Harris Teeter + Food Lion appear. "Different city. Same app."
3. `80202` (Denver) → King Soopers
4. `60601` (Chicago) → Marianos
5. `90012` (LA) → Ralphs Fresh Fare
6. Admin → National Demo tab → show per-market data cards
7. "Generate National Report" → PDF downloads in seconds
8. Open PDF → holding company grouping, brand scores, 5 cities

Key lines:
- *"One developer account. 2,800+ stores. 15 banner brands."*
- *"We don't need to build for scale — we're already at scale. We need households to catch up."*
- *"Food Lion beat Kroger in Charlottesville this week. The algorithm doesn't care who has the API deal."*

---

*WhollyFare® · Sentir Solutions® LLC · Charlottesville, VA*
*Last updated: 2026-06-02*
