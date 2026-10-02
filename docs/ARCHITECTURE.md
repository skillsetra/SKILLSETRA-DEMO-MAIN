# SKILLSETRA Architecture — Rebuilt

```text
Next.js App Router
  ├─ Root AppProvider (auth + workspace session)
  ├─ Root PersistentAIWidget (survives navigation)
  └─ Feature pages
       ├─ Dashboard / evidence visualizations
       ├─ Assessment / challenges / project defense
       ├─ Projects / roadmap / learning
       └─ GitHub Intelligence
              ↓
        FastAPI API layer
              ├─ Workspace-scoped state / Supabase persistence
              ├─ Competency + evidence engine
              ├─ GitHub Intelligence service
              └─ AI Orchestrator
                    ├─ Puter AI — primary
                    ├─ Ollama — secondary
                    └─ Puter — tertiary browser route
```

## Persistent AI

The coach is mounted from `frontend/app/layout.tsx`. It is therefore outside individual route page trees and does not unmount during normal navigation. Chat history is persisted in browser local storage.

## AI provider responsibilities

### Puter AI
Server-side API calls. `(no cloud AI key)` remains in the backend environment.

### Ollama
Server-side calls to the configured Ollama endpoint. Suitable for local/private inference.

### Puter
Browser-side calls through Puter.js. It is the tertiary route because the browser owns the provider session.

## GitHub evidence

`github_intelligence.py` collects observable repository facts first. Claims contain evidence, confidence and limitations. AI interpretation receives those facts as grounding context. The product should never treat repository metadata alone as proof of individual competency.

## Deployment

Deploy the Next.js frontend and FastAPI backend separately. Set `NEXT_PUBLIC_API_BASE_URL` on the frontend to the public backend URL, and configure CORS on the backend for the frontend origin.
