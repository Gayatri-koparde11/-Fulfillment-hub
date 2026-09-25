# Fulfillment Hub

**A lightweight operations console for e-commerce order fulfillment — built for XYZ, a small business shipping from its own warehouse.**

XYZ currently runs fulfillment on spreadsheets and a shared folder. It works, until it doesn't: nobody can see order status at a glance, priority orders get buried with regular ones, stock shown in the spreadsheet doesn't match what's actually on the shelf, and packed boxes or courier pickups go missing without anyone noticing. Fulfillment Hub is a small, focused tool built directly against those specific breakdowns — not a full ERP rebuild.

---

## Why this exists

Of the seven problems named in the brief, this build deliberately concentrates on four that compound into the most operational risk:

| Problem | How it's addressed |
|---|---|
| No visibility into order status | A live Dashboard replaces the spreadsheet scan — at-risk orders, low stock, and open issues surface automatically |
| Priority orders getting buried | Priority is flagged everywhere (dashboard, orders list, order detail) and feeds directly into an "at risk" calculation |
| Stock mismatches / wrong items shipped | Inventory is visible per warehouse and tied directly into the picking step — an order literally cannot be picked against stock that isn't there |
| Lost boxes / missed pickups | A dedicated Staged view plus a running issue log, so problems get recorded instead of handled informally and forgotten |

Deliberately **out of scope**: real courier-API integration, label printing, and barcode scanning. These matter in production but aren't needed to demonstrate the workflow logic — the brief scopes this as a demo, and dummy data is sufficient to prove it end to end.

---

## What's in the app

- **Dashboard** — orders in progress, priority queue, at-risk orders, low-stock SKUs, staged boxes awaiting courier pickup, recent activity, and a stage-by-stage volume chart.
- **Orders** — the full order list, filterable, sortable, with one-click **Advance** and **Flag issue** actions. Click any row to open a detail view with the order's full context, current main-warehouse stock, and a **Transfer stock** shortcut when stock is too low to pick.
- **Picking / Packed / Staged / Shipped** — dedicated shortcuts into the order list, pre-filtered to that stage, since warehouse staff typically work one stage at a time rather than scanning a full order list.
- **Inventory** — stock per product across the main and secondary warehouse, with a one-click **Transfer to main**. Orders only ship from the main warehouse, matching how XYZ actually operates — stock has to move over before it can be picked.
- **Issues** — a running log of problems (stock shortfalls, flagged mismatches, courier misses), some auto-logged by the app itself, some added manually. Resolve or reopen as needed.
- **Export** — downloads the current session's data as JSON, for anyone who wants to inspect what the demo generated.

---

## How to run it

No build step, no install, no server required.

1. Unzip this folder.
2. Double-click `index.html` — it opens in your default browser and loads immediately.

**In VS Code:** open this folder, install the "Live Server" extension, then right-click `index.html` → *Open with Live Server*.

**If your browser blocks local scripts:**
```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Sample data (orders, products, warehouse stock, issues) is generated on first load and saved to your browser's `localStorage`, so anything you do — advancing an order, transferring stock, resolving an issue — persists if you close and reopen the file. To reset to a clean demo, clear that site's local storage or use a fresh unzip.

---

## Design decisions

The brief specifies the warehouse team is experienced but not comfortable with technology, so the interface stays deliberately plain: clear status labels instead of jargon, one-click actions instead of multi-step forms, and no logins, settings, or configuration screens to get lost in. Every action name matches what it does — "Advance," "Transfer to main," "Resolve" — so nothing needs explaining twice.

## Tech

A single self-contained `index.html` — HTML, CSS, and vanilla JavaScript, no framework or build tooling. State lives in memory and `localStorage`; there is no backend, by design, since the brief doesn't require one for a demo built on sample data.

## Files
fulfillment-hub/
├── index.html the application
├── README.md this file
└── AI_Usage_Note.pdf AI usage note for this submission


## If this went further

Real courier-API integration and shipping label generation, barcode/scanner support for the picking floor, and role-based views (office vs. warehouse) would be the natural next additions — each was left out here because it adds real-world integration complexity without changing what this demo needs to prove.
