# Task Template — Secondary navigation on the product detail (desktop modal)

Export version: **2026-10-14_1045**
Prototype file: `product-detail-secondary-nav.html` (same bundle, open in any browser; no server needed).
Figma reference: https://www.figma.com/design/FNpNrYsGIQFSH2pb5xHFyS/Product-detail-2026?node-id=7545-428059

> **Key information is missing ⚠️** — fields marked `MISSING ⚠️` were not provided by the requester. Items marked *(proposal)* were suggested during the session and are NOT confirmed. Please reach out to the design department to finalize them.

---

## Problem statement

Under the gallery of the Kosik product detail (desktop modal) there are four equal-width grey blocks (Popis produktu, Složení, Podobné produkty, Produkty značky). They are anchor links that scroll to a section, but they look like inert buttons/labels (low affordance), they scroll away with the page, and nothing shows which section the customer is currently in.

Why this matters (root cause / evidence): `MISSING ⚠️` — no research, analytics or complaints were provided showing customers fail to find or use these sections.

## Value

- **For the customer** — *(proposal, unconfirmed)* find ingredients/nutrition and alternatives faster; always know where they are on a long page; less scrolling to get back to the navigation.
- **For the business** — `MISSING ⚠️` *(hypothesis: more visits to Složení / Podobné produkty / Produkty značky, which supports substitution when a product is not right and basket size via brand and similar products)*. Needs confirming with the product owner.

## Measurement of success

Requester gave no metric. Proposal to confirm or sharpen with the owner:

- **Customer-wise (usability)** *(proposal)*
  - Click-through on the secondary navigation (share of product-detail views with at least one nav click), per variant.
  - Scroll depth: share of views reaching Složení and Podobné produkty (needs a baseline from the current page).
  - Qualitative: can customers find ingredients/allergens in a task test (time to find, success rate).
- **Business-wise** *(proposal)*
  - Guardrail: no drop in add-to-basket rate on the product detail, and no drop in clicks on variants and the cross-sell block in the right column ("Další varianty", "Lidé často kupují společně") — a nav that pulls attention must not cannibalise them.
  - Upside to watch: clicks/add-to-basket from "Podobné produkty" and "Produkty značky".
  - Target values: `MISSING ⚠️`. Baseline from the current page: `MISSING ⚠️`.
- **Instrumentation in the prototype:** a click logs `[analytics] pd_secondary_nav_click { variant, tab }` to the browser console. Event name is a proposal, not an agreed tracking plan.
- **A/B setup** — `MISSING ⚠️` (which variant(s) go to test, sample size, duration).

**How will customers find out about this?** No announcement should be needed: it replaces an existing control in place and is self-explanatory. Informing customers is `MISSING ⚠️` / not decided (when, who, how, how long).

## Limitations

- Prototype data: the product "Agrola Jogurt z Jižních Čech Meruňka" is not in the kit's captured payloads. It is cloned from a sample dairy product, so **the photo (a mozzarella), nutrition values and ingredients are sample data**. The description text is taken from the Figma frame. Price per kg is computed as 99,50 Kč/kg (the Figma frame shows 229,45 Kč/kg, which does not match 19,90 Kč for 200 g).
- Variants ("Další varianty") and the cross-sell block on the right are not reproduced with the Figma content; the right column shows the production components with the kit's sample data.
- Counts on the chips/tabs (e.g. "8" similar products) come from the widgets, which load after the modal opens (simulated 300 ms), so counts appear shortly after open. In production the counts need to be available without loading the carousels first (`MISSING ⚠️` — confirm API/data source). "Složení" count is nutrition rows plus parameter rows ("10 položek"); the counting rule is a proposal.
- Browser-only, no real back end. Scroll-spy needs verification against real, taller content and lazy-loaded blocks (sections shifting height changes the active tab).
- Technical owner/constraints for the real implementation (framework version, sticky offsets with the real modal header): `MISSING ⚠️`.

## Requirements

Aligned with the design docs of the kit (mobile first, accessibility, "never hide necessary information"):

- Mobile first: works from 375 px. Variants 1 and 2 are a sticky, horizontally scrollable bar that keeps the active item centred; variant 3 is a vertical accordion list.
- Variants 1 and 2 are sticky while scrolling inside the modal (and the page) and show the current section (scroll-spy, `aria-current`). Clicking an item smooth-scrolls to the section and offsets for the sticky bar.
- Variant 2 uses an icon plus a text label (never icon-only) and counts.
- Variant 3: accordions with chevrons, "Popis produktu" open by default, count shown as subtitle.
- Touch targets at least 40 px (chips 40 px, tabs 48 px). Keyboard: items are real links in tab order; native focus is kept.
- Colors, radius, typography from the design system tokens only. No timeouts.
- Unresolved design-department decisions: see notes.md ("Open design questions"). Further requirements `MISSING ⚠️`.

## Resources

- Figma: https://www.figma.com/design/FNpNrYsGIQFSH2pb5xHFyS/Product-detail-2026?node-id=7545-428059 (fileKey FNpNrYsGIQFSH2pb5xHFyS, node 7545:428059)
- Starting template: kit `dist/product-detail-standalone.html` (changes live in the product-detail component's tab navigation + the app region).
- Research / analytics / baseline numbers / PRD: `MISSING ⚠️`

## More information and notes

See `notes.md` in this bundle.
