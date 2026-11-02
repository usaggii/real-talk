# RealTalk

A real-time chat application built to explore production-grade architecture: WebSocket messaging, message persistence, presence tracking, and horizontal scaling.

**Stack:** Next.js 14 · NestJS · Socket.io · PostgreSQL · Redis · Prisma · Turborepo

> **Status: in development.** The monorepo, tooling, and infrastructure are in place. Chat features are being built. See [Status](#status).

---

## Status

**Built**
- pnpm + Turborepo monorepo (Next.js frontend, NestJS API)
- Shared packages for types, Prisma database client, TypeScript config, and ESLint rules
- Docker Compose for PostgreSQL and Redis
- CI workflow, Husky pre-commit hooks, lint-staged, and commitlint (conventional commits)
- API health endpoint

**Planned**
- Socket.io real-time messaging
- Message persistence with cursor-based pagination
- WebSocket authentication guard
- Presence tracking (online/offline) backed by Redis
- Redis pub/sub adapter so multiple API instances can share messages (horizontal scaling)

---

## Prerequisites

- Node.js 20 or higher
- pnpm 9 or higher
- Docker and Docker Compose

---

## Getting Started

### 1. Clone and install

```bash
git clone https://github.com/Tee-chan/real-talk.git
cd real-talk
pnpm install
```

### 2. Configure the environment

```bash
cp .env.example .env
```

Fill in the values in `.env`.

### 3. Start PostgreSQL and Redis

```bash
docker compose up -d
```

### 4. Run database migrations

```bash
pnpm db:migrate
```

### 5. Start everything

```bash
pnpm dev
```

The apps run at:

| App | URL |
|-----|-----|
| Frontend | http://localhost:3000 |
| Backend | http://localhost:4000 |
| Health check | http://localhost:4000/api/health |

---

## Project Structure

| Path | Purpose |
|------|---------|
| `apps/web` | Next.js 14 frontend |
| `apps/api` | NestJS backend |
| `packages/types` | Shared TypeScript interfaces |
| `packages/database` | Prisma schema and client |
| `packages/tsconfig` | Shared TypeScript configs |
| `packages/eslint-config` | Shared ESLint rules |

---

## Commands

| Command | Description |
|---------|-------------|
| `pnpm dev` | Start all apps in dev mode |
| `pnpm build` | Build all apps |
| `pnpm lint` | Lint all workspaces |
| `pnpm typecheck` | Type-check all workspaces |
| `pnpm test` | Run all tests |
| `pnpm db:migrate` | Run Prisma migrations |
| `pnpm db:generate` | Regenerate the Prisma client |
| `pnpm format` | Format all files with Prettier |

---

## Commit Convention

This repo uses [Conventional Commits](https://www.conventionalcommits.org), enforced by commitlint. Examples of the format:

```
feat: add message model
fix: correct health check route
chore: upgrade prisma
```

---

## Author

**Tenshi**: [GitHub](https://github.com/Tee-chan) · [LinkedIn](https://linkedin.com/in/georgeangel1)

  ## License

  MIT
