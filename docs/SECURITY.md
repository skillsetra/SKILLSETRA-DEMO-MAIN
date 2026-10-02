# Security

Implemented baseline controls:
- explicit production/demo environment separation
- Supabase Auth required in production
- JWT-bound user CRUD path for ordinary Supabase operations
- RLS migration for user-owned tables
- GitHub URL allowlisting and redirect rejection
- security headers and CSP baseline
- request IDs
- API timeout/abort handling
- no production demo credentials
- no silent AI fallback
- no arbitrary AI-generated HTML rendering
- no claim of code execution without an isolated worker

External OAuth/token storage and production secret rotation still require deployment-specific configuration.
