# SKILLSETRA — Audit After

## Fixed / implemented
- One canonical `AppShell` now owns desktop, mobile, sidebar, top bar, search, theme and account navigation. `AppLayout` and `StitchShell` delegate to it.
- Typed navigation registry is shared by sidebar and search.
- Demo mode is explicit (`NEXT_PUBLIC_DEMO_MODE=true` / `DEMO_MODE=true`); production defaults to false.
- Demo workspace state persists in SQLite (`backend/data/skillsetra_demo.db`). Production workspace snapshots use a user JWT/RLS-bound Supabase client.
- Normal profile/settings CRUD no longer uses the service-role key. Service-role is limited to authentication verification in the backend.
- API responses have request IDs and structured errors; frontend requests have timeout/abort handling.
- Assessment is server-scored and expanded to 12 role-aligned questions with detailed answer feedback and persisted attempts.
- Learning progress, bookmarks and roadmap-step completion persist through the backend workspace state; production schema includes normalized tables for these records.
- Global search now queries navigation plus subjects, resources, challenges, roles and evidence.
- AI providers are exactly Puter AI, Ollama and Puter AI. Unsupported Claude UI was removed. Provider fallback is no longer silent.
- Puter AI model discovery is API-backed when configured; Ollama models come from `/api/tags`; Puter is browser-side.
- AI Coach history is persisted through `/api/v1/ai/history`; fullscreen uses the browser Fullscreen API when supported and handles `fullscreenchange`/Escape.
- GitHub analysis now inspects recursive repository tree signals, languages, commits, pull-request samples and README content where authorized. It separates observed facts from inference/recommendations.
- Demo GitHub repositories are explicitly labeled seeded demo examples.
- Production career market data is unavailable unless a current external source is configured; no current salary claim is fabricated.
- A roadmap visual asset was added as supplementary PNG; interactive roadmap remains primary.
- Sidebar stays dark in both themes; content canvas and text tokens change with the selected theme.
- Product shell uses a restrained navy/blue system and removes gradient/glow treatment from the canonical shell.
- SVG DOM property mistakes were normalized to React property names.
- Accessibility focus states, labels, keyboard sidebar/search shortcuts and reduced-motion handling were added.

## Tests actually executed
- Backend pytest: **7 passed** in demo configuration.
- Backend persistence smoke test: profile update and assessment result survived a fresh `WorkspaceStore` instance through the local SQLite snapshot.
- TypeScript/TSX parser: **62 files, 0 syntax errors**.
- CSS parser: `globals.css` and `stitch-ui.css` parsed successfully.
- Production authentication smoke test with `DEMO_MODE=false`: protected dashboard returned 401 without credentials.

## Not verified in this environment
- Full Next.js production build: **NOT VERIFIED — REQUIRES EXTERNAL ENVIRONMENT** because dependency installation timed out in this environment.
- Live Supabase RLS execution: **NOT VERIFIED — REQUIRES EXTERNAL ENVIRONMENT** with a real Supabase project and migrations applied.
- Live Puter AI, Ollama and GitHub OAuth: **NOT VERIFIED — REQUIRES EXTERNAL ENVIRONMENT** with valid provider credentials/services.
- Actual isolated arbitrary-code execution: **NOT VERIFIED — REQUIRES ISOLATED WORKER ENVIRONMENT**. The UI explicitly refuses to claim execution results when no worker exists.
