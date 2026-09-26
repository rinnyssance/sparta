# AGENTS.md — guidance for coding agents working on SPARTA

SPARTA is a mobile-first React app (TanStack Start v1 + React 19 + Vite 7 + Tailwind CSS v4) for Norfolk State University students. It is intentionally a front-end prototype: **no backend, no authentication, no external services**. Do not add them unless the project owner asks.

## Architecture rules

- **Routing:** TanStack Router file-based routes in `src/routes/` only. Never install or use `react-router-dom`, `BrowserRouter`, or an `App.tsx` page switcher. Never edit `src/routeTree.gen.ts` (it regenerates).
- **Root shell:** shared layout lives in `src/routes/__root.tsx` around `<Outlet />`; the bottom navigation is rendered there so all five tabs share it. Every path-level parent route must render `<Outlet />`.
- **Demo data:** calendar events and types live in `src/lib/calendar-data.ts` and are seeded locally. Calendar edits persist to browser **localStorage** only — do not move them to a database, server function, or remote store without an explicit request.
- **Server boundaries:** there are no server functions today. If one is ever needed, use `createServerFn` from `@tanstack/react-start` in a client-safe module path (e.g. `src/lib/*.functions.ts`), not under `src/server/`.

## Design rules

- All colors/gradients/shadows are semantic design tokens in `src/styles.css`; theme shadbn component variants through them. **Never hardcode color utilities** (`text-white`, `bg-[#...]`) in components — it breaks theming.
- Brand palette: deep Norfolk State green `#004F36`, warm gold `#F6C945`, cream `#FFFDF7`, soft sage/neutral background. Stick to these tokens.
- Mobile-first: design at ~390px width; keep touch targets comfortably large. Check changes don't introduce horizontal overflow.
- Reusable primitives (Button, Card, Badge, SectionHeader) live in `src/components/` — compose screens from them instead of one-off markup.

## Conventions

- Keep the five tabs (Home, Calendar, Plan, Book, Campus) as distinct route files with their own `head()` metadata (unique title/description per route).
- Booking and campus screens must clearly state they show sample/demo data.
- Date logic must be UTC-safe (see helpers in `src/lib/calendar-data.ts`); the demo week is September 2025 (Mon 22 – Fri 26, Thu 25 active).
- Verify changes by running the app at phone and desktop widths and checking for runtime errors and horizontal overflow before declaring a task done.
