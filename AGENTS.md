# cursor-cloud-agent

## Cursor Cloud specific instructions

### Current repository state

This repository is currently an **empty scaffold**. It contains only `README.md` and
a `.gitignore`. There is **no application code** yet — no `package.json`, no lockfile,
no source directory, and nothing to build, test, lint, or run.

The `.gitignore` is oriented toward a **Node.js / Next.js** project (it ignores
`/node_modules`, `/.next/`, `/out/`, `/build`, `next-env.d.ts`, `*.tsbuildinfo`, and
`.env*.local`). This strongly implies the intended stack is Next.js, but no app has
been added.

### Toolchain available on the VM

The base image already provides the JavaScript toolchain, so no runtime install is
needed for future Next.js work:

- Node.js `v22.x`
- npm, pnpm, and yarn are all preinstalled

### Setup / run guidance

- There is nothing to run today. Once application code is added, dependency
  installation is handled automatically by the startup update script (see below), and
  the app should be started with its dev command (e.g. `npm run dev` / `pnpm dev` for
  Next.js) — never a production build/serve for development.
- The startup **update script is intentionally guarded**: it inspects for a lockfile
  or `package.json` and installs dependencies with the matching package manager
  (`npm`/`pnpm`/`yarn`). If none exist (the current state), it safely no-ops. This
  keeps future VM boots reliable whether or not application code has landed yet.
