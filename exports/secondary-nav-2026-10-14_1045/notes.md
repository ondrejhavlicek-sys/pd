# Notes — secondary navigation prototype

Export version: 2026-10-14_1045

## How to use the prototype
- Open `product-detail-secondary-nav.html` in a browser. The product-detail modal for "Agrola Jogurt z Jižních Čech Meruňka" opens on load (desktop modal = the Figma frame). Close it with the X, reopen with "Otevřít detail".
- The black switcher at the bottom compares: **Původní** (current production grey blocks), **1 Záložky**, **2 Čipy**, **3 Akordeon**.
- Deep link to a variant: `?nav=original|tabs|chips|accordion` (default is tabs).
- Resize to 375 px width to check mobile (reload after resizing, the layout is chosen at load).

## The three alternatives
1. **Sticky underline tabs**: text tabs in a bar pinned at the top of the scrolling area, 3 px primary underline and bold primary text on the active section, thin divider below; counts in muted text.
2. **Chips with icons and counts**: pill chips with icon + label + count ("Složení · 10 položek", "Podobné produkty · 8"), sticky, active chip filled with the light primary and a primary outline.
3. **Accordions**: all four sections become collapsible items with chevrons; Popis produktu open by default (single-open). Count appears as subtitle ("10 položek").

## Open design questions (please review with the design department)
- **Accordions vs. "never hide necessary information"** (design principles): variant 3 hides Složení/allergens behind a click. Allergens and ingredients are arguably necessary information. Needs a design decision, or keep Složení open/visible.
- **Icons**: the chips use icons from the DS set (text-file, leaf-eco, replacement, store) always paired with a label, as accessibility rules require. The icon choice is a proposal.
- Counts: confirm the rule for "Složení" count and where the data comes from.
- Count/underline/chip visuals are built from DS color tokens and Tailwind classes, not from a dedicated DS component (the DS Tabs component swaps panels, it does not do anchor scroll-spy). A DS component for this pattern may be needed.
- Single vs. multiple open accordion items.
- The accordion body repeats the title as an inner heading ("Popis produktu") — pre-existing production behaviour.

## What was changed in the file (for implementers)
Only inside the PROTO regions of the copied `product-detail-standalone.html`:
- `PROTO:COMPONENT product-detail`: `ProductDetailTabNav` rewritten with the variants, `ProductDetailTabs` got the variant switch, scroll-spy, counts, accordion-for-all-tabs mode and an analytics console log.
- `PROTO:EDIT app`: sample data for the Agrola product, auto-open of the modal, the switcher.

## Not verified
- Only checked in the browser pane at desktop and 375 px width, no real devices. Screen reader behaviour not tested.
