# SKILLSETRA — Demo Local No-Sign-In Test Mode

## Purpose

This package includes an explicit local test launcher so the complete UI/workflow can be tested without creating an account.

## Run

1. Install Node.js LTS and Python 3.11+.
2. Double-click `START_TEST_NO_SIGNIN.bat`.
3. Open `http://localhost:3000`.
4. API documentation is available at `http://localhost:8000/docs`.

The launcher sets `DEMO_MODE=true` for the backend and `NEXT_PUBLIC_DEMO_MODE=true` for the frontend. The application therefore creates/uses the deterministic local demo workspace and does not require sign-in.

## Production safety

This is not a production authentication bypass. The production launcher remains separate and keeps authentication required.

## Persistence

Local demo workspace state uses the package's local demo persistence path. It is intentionally separate from a production Supabase workspace.
