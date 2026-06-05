# Tomorrow's Brief — 2026-06-02 Session Recap
### Read this before opening anything else.

---

## COMMITS NEEDED BEFORE YOU DO ANYTHING

Two repos have uncommitted work from tonight. Run these first.

### 1. WhollyFare-Website
The rebase-merge ghost is back. Clear it, then commit and push:
```
cd C:\Users\timhi\Documents\GitHub\Whollyfare\Whollyfare-Website
del /F /Q .git\index.lock
rmdir /S /Q .git\rebase-merge
git add -A
git commit -m "2026-06-02: NEXT_STEPS updates, WhollyBare/WhollyCare brand finalization"
git push origin main
```
Last confirmed commit: `3e28eae` (WhollyBare brand named, WhollyCare free-always, NEXT_STEPS master list)
Tonight added: minor NEXT_STEPS.md edits. Nothing else in this repo changed tonight.

### 2. Sentir Solutions Site (its own repo — different from Sentir_Consulting root)
This one has significant uncommitted changes from tonight:
```
cd C:\Users\timhi\Documents\GitHub\Sentir_Consulting\sentir-solutions-site
git add -A
git commit -m "2026-06-02: WhollyBare rename across all pages, WhollyCare health advocacy shell, two-group brand segmentation, whollybare/ sub-site"
git push origin main
```
What changed: about.html, brands.html, index.html, investors.html, mission.html,
whollycare/index.html (rebuilt as health advocacy), whollyfare.html, whollypaws/index.html,
whollyware/index.html + new whollybare/ folder (personal care brand sub-site).

### 3. Sentir_Consulting root (NOT a git repo yet)
The WhollyCare blueprint lives at:
`C:\Users\timhi\Documents\GitHub\Sentir_Consulting\whollycare-app\WHOLLYCARE_BLUEPRINT.md`
It's not tracked anywhere. When you're ready:
```
cd C:\Users\timhi\Documents\GitHub\Sentir_Consulting
git init
git add -A
git commit -m "2026-06-02: WhollyCare manifesto + blueprint, WhollyBare naming decision"
```

---

## WHAT TO REVIEW BY SITE

---

### WhollyFare App — share.streamlit.io
**Status:** Live. Two good commits from tonight already pushed (pre-rebase issue).
**Priority: TEST THE FULL LOOP BEFORE BUILDING ANYTHING**

Full end-to-end test sequence (do this first session home):
1. Admin → upload a PDF circular → Claude Vision extracts → preview → Save
2. Admin → Kroger API pull for Charlottesville
3. This Week → does a plan generate from real sale prices?
4. Review & Approve → approve a meal, swap one, skip one
5. Shopping List → items organized by store, quantities correct?
6. Ledger → Found Money recorded, net of trip costs shown?

**Known risk areas to probe:**
- Recipe steps (Haiku API) — confirm model `claude-haiku-4-5-20251001` not returning 404
- Shopping list quantity pooling — was fixed, verify it held
- Buy-Off HTML rendering — was fixed, verify
- Plan generation when no household_id in session

**What to build next (after test passes):**
- Priority 2: National Demo tab in Admin (6th tab, 5-metro loader, multi-metro PDF)
- Priority 3: Market Intelligence PDF upgrade (holding company grouping + 🟢/🟡/🔴 indicators)
- Priority 4: Admin user management UI (promote pilot households by email)

Full priority list: see `NEXT_STEPS.md` in this repo.

---

### Sentir Solutions Site — sentirsolutions.github.io/sentir-solutions-site
**Status:** Changes uncommitted (see above). Push before reviewing.

**What changed tonight:**
- Every page updated: WhollyCare (personal care) → WhollyBare across all HTML
- `brands.html` — major restructure:
  - New headline: "Four brands earn. One proves we mean it."
  - Household Spending Family label over WhollyFare / WhollyWare / WhollyPaws / WhollyBare
  - New dark navy WhollyCare mission block below the four cards — Adjacent Mission framing, three jobs, founding story hook, FREE badge, waitlist CTA
  - Footer updated to include WhollyCare® (Free)
- `index.html` — brand description updated to reflect two-group architecture
- `investors.html`, `about.html`, `mission.html` — WhollyBare rename throughout

**What to review visually after pushing:**
- brands.html — does the two-group layout read right? Does the WhollyCare block feel distinct enough?
- index.html — does the platform description make sense with the new framing?
- Navigation links — whollycare/ and whollybare/ both exist as sub-sites now

---

### WhollyCare Site — new shell tonight
**Location:** `sentir-solutions-site/whollycare/index.html`
**Theme:** Deep navy/teal — `#081420` dark, `#1A8FA8` accent. Distinct from all other brands.

