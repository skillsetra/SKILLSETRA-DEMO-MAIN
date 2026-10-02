# AI

Supported providers: Puter AI, Ollama AI.

- Puter AI: server-side API; models are discovered from the Puter AI models endpoint when a key is configured.
- Ollama: server-side local runtime; models are discovered from `http://localhost:11434/api/tags`.
- Puter AI: browser-side provider; the server returns an explicit handoff rather than pretending the server executed it.

There is no automatic provider substitution. If the selected provider fails, the UI reports the selected provider failure/unavailable state.

AI prompts instruct the model to separate observed evidence from inference and recommendations. Arbitrary AI HTML is not rendered.
