# Agent capabilities -- staple-ai

Read by `agent-scope-check` before any agent slice opens a PR here.
Edit the YAML below; the script parses the first ```yaml block.

Staple is an AI-agent company control plane. Default scope lets agents
work on product code, tests, docs, adapters, and local tooling while
keeping release, deployment, database ownership, and secret-bearing
surfaces behind human review.

```yaml
allow:
  - AGENT_CAPABILITIES.md
  - cli/**
  - doc/**
  - docs/**
  - evals/**
  - packages/adapter-utils/**
  - packages/adapters/**
  - packages/mcp-server/**
  - packages/plugins/**
  - packages/shared/**
  - scripts/**
  - sdlc/**
  - server/src/**
  - server/scripts/**
  - skills/**
  - tests/**
  - ui/src/**
  - ui/public/**
  - ui/storybook/**
  - README.md
  - ROADMAP.md
  - CONTRIBUTING.md

deny:
  - .env
  - .env.*
  - secrets/**
  - "**/credentials*"
  - "**/*.key"
  - "**/*.pem"
  - .github/CODEOWNERS
  - .github/workflows/release.yml
  - .github/workflows/docker.yml
  - .github/workflows/refresh-lockfile.yml
  - docker/**
  - releases/**
  - patches/**
  - packages/db/**
  - server/src/db/**
  - server/src/auth/**
  - package.json
  - pnpm-lock.yaml
  - pnpm-workspace.yaml
  - tsconfig.base.json
  - tsconfig.json
  - Dockerfile

limits:
  max_files: 25
  max_loc: 800
  max_minutes: 30
```

## Notes

- `packages/db/**` is denied because schema and migration changes must
  be reviewed with the database workflow in `AGENTS.md`.
- Release, Docker, and lockfile changes are denied because they can alter
  published artifacts or dependency provenance.
- `server/src/auth/**` is denied by default because agent edits there can
  broaden operator and service access boundaries.