**What's in it:**
- Hero: "The healthcare system wasn't built to explain itself. We will."
- FREE banner (green) — prominent, persistent message
- Founding story section (dark bg) — Tim's wife + daughter, first-person
- Three Jobs cards: Appointment Prep / Insurance Denial / Specialist Navigation
- Not/Is comparison (red ✕ / green ✓ boxes)
- Insurance denial spotlight with the three stats (80% / 40-60% / 180 days)
- Sincere Strategy table applied to healthcare
- Full manifesto section
- Waitlist CTA (free, no spam promise)
- Footer links all five Wholly brands

**What to review:**
- Does the founding story section hit right? It uses "my wife" and "my daughter" — confirm you're comfortable with that level of personal detail on a public page
- The waitlist form is cosmetic (no backend) — that's fine for now, just a shell
- WhollyCare is explicitly "coming after WhollyFare Series A" in the CTA copy

---

### WhollyBare Site — moved from whollycare/
**Location:** `sentir-solutions-site/whollybare/index.html`
**Theme:** Purple/violet — carried over from the original personal care design

**What's in it:**
- Same personal care brand content, now correctly branded WhollyBare™
- Ingredient-transparent pricing across CVS, Walgreens, Ulta, Target, Walmart
- Cruelty-free, vegan, fragrance-free, paraben-free filters
- Same "Coming Soon" positioning

**What to review:**
- The old `whollycare/` folder still exists (now WhollyCare health advocacy)
- `whollybare/` is new — confirm links from brands.html and nav point correctly
- Note: other brand sub-sites (whollypaws/, whollyware/) still link to `whollycare/` in their footers — those links now correctly go to the health advocacy page. Verify that feels right or update to link to whollybare/ for the personal care context.

---

### WhollyPaws / WhollyWare Sub-sites
**No content changes tonight.** Footer links were updated to point whollycare/ (now health advocacy).
**Quick check:** footer of each still has correct brand links.

---

## PORTFOLIO LOCKED — FOR REFERENCE

| Brand | Mission | Model | Status |
|---|---|---|---|
| WhollyFare® | Grocery price optimization + meal planning | Subscription (Free–$19/mo, one membership) | Active pilot, Phase 1 |
| WhollyBare™ | Personal care & beauty — ingredient-transparent, honest pricing | Subscription | Blueprint + shell site |
| WhollyPaws™ | Pet food + supplies optimization | Subscription | Blueprint + shell site |
| WhollyWare™ | Household non-perishables | Subscription | Blueprint + shell site |
| WhollyCare® | Health advocacy — appointment prep, insurance denials, specialist navigation | **Free. Always.** | Blueprint + shell site |

**The investor line:** Four brands earn through the Sincere Strategy. WhollyCare proves we mean it.

---

## THE TIMELINE (don't lose sight of this)

- **2-4 months:** Potential round 2 at current employer
- **Now:** WhollyFare pilot data + Sentir Consulting pipeline
- **Summer 2026:** Investor conversations need to be active
- **The demo:** 5-metro zip-switching (needs national demo tab built)
- **The proof:** Real pilot receipts from real households (needs end-to-end test to pass first)

---

*WhollyFare® · Sentir Solutions® LLC · Charlottesville, VA*
*Generated: 2026-06-02 end of session*

---

## WhollyCare Pillar Work — Structure to Build Next Session

Tim's direction: WhollyCare needs its own air on sentir-solutions. Not a footnote to the four 
spending brands — a separate pillar with its own visual identity and framing.

### Three structural moves (to implement next session):

**1. Two named sections on brands.html**
- Section A: "The Wholly Platform" — 4 brand cards, subscription engine, household spending
- Section B: "The WhollyCare Mission" — full-width, dark navy, no pricing, no Coming Soon badge
  Opening line: *"Free. Because it should be."*

**2. Nav treatment — separate from brand links**
WhollyCare gets a visually distinct nav item with a green FREE badge, not grouped with WhollyBare etc.
Signals at a glance: this is categorically different.

**3. The bridge sentence between the two sections**
> "Four brands apply the Sincere Strategy to your grocery bill, your medicine cabinet, your pets, 
> and your pantry. WhollyCare applies it to the conversation your doctor, your insurer, and your 
> specialist are having about you — whether you're in the room or not."

That line is the pillar. It earns WhollyCare its own section without diminishing the four brands.

### What to do with it on sentir-solutions homepage (index.html):
- Two-row brand display: row 1 = four spending brands, row 2 = WhollyCare alone, full width
- Different background color for row 2 (the dark navy from the WhollyCare site theme)
- No subscription pricing shown — just the mission line and FREE badge

### The investor read on this architecture:
"We built a platform company that earns on four categories of household spending,
and gives away the fifth thing — healthcare advocacy — because the families we serve
can't afford for it to cost anything. That's not a loss leader. That's the proof of character."
