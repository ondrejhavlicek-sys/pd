# Product detail – secondary navigation prototype

Prototype exploring how to improve the secondary navigation (Popis produktu / Složení / Podobné produkty / Produkty značky) on the Košík product detail.

**Primary metric (proposed):** add-to-cart rate from the product detail. Supporting: tab click-through, scroll depth to Popis and Složení. Guardrails: clicks on variants and cross-sell.

## Latest version
- Prototype: [`exports/secondary-nav-bohemilk-2026-10-14_1125/`](exports/secondary-nav-bohemilk-2026-10-14_1125/)
  - `product-detail-secondary-nav-bohemilk.html` – open locally in a browser (needs internet for product images)
  - `task-template.md` – handoff template (some fields still marked MISSING)
  - `notes.md` – design notes, trade-offs and open questions
- Switch variants with `?nav=original` (baseline) or the default (DS-look tabs that scroll to anchors).

## Folder layout
- `product-detail-secondary-nav-bohemilk.html` – working copy (Bohemilk product, real data from kosik.cz)
- `product-detail-secondary-nav.html` – earlier working copy (Agrola product, sample data, variants 1/2/3)
- `exports/` – versioned exports named by date-time; older ones kept for history

Product data is a static snapshot captured 2026-10-14.
