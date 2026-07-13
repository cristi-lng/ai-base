# ai-base

Generic, reusable [pi](https://github.com/earendil-works/pi) building blocks — a foundation layer of extensions and skills that add research, sub-agents, safety guards, and authoring tools to any pi setup.

## Installation

```bash
# Global — writes to ~/.pi/agent/settings.json, available in every project
pi install git:github.com/cristi-lng/ai-base@v1.0.0
```

## Features

### Extensions

- **info-bar** — Custom TUI editor with purple borders and a session info bar (cost, context usage, model, provider, cwd, git branch).

### Skills

- **write-a-skill** (`/skill:ai-base-write-a-skill`) — Author or edit skills with proper structure, description writing, and progressive disclosure.

### Bundled dependencies

Pinned external pi packages that install alongside ai-base:

- **[pi-web-access](https://github.com/nicobailon/pi-web-access)** — Web search and URL/PDF/video fetching, plus the `librarian` skill for researching open-source libraries.
- **[pi-fork](https://github.com/elpapi42/pi-fork)** — Run a task in an isolated child agent (sub-agents).
- **[pi-mono-sentinel](https://github.com/emanuelcasco/pi-mono-extensions)** — In-process guard against secret leaks and unsafe tool calls.
