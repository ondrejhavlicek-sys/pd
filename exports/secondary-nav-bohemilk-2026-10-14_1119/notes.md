# Notes — Bohemilk prototype (sticky DS-look tabs + right-hand column)

## How to use
- Open `product-detail-secondary-nav-bohemilk.html`. The product-detail modal for the real Bohemilk product opens on load (desktop modal). Close with X, reopen with "Otevřít detail" in the bottom switcher.
- Switcher: **Původní** (current grey blocks, baseline) and **Nové záložky** (default). `?nav=original` opens the baseline. The tabs/chips variants from the earlier exports are not offered here (their code is still in the file, but dormant).
- For mobile, set the browser width to 375 px and reload.

## How I read "right pane scrolls on its own" (please confirm)
The request was unclear: the right-hand column could scroll in its own inner scroll area, or behave like production. I picked the second, since it is the existing production behaviour and avoids nested scrolling: when the right column is taller than the modal, it scrolls together with the left column until its bottom meets the viewport, then stays in place (sticky with a negative top). The modal header then expands to show name, price and "Do košíku", so the buy box stays reachable. I made the right column genuinely tall: Multikup tiers, buy box, "Varianty v Multikupu" (3), "Další varianty" (2), and a new "Lidé často kupují společně" block (6) — about 1570 px against a 910 px modal body on a 1400x1000 viewport.
- Why no inner scroll: nested scroll areas cause scroll-chaining (the wheel jumps between panes), make the page feel stuck, and hide the buy box on touch devices. Not built; can be added if the requester meant that.
- Checked: the tab bar sticks at the top of the left column; clicking a tab scrolls to the section (heading 72 px below the root top); scroll-spy depends only on the left-column sections, so the right column does not affect it; there is a single scroll container, so no scroll chaining.
- Mobile: the right-column blocks stack above the tabs (production layout), so the tab bar only becomes sticky after them.

## Data: real vs. fake
See the Limitations in `task-template.md`. In short, real: everything about the product itself, Multikup variants, similar products, brand products. Fake or stand-in: "Lidé často kupují společně" (the block and its items), the selection feeding "Další varianty".
Also noted: the Figma frame (Agrola) showed different data; this prototype uses the real Bohemilk page instead.

## Tab bar layout details (changed in this version)
- The tab bar starts flush at the left edge of the content column: the left padding of the tab list is removed, so the first tab box and the bottom line align with the content below (verified: box and heading both at the same left edge). The first tab keeps its normal inner padding, so its label does not touch the border (label about 17-21 px in).
- When the bar is stuck there is a 12 px white gap between the expanded modal header and the tabs (padding at the top of the sticky bar, so content does not show through the gap). The scroll-to-section offset was increased from 72 to 84 px (page mode: +68 px instead of +56 px), so a clicked heading lands about 27 px below the bar. Checked at desktop and 375 px: click-to-scroll lands correctly and scroll-spy still follows the sections.
- The 12 px also appears above the tabs when they are not stuck.

## Open design questions
- Variant 3 deviation from DS Tabs behaviour (tabs that scroll rather than switch panels) and its accessibility semantics: DS Tabs announces tablist/tab/aria-selected without a matching tabpanel. A link list with `aria-current` styled like DS Tabs is the usual alternative. Design must confirm.
- Where "Lidé často kupují společně" comes from (recommendation source, number of items, same row design as variants?).
- On mobile the tabs sit after the right-column blocks; consider whether the tab bar should come earlier.

## What was changed (for implementers)
Same as earlier exports (the tab navigation in the product-detail component), plus: a prototype-only `product-cross-sell` block in the right column, product data and a products-by-id registry for variant rows in the app region.

## Not verified
Desktop (1400 px) and 375 px checked in the browser pane only; no real devices or screen readers.
