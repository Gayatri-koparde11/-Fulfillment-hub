# Fulfillment Hub — demo

This is a single-file demo application to help a small e-commerce business run fulfillment tasks: track orders, move them through workflow stages, transfer inventory between warehouses, and log issues.

How to run

- Open `index.html` directly in your browser (no build required).
- Or run a simple static server:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

What changed in this demo

- Dedicated navigation items for `Picking`, `Packed`, `Staged`, and `Shipped` so you can quickly view each stage.
- Click any order row to open a detail modal with one-click actions: `Advance`, `Flag issue`, and `Transfer stock` when main warehouse stock is low.
- Sample data persists to `localStorage` so your changes remain while testing the demo.

Files

```
fulfillment-hub/
├── index.html          the application (single-file SPA)
└── README.md            this file
```

Next steps (optional)

- Add label printing and courier integration.
- Add barcode scanning or a mobile-friendly picking UI.
- Add user roles (office vs warehouse) and shift-based pickup reminders.

If you want, I can tune colors, add a print / label view, or wire a tiny backend for persistence. Tell me which you'd like next.
