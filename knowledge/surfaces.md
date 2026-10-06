# Where a GitOrange feature shows up

A change to one surface usually needs the others checked:

- **Web app** (`src/pages`, `src/components`): pull request page, Approvals, Actions, repository settings, Site
  admin, profiles.
- **REST API** (`worker/src/routers/*`, OpenAPI at `/api/doc`).
- **MCP tools** (`worker/src/mcp/*`): what agents can do and the instructions they read. Agents drive most work, so
  a web-only feature is often half a feature.
- **Pull request states** (`worker/src/pulls/state.ts`): the reason an agent or person sees for what to do next.
- **Docs**: `README.md`, `docs/*.md`, `docs/diagrams/how-it-works.html` (+ its PNG), `CLAUDE.md`, the onboarding
  skill.
- **Settings** (`worker/src/lib/settings.ts`, Site admin → Settings).
