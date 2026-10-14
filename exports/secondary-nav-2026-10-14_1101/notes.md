# Notes — secondary navigation prototype

Export version: 2026-10-14_1101 (accordion dropped in 1057; variant 3 changed from panel switching to scroll-to-section in this version)

## How to use the prototype
- Open `product-detail-secondary-nav.html` in a browser. The product-detail modal for "Agrola Jogurt z Jižních Čech Meruňka" opens on load (desktop modal = the Figma frame). Close it with the X, reopen with "Otevřít detail".
- The black switcher at the bottom compares: **Původní** (current production grey blocks), **1 Záložky**, **2 Čipy**, **3 Tabs DS**.
- Deep link to a variant: `?nav=original|tabs|chips|dstabs` (default is tabs).
- For mobile, set the browser to 375 px width and reload (the layout is chosen at load).

## The alternatives
1. **Záložky (custom sticky underline tabs)**: text tabs pinned at the top of the scrolling area, 3 px primary underline and bold primary text on the active section, thin divider below, muted counts. Scroll-spy marks the section being read; a click scrolls to the section. The requester likes the sticky behaviour when scrolled down.
2. **Čipy**: pill chips with icon + label + count ("Složení · 10 položek", "Podobné produkty · 8"), sticky, scroll-spy, active chip filled light primary with a primary outline.
3. **Tabs DS (design-system Tabs look, scroll behaviour)**: the standard DS Tabs component in a sticky bar, but driven like variants 1 and 2: clicking a tab smooth-scrolls to the section (offset for the sticky bar), scroll-spy moves the selected tab, all sections stay visible. Plain labels, no counts. The bar scrolls sideways on narrow widths.

## Variant 3 — decision and trade-off
Requester decision: keep the DS Tabs visual, but make the tabs scroll to anchors (no panel switching). The component is used as a controlled `Tabs` (`model-value` = the section the scroll-spy reports, `update:model-value` = scroll to that section). The tab body is hidden and the real sections below are the content.

- For: the familiar DS look, the same long-page model and behaviour as variants 1 and 2 (Popis and Složení readable in one scroll), so the three can be compared on look alone.
- **Deviation from the DS Tabs behaviour — design must confirm.** DS Tabs is designed to swap panels. Here it only navigates, so the tab semantics are slightly off: the component still announces `tablist` / `tab` / `aria-selected`, but there is no matching `tabpanel` next to each tab (the content is the whole page below). Assistive technology users are told they are in tabs, yet activating one scrolls instead of showing a panel.
- Accessibility options for the real implementation: (a) keep DS Tabs and accept the deviation; (b) use a link list (`nav` with links and `aria-current="true"` on the active one, as variants 1 and 2 do), which is the usual semantics for page-section navigation, styled like the DS Tabs; (c) give the sections `role="tabpanel"` and tie them with `aria-controls`, which is awkward with all panels visible. Recommendation to discuss: (b) with the DS Tabs visual.
- Also open: no counts in this variant (no slot for them in the DS component and four labels with counts do not fit the column).

## Open design questions (please review with the design department)
- Variant 3: confirm the deviation from DS Tabs behaviour and the accessibility option (see above).
- Variants 1 and 2 are built from design-system color tokens and Tailwind classes, not from a dedicated component. A DS component for "sticky section navigation with scroll-spy" may be needed.
- Icons in variant 2 (text-file, leaf-eco, replacement, store) are paired with labels as the accessibility rules require. The icon choice is a proposal.
- Counts: confirm the rule for the "Složení" count and where the data comes from.
- Description panel shows its title twice ("Popis produktu" heading plus the inner title) — pre-existing production behaviour.

## What was changed in the file (for implementers)
Only inside the PROTO regions of the copied `product-detail-standalone.html`:
- `PROTO:COMPONENT product-detail`: `ProductDetailTabNav` rewritten with the variants, `ProductDetailTabs` got the variant switch, scroll-spy, counts, the DS Tabs look with scroll-to-section behaviour and the analytics console log.
- `PROTO:EDIT app`: sample data for the Agrola product, auto-open of the modal, the switcher.

## Not verified
- Checked in the browser pane at desktop and 375 px width only, no real devices. Screen reader behaviour not tested. Add-to-cart is not instrumented.
