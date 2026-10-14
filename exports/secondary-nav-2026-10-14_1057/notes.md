# Notes — secondary navigation prototype

Export version: 2026-10-14_1057 (the accordion variant from 2026-10-14_1045 was dropped on the requester's feedback)

## How to use the prototype
- Open `product-detail-secondary-nav.html` in a browser. The product-detail modal for "Agrola Jogurt z Jižních Čech Meruňka" opens on load (desktop modal = the Figma frame). Close it with the X, reopen with "Otevřít detail".
- The black switcher at the bottom compares: **Původní** (current production grey blocks), **1 Záložky**, **2 Čipy**, **3 Tabs DS**.
- Deep link to a variant: `?nav=original|tabs|chips|dstabs` (default is tabs).
- For mobile, set the browser to 375 px width and reload (the layout is chosen at load).

## The alternatives
1. **Záložky (custom sticky underline tabs)**: text tabs pinned at the top of the scrolling area, 3 px primary underline and bold primary text on the active section, thin divider below, muted counts. Scroll-spy marks the section being read; a click scrolls to the section. The requester likes the sticky behaviour when scrolled down.
2. **Čipy**: pill chips with icon + label + count ("Složení · 10 položek", "Podobné produkty · 8"), sticky, scroll-spy, active chip filled light primary with a primary outline.
3. **Tabs DS (standard design-system Tabs component)**: proper tabs semantics (tablist / tab / tabpanel, arrow-key navigation from the component), sticky bar, plain labels.

## Variant 3 — decision and trade-off
The DS Tabs component switches panels; it does not scroll to sections. I kept it standard and designed around that: **panel switching**. Only the selected section is shown under the bar (Popis produktu is selected by default). When you pick a tab while scrolled down, the view is reset so the panel starts right under the sticky bar. The "Objevte také" and category blocks stay below.

- For: correct semantics out of the box (screen readers announce tabs and the selected state), no scroll-spy needed, the selected state is always clear, short page, and no scroll offsets to maintain.
- Against: Popis and Složení can no longer be read in one scroll (the information the success hypothesis is about is split across tabs, one click apart); "Podobné produkty" and "Produkty značky" are hidden until selected; no counts; the sections can no longer be linked or scrolled to as one page; it differs from the long-page model used elsewhere on the detail (and on mobile in production, which uses accordions).
- Alternative not built: standard Tabs as the sticky bar plus scroll-to-section and scroll-spy driving the selected tab. This keeps the long page but uses the component against its design (tabs imply panels), so it should only be done with design department sign-off.

## Open design questions (please review with the design department)
- Which model: long page with scroll-to-section (variants 1 and 2) or panel switching (variant 3)? This is the main product decision, since it changes how much information the customer sees without clicking.
- Variants 1 and 2 are built from design-system color tokens and Tailwind classes, not from a dedicated component. A DS component for "sticky section navigation with scroll-spy" may be needed.
- Icons in variant 2 (text-file, leaf-eco, replacement, store) are paired with labels as the accessibility rules require. The icon choice is a proposal.
- Counts: confirm the rule for the "Složení" count and where the data comes from.
- Description panel shows its title twice ("Popis produktu" heading plus the inner title) — pre-existing production behaviour.

## What was changed in the file (for implementers)
Only inside the PROTO regions of the copied `product-detail-standalone.html`:
- `PROTO:COMPONENT product-detail`: `ProductDetailTabNav` rewritten with the variants, `ProductDetailTabs` got the variant switch, scroll-spy, counts, the DS Tabs panel mode and the analytics console log.
- `PROTO:EDIT app`: sample data for the Agrola product, auto-open of the modal, the switcher.

## Not verified
- Checked in the browser pane at desktop and 375 px width only, no real devices. Screen reader behaviour not tested. Add-to-cart is not instrumented.
