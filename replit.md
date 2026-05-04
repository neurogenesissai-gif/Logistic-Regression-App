# Workspace

## Overview

pnpm workspace monorepo using TypeScript. Each package manages its own dependencies.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)

## Artifacts

### Logistic Regression Learning App (`/`)
- **Type**: React + Vite (frontend only, all computation client-side)
- **Path**: `artifacts/logistic-regression-app/`
- **Purpose**: Interactive educational web app for learning logistic regression
- **Key dependencies**: papaparse (CSV parsing), zustand (state), recharts (charts)

### API Server (`/api`)
- **Type**: Express 5 API server
- **Path**: `artifacts/api-server/`
- **Purpose**: Shared backend (currently health check only)

## App Features (Logistic Regression App)

8-step pipeline, all computation in TypeScript:
1. **Dataset Input** — CSV upload, preview, target selection
2. **Preprocessing** — Missing value handling, encoding, StandardScaler
3. **EDA** — Histograms, correlation heatmap, class distribution, scatter plots
4. **Learning Module** — Step-by-step math explanations (sigmoid, gradient descent, etc.)
5. **Training Config** — Train/test split, k-fold CV, learning rate, max iterations
6. **Model Training** — Train binary or OvR multi-class LR, loss curve, decision boundary
7. **Prediction** — Step-by-step computation trace for new samples
8. **Evaluation** — Confusion matrix, accuracy/precision/recall/F1, ROC/AUC, CV scores

## Key Files

- `artifacts/logistic-regression-app/src/lib/ml.ts` — ML engine (logistic regression, sigmoid, gradient descent, metrics)
- `artifacts/logistic-regression-app/src/lib/dataUtils.ts` — Data processing (CSV parsing, encoding, scaling, stats)
- `artifacts/logistic-regression-app/src/store/dataStore.ts` — Global state with Zustand
- `artifacts/logistic-regression-app/src/pages/` — 8 module pages
- `artifacts/logistic-regression-app/src/App.tsx` — Main layout with sidebar navigation

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server locally

See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details.
