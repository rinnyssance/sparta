# SPARTA

SPARTA is a mobile-first student companion app for **Norfolk State University**. It gives students a warm, collegiate home for their day: a class timeline, a week/month calendar with a personal planner, booking previews, and campus info — all wrapped in the university's deep green and gold.

> This is a front-end prototype. All data is local demo data; there is no backend, authentication, or external integration yet.

## Features

- **Home** — "Good morning, Maya" day view with a week date strip, class timeline (BIO 301, Writing Center draft review, Spartan Café lunch, CHEM 221, study block, Biology Club meeting), a quick-action FAB, and the campus photo banner.
- **Calendar** — day and week planner with demo events; add, edit, and delete events. Changes persist in browser localStorage only (per-browser, not synced).
- **Plan** — study plan preview.
- **Book** — appointment booking preview (booking is not connected in the demo).
- **Campus** — campus info preview (sample data, not live hours or directions).

## Tech stack

- [TanStack Start](https://tanstack.com/start) v1 (React 19, Vite 7) — file-based routing with TanStack Router
- Tailwind CSS v4 (theme tokens in `src/styles.css`)
- shadcn/ui-style components with Radix primitives
- No backend — static local demo data + browser localStorage for calendar edits

## Design

| Token | Value | Use |
| --- | --- | --- |
| Deep green | `#004F36` | Primary / brand |
| Warm gold | `#F6C945` | Accents, active states |
| Cream | `#FFFDF7` | Cards, light surfaces |
| Soft sage | neutral background | Page background |

Reusable primitives live in `src/components` (Button, Card, Badge, SectionHeader) and the bottom navigation (Home · Calendar · Plan · Book · Campus) in `src/components/app-navigation.tsx`.

## Getting started

```bash
bun install   # or npm install
bun run dev   # or npm run dev
```

Then open the printed local URL (the dev server serves the app in development mode).

## Project structure

```text
src/
  components/       # Shared UI: cards, buttons, badges, section headers, bottom nav
  lib/              # Shared demo data (calendar events) and helpers
  routes/           # File-based routes: /, /calendar, /plan, /book, /campus
  styles.css        # Tailwind v4 theme tokens (colors, fonts)
```

## Roadmap ideas

- Connect real booking flows and campus data
- Sync calendar events to a backend
- Per-student profiles and notifications
