# Task Template — Secondary navigation on the product detail (desktop modal)

Export version: **2026-10-14_1101** (supersedes 2026-10-14_1057 and 2026-10-14_1045)
Prototype file: `product-detail-secondary-nav.html` (same bundle, open in any browser; no server needed).
Figma reference: https://www.figma.com/design/FNpNrYsGIQFSH2pb5xHFyS/Product-detail-2026?node-id=7545-428059

> **Key information is missing ⚠️** — fields marked `MISSING ⚠️` were not provided by the requester. Please reach out to the design department to finalize them.

---

## Problem statement

Under the gallery of the Kosik product detail (desktop modal) there are four equal-width grey blocks (Popis produktu, Složení, Podobné produkty, Produkty značky). They are anchor links that scroll to a section, but they look like inert buttons/labels (low affordance), they scroll away with the page, and nothing shows which section the customer is currently in.

Why this matters: the requester believes customers open the product detail to learn more, mainly the product description and the ingredients/nutrition values, and that this information builds trust. The navigation currently makes that information harder to discover than it should be. Evidence (research, analytics, complaints) that customers fail to find or use these sections: `MISSING ⚠️`.

## Value

- **For the customer** — finds the information they came for (description, ingredients, nutrition values, allergens) quickly, knows where they are on a long page, and does not have to scroll back to the top to navigate. Better informed, so more confident in the purchase.
- **For the business** — hypothesis from the requester: easier discovery of the information sections leads to more trust in the product, which leads to a higher add-to-cart rate on the product detail (more conversion). Not yet validated. Business impact in money terms (revenue, margin): `MISSING ⚠️`.

## Measurement of success

**Primary success metric (requester): add-to-cart rate from the product detail** (share of product-detail views that end in an add to cart), compared between the current navigation and the chosen variant. Target uplift: `MISSING ⚠️`. Baseline: `MISSING ⚠️`.

- **Supporting metrics (customer-wise / usability)**
  - Tab click-through: share of product-detail views with at least one secondary-navigation click, per variant.
  - Scroll depth / section reach: share of views reaching or opening Popis produktu and Složení (the sections the hypothesis is about), and Podobné produkty.
  - Qualitative: can customers find ingredients and allergens in a task test (time to find, success rate) — `MISSING ⚠️` whether this will be run.
- **Guardrails (business-wise)**
  - Clicks on variants ("Další varianty") and the cross-sell block ("Lidé často kupují společně") in the right column must not drop: the navigation must not pull attention away from them.
  - Add-to-cart rate must not drop in any variant.
  - Clicks/add-to-cart from "Podobné produkty" and "Produkty značky" are watched as a secondary effect.
- **Instrumentation in the prototype:** every navigation click logs `[analytics] pd_secondary_nav_click { variant, tab }` to the browser console (variant is `original`, `tabs`, `chips` or `dstabs`). Event name is a proposal, not an agreed tracking plan. Add-to-cart events are not instrumented in the prototype.
- **A/B setup** (which variants are tested, sample size, duration): `MISSING ⚠️`.

**How will customers find out about this?** No announcement should be needed: it replaces an existing control in place and is self-explanatory. Whether and how to inform customers (when, who, how, how long): `MISSING ⚠️`.

## Limitations

- Prototype data: the product "Agrola Jogurt z Jižních Čech Meruňka" is not in the kit's captured payloads. It is cloned from a sample dairy product, so **the photo (a mozzarella), nutrition values and ingredients are sample data**. The description text is taken from the Figma frame. Price per kg is computed as 99,50 Kč/kg (the Figma frame shows 229,45 Kč/kg, which does not match 19,90 Kč for 200 g).
- Variants ("Další varianty") and the cross-sell block on the right are not reproduced with the Figma content; the right column shows the production components with the kit's sample data.
- Counts on variants 1 and 2 (e.g. "8" similar products) come from widgets that load after the modal opens (simulated 300 ms), so the counts appear shortly after open. In production the counts need to be available without loading the carousels first (`MISSING ⚠️` — data source). The "Složení" count is nutrition rows plus parameter rows ("10 položek"); the counting rule is a proposal.
- Variant 3 (DS Tabs look) shows plain labels without counts: the DS Tabs component has no count slot, and four labels with counts do not fit the column. It uses the component for navigation (scroll), not for panel switching, which deviates from the DS Tabs behaviour and needs design confirmation.
- Browser-only, no real back end. Scroll-spy (variants 1 and 2) needs verification against real, taller content and lazy-loaded blocks.
- Technical owner/constraints for the real implementation: `MISSING ⚠️`.

## Requirements

Aligned with the design docs of the kit (mobile first, accessibility, "never hide necessary information"):

- Mobile first: works from 375 px. Variants 1, 2 and 3 are a sticky, horizontally scrollable bar; all sections stay visible (variants 1 and 2 keep the active item centred).
- Variants 1, 2 and 3 are sticky while scrolling inside the modal (and the page) and show the current section (scroll-spy; `aria-current` in 1 and 2, `aria-selected` in 3). Clicking an item smooth-scrolls to the section and offsets for the sticky bar.
- Variant 2 uses an icon plus a text label (never icon-only) and counts.
- Variant 3 uses the design-system Tabs component for the look, with scroll-to-section behaviour (no panel switching). Accessibility consideration and the deviation from DS Tabs: see notes.md.
- Touch targets at least 40 px (chips 40 px, tabs 48 px). Keyboard: items are real links or tabs in tab order; native focus is kept.
- Colors, radius, typography from the design system tokens only. No timeouts.
- Open design decisions: see notes.md. Further requirements `MISSING ⚠️`.

## Resources

- Figma: https://www.figma.com/design/FNpNrYsGIQFSH2pb5xHFyS/Product-detail-2026?node-id=7545-428059 (fileKey FNpNrYsGIQFSH2pb5xHFyS, node 7545:428059)
- Starting template: kit `dist/product-detail-standalone.html` (changes live in the product-detail component's tab navigation + the app region).
- Research / analytics / baseline numbers / PRD: `MISSING ⚠️`

## More information and notes

See `notes.md` in this bundle.
