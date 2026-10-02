# SKILLSETRA — Audit Before

Source: `SKILLSETRA-AI-DEMO-STITCH-THEME-FIXED-V3.zip`.

## P0/P1 findings
- Two application shells (`AppLayout` and `StitchShell`) maintained different navigation and layout systems.
- Stitch screens read `mockData.ts` directly and displayed static user/evidence values.
- `WorkspaceStore` kept important mutable state in process memory; refresh/restart could lose changes.
- Demo mode was inferred from missing Supabase configuration rather than an explicit environment switch.
- Production authentication used a service-role Supabase client for user CRUD.
- AI selection could silently fall back between providers and finally to a deterministic demo provider.
- Assessment was fixed at five questions and local UI state controlled completion.
- GitHub demo data was returned by the normal GitHub endpoint without a strong demo-data boundary.
- Global search only searched navigation labels.
- Learning and roadmap screens were mostly static presentation data.
- Salary/market data was hardcoded and labeled demo/illustrative.
- Persistent AI history was browser localStorage only and fullscreen was a CSS expansion, not browser Fullscreen API.
- Sidebar/top bar contained hardcoded telemetry and mock profile data.
- Light/dark styling had conflicting global and Stitch CSS and could lower contrast.
- Production shell contained gradients/glow/neon styling inconsistent with the requested restrained engineering product.
- Existing test suite encoded the five-question behavior.

## Verification limitations before changes
The source archive did not contain an installed frontend dependency tree, so a production Next.js build was not available without dependency installation. Static source inspection was used for the initial audit.
