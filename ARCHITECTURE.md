# Contract Tracker — Architecture Overview

This document shows a high-level architecture diagram for the Contract Tracker single-page mobile app and explains the main components and responsibilities.

```mermaid
flowchart LR
  U[User (Mobile Device)] --> B[Mobile Browser / WebView]

  subgraph App[Contract Tracker SPA]
    UI[UI Components\n(Header, Tabs, List, Modals, FAB, Toasts)]
    Logic[Application Logic\n(Add/Update/Delete, Filters, Stats, Reminders)]
    ImportExport[XLSX Library\n(Export / Import)]
  end

  B --> App

  App --> LS[localStorage\n(key: mobileContracts)]
  App --> DateAPI[Timer / Date APIs\n(reminders & stale detection)]
  App --> Toasts[In-app Toasts]
  App --> ImportExport

  subgraph PWA[Optional PWA Layer]
    SW[Service Worker\n(offline caching, background sync)]
    Manifest[Web App Manifest\n(home screen, theme-color)]
  end

  App --> PWA
  SW --> Cache[Cache (static assets & app shell)]

  subgraph Sync[Optional Cloud Sync]
    Backend[Sync API / Sync Server]
    DB[(Server Database)]
    Auth[Auth Provider\n(OAuth / GitHub / Gist)]
  end

  App -->|Optional Sync| Backend
  Backend --> DB
  Backend --> Auth

  style App fill:#f0f8ff,stroke:#2b6cb0,stroke-width:1px
  style PWA fill:#fff7ed,stroke:#d69e2e,stroke-width:1px
  style Sync fill:#f0fff4,stroke:#2f855a,stroke-width:1px
```

Overview
- Mobile Browser / WebView: Runs the SPA (single HTML file + JS + CSS). The UI renders contract lists, forms and handles user interaction.
- Application Logic: Maintains contracts in memory and performs add/update/delete, filtering, stats, stale/overdue detection, and reminder checks.
- Persistence: Currently uses localStorage (key: `mobileContracts`) for client-side persistence and quick offline availability.
- Import/Export: Uses the XLSX library loaded in the page to import/export spreadsheets for bulk data interchange.
- Notifications & Reminders: Simple in-app toasts and timer-based checks; can be extended to Web Notifications.
- Progressive Web App (optional): Adding a service worker and manifest enables offline caching and a native-like install experience.
- Cloud Sync (optional): If multi-device sync is desired, add an authenticated backend (API + DB) and an auth provider.

Next steps (suggested)
- Add a Web App Manifest and a lightweight Service Worker to enable PWA install and offline caching.
- Replace or complement localStorage with IndexedDB for larger data or use a client-side sync library.
- Implement optional authenticated cloud sync (REST/GraphQL) for cross-device persistence and backups.
- Add Web Notifications permission flow for background reminders (if retention & UX permit).

If you'd like, I can:
- Generate a PNG/SVG export of the diagram,
- Create a PR that adds this ARCHITECTURE.md to your repository, or
- Expand the diagram to include sequence flows for common user actions (add contract, complete contract, export/import).
```