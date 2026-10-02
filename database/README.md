# Supabase setup

1. Create a Supabase project.
2. Run `schema.sql`.
3. Run `seed.sql`.
4. In Authentication, enable Email/Password.
5. Add the frontend URL to Auth → URL Configuration for local development:
   `http://localhost:3000`
6. Keep `SUPABASE_SERVICE_ROLE_KEY` server-side only.

For a production deployment, add an email provider, rate limits, audit logging and secret rotation.
