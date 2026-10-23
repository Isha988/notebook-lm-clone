# NotebookLM Clone

A clone of Google's NotebookLM

## Architecture

pnpm + Turborepo monorepo (`pnpm-workspace.yaml`: `apps/*`, `packages/*`).

| Path | Package | What it is |
| --- | --- | --- |
| `apps/web` | `web` | Next.js 16 (App Router, Turbopack), React 19, Tailwind v4, shadcn/ui |
| `apps/api` | `api` | Express 5 + zod, ESM, run with `tsx watch`; port `4000` (`PORT` env) |
| `packages/shared` | `@notebook-lm-clone/shared` | Shared TypeScript types/schemas; built with `tsc` to `dist/` |

Both apps depend on `@notebook-lm-clone/shared` via `workspace:^`. Put types and zod schemas used by both sides there (e.g. API request/response shapes), not duplicated.

## Commands

Run from the repo root:

- `pnpm dev`: runs `shared` (tsc watch), `api` and `web` together via turbo. Web on http://localhost:3000, API on http://localhost:4000.
- `pnpm build`, `pnpm lint`, `pnpm typecheck`: turbo tasks (`build`/`typecheck` build dependencies first via `^build`).
- Single package: `pnpm --filter web <script>` / `pnpm --filter api <script>`.
- Add a shadcn component: `cd apps/web && pnpm dlx shadcn@latest add <name>`.

## Environment

- Node 22.23.4 and pnpm 9.4.0, pinned with Volta. Next.js 16 needs Node >= 20.9; if `pnpm dev` complains about Node 18, pnpm was installed under an old Node (`volta install node@22 && volta install pnpm@9.4.0`).
- `.env*` files are gitignored except `.env.example`. Put real secrets (LLM API keys etc.) in the app's own `.env`, and list the variable names in `.env.example`.
