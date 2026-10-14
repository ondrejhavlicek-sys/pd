# Task Template — Secondary navigation on the product detail (desktop modal), real product: Bohemilk ice cream

Export version: **2026-10-14_1125** (see folder name). Earlier exports are unchanged: 2026-10-14_1045, 1057, 1101 (Agrola, sample product).
Prototype file: `product-detail-secondary-nav-bohemilk.html` (open in any browser; product images load from static-new.kosik.cz, so it needs internet).
Real product: https://www.kosik.cz/p455650-bohemilk-ceska-zmrzlina-z-opocna-bez-pridaneho-cukru-boruvka
Figma reference (layout): https://www.figma.com/design/FNpNrYsGIQFSH2pb5xHFyS/Product-detail-2026?node-id=7545-428059

> **Key information is missing ⚠️** — fields marked `MISSING ⚠️` were not provided. Please reach out to the design department to finalize them.

---

## Problem statement

Under the gallery of the Kosik product detail (desktop modal) four equal-width grey blocks (Popis produktu, Složení, Podobné produkty, Produkty značky) act as anchor links. They look like inert buttons, scroll away with the page and do not show which section the customer is in. This prototype replaces them with sticky Design-System-look tabs that scroll to the section and follow the scroll, and shows them working together with the right-hand column (buy box, Multikup variants, "Další varianty", "Lidé často kupují společně").

Why it matters: the requester believes customers open the product detail to learn more (description, ingredients, nutrition) and that this builds trust. Evidence that customers fail to find these sections today: `MISSING ⚠️`.

## Value

- **For the customer** — finds description, ingredients, nutrition and allergens quickly, always knows where they are on a long page, and can reach the buy box and the alternatives at any scroll position.
- **For the business** — hypothesis from the requester: easier discovery of information builds trust, which raises the add-to-cart rate. Not validated. Business impact in money terms: `MISSING ⚠️`.

## Measurement of success

**Primary metric (requester): add-to-cart rate from the product detail** (share of product-detail views ending in add-to-cart), current navigation vs. new tabs. Target uplift and baseline: `MISSING ⚠️`.

- **Supporting metrics:** tab click-through (share of views with at least one nav click); scroll depth / section reach for Popis and Složení (the sections the hypothesis is about) and Podobné produkty.
- **Guardrails:** clicks on Multikup variants, "Další varianty" and the cross-sell block in the right column must not drop; add-to-cart rate must not drop.
- **Instrumentation in the prototype:** a nav click logs `[analytics] pd_secondary_nav_click { variant, tab }` to the browser console (`original` or `dstabs`). Event name is a proposal. Add-to-cart is not instrumented.
- **A/B setup** (sample size, duration): `MISSING ⚠️`.
- **How will customers find out?** No announcement needed (in-place replacement). Whether to inform customers: `MISSING ⚠️`.

## Limitations

- **Data from the real page (public kosik.cz API, captured 2026-10-14):** name, weight (120 ml), price (49,90 Kč), unit price (415,83 Kč/l), Multikup tiers (2 ks 42,90 Kč, 3 ks 39,90 Kč), image, description, ingredients, nutrition, allergens, brand, origin, shelf life (31/365 days), breadcrumbs and categories, the three Multikup variants (Jahoda-Malina, Pistácie, Stracciatella), similar products (29 real products) and brand products (10 of 48 real products).
- **FAKE / stand-in data ⚠️:**
  - **"Lidé často kupují společně"** — this block does not exist in the production component. The six items are real products (same-brand dairy plus items from the generic checkout-upsell widget) hand-picked as a stand-in, NOT a real co-purchase recommendation. The block itself is prototype-only.
  - **"Další varianty"** — the real source is a products-flexible query whose parameters are not known here. The prototype feeds it the real same-brand products from the similar-products response; the production price-tolerance rule (±10 %) then leaves 2 of them (Vanilková, Čokoládová).
  - The product detail page behind the modal uses the same product.
  - Add-to-cart, prices and availability are static snapshots.
- Counts are not shown (the DS Tabs component has no count slot).
- The prototype needs internet for images; no real back end.

## Requirements

- Mobile first, works from 375 px. On mobile the right-column content (buy box, variants, cross-sell) stacks above the tabs, so the sticky tab bar appears after about two screens; it then sticks and scrolls sideways if needed.
- DS Tabs look, sticky, click smooth-scrolls to the section with a sticky-bar offset, scroll-spy marks the section in view. All sections visible (no panel switching). Deviation from DS Tabs behaviour needs design confirmation (see notes.md).
- Desktop modal right column (production behaviour, kept): the right column is longer than the viewport, so it scrolls together with the left column until its bottom meets the viewport and then stays put; the modal header expands to show product name, price and "Do košíku" once the buy box has scrolled out, so the buy box is always reachable.
- Touch targets at least 40 px, native keyboard focus, design tokens only, no timeouts.
- Further requirements `MISSING ⚠️`.

## Resources

- Real product page and public API (see above).
- Figma node 7545:428059 (file FNpNrYsGIQFSH2pb5xHFyS).
- Starting template: kit `dist/product-detail-standalone.html`.
- Research / analytics / baseline / PRD: `MISSING ⚠️`

## More information and notes

See `notes.md`.
