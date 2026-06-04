# Repo guidance

## Codebase Map

See `.obvious/codebase-map.md`.

## Rules

<!-- synthesized from: README.md (only guidance file found in SCAN) — agent-relevant rules only -->

No AGENTS.md, CONTRIBUTING.md, or DEVELOPMENT.md found. Follow standard MERN conventions:
- Backend: Node.js ESM modules (`"type": "module"` in package.json). Use `import`/`export`, not `require`.
- Frontend: React 18 + Vite. JSX files use `.jsx` extension.
- State management: Redux Toolkit with RTK Query slices in `frontend/src/redux/`.
- Auth: JWT HttpOnly cookies via `cookie-parser`. Protected routes use `authenticate` + `authorizeAdmin` middlewares.
- API prefix: all backend routes are under `/api/v1/`.
- File uploads: `multer` middleware, served from `/uploads/` static directory.

## Local Verification

> **Warning:** Running full-repo typecheck, lint, or tests may OOM or timeout in the sandbox for large repos.
> Use the scoped commands below when verifying changes.

### Verified Commands

```
- Typecheck: not_discovered (no TypeScript — JavaScript-only project)
- Lint: cd frontend && npx eslint . --ext js,jsx  (34 pre-existing prop-types warnings)
- Test: not_discovered (no test suite in this repo)
```

<!-- local-verification-summary:v1 -->
- **Typecheck command:** not_discovered
- **Lint command:** `cd frontend && npx eslint . --ext js,jsx` | verified (pre-existing warnings)
- **Test command:** not_discovered
- **Scoped typecheck:** not_supported
- **Scoped lint:** `cd frontend && npx eslint src/path/to/file.jsx` | not_supported (whole-dir only)
- **Scoped test:** not_supported
- **Full-repo check safe:** yes
- **Scoped alternatives discovered:** no
<!-- /local-verification-summary -->

### Scoped Workflow

Run these commands to verify changed files without triggering a full-repo scan:

1. **Typecheck changed files:** not_supported
2. **Lint changed files:** `cd frontend && npx eslint <file>.jsx`
3. **Test changed files:** not_supported

## Sandbox Snapshot

- **Snapshot ID:** `rztrw1xu43hls9zlpcck:default`
- **Captured:** `2026-06-04T18:57:29.851Z`
- **Dev stack healthy:** yes

## Runbooks

[Populated by autobuild-runbooks skill when requested. See `.obvious/runbooks/` after that skill runs.]
