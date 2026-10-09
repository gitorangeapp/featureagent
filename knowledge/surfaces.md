# Where a GitOrange feature shows up

A change to one surface usually needs the others checked:

- **Web app** (`src/pages`, `src/components`): pull request page, Approvals, Actions, repository settings, Site
  admin, profiles.
- **REST API** (`worker/src/routers/*`, OpenAPI at `/api/doc`).
- **MCP tools** (`worker/src/mcp/*`): what agents can do and the instructions they read. Agents drive most work, so
  a web-only feature is often half a feature.
- **Pull request states** (`worker/src/pulls/state.ts`): the reason an agent or person sees for what to do next. The
  reason `kind` is an internal union, not a public API: its consumers are only in this repository (the web app's
  `src/lib/pullState.ts` and `worker/src/mcp/*`). Renaming or reshaping a `kind` is a breaking change only if the
  diff leaves a consumer matching the old kind; when every consumer is updated in the same PR, it's an internal
  refactor, not something a client can silently lose.
- **Agent prompt and its MCP tool together** (`src/lib/agentPrompt.ts` and `worker/src/mcp/*`): the prompt is not a
  public contract; it's instructions this repository ships to its own agents, and the MCP tools it names live in
  the same repository. When a PR updates both the prompt and the tool it calls (names, parameters, descriptions) in
  step, agents are not broken — check the diff actually updates the tool before flagging a mismatch. Only flag it
  when one side changes and the other doesn't, or when the tool's description no longer matches its real
  parameters.
- **Docs**: `README.md`, `docs/*.md`, `docs/diagrams/how-it-works.html` (+ its PNG), `CLAUDE.md`, the onboarding
  skill.
- **Settings** (`worker/src/lib/settings.ts`, Site admin → Settings).
