# Database

`database/supabase/migrations/003_skillsetra_production.sql` adds the production-oriented entities requested by the master audit: workspaces, targets, assessment results/dimensions, challenge execution/evaluation records, project evidence/defense records, GitHub analysis/evidence, subjects/resources/progress, roadmaps/versions/steps/materials/completions, notifications, settings, audit logs and AI conversations/messages/requests/evaluations.

RLS is enabled on user-owned tables with `user_id = auth.uid()` policies. Workspace ownership and membership policies are also included.

Catalog seed is in `database/supabase/seed/001_catalog.sql`.
