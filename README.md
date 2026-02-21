# CICD-Fe Single (Next.js)

Minimal Next.js + TypeScript project prepared to validate the existing CI/CD workflows in this repository.

## Local Commands

```bash
npm install
npm run dev
npm run test
npm run lint
npm run build
```

## CI/CD Setup Required (No Pipeline Changes)

The workflows under `.github/workflows` already assume this project is at repository root (`.`) and use branch flow: `test -> uat -> main`.

### 1) Required Branches

- `test`
- `uat`
- `main`

### 2) Required Repository Secrets

- `VERCEL_TOKEN`
- `VERCEL_ORG_ID`
- A secret that stores your Vercel Project ID (for example: `VERCEL_PROJECT_ID_FE_SINGLE`)

For PR auto-creation jobs, also provide one of:

- `GH_PR_TOKEN` (preferred), or
- `GHPR_TOKEN` (legacy)

### 3) Required Repository Variable

- `FE_SINGLE_VERCEL_PROJECT_SECRET`
  - Value must be the **name** of the secret that contains your Vercel Project ID.
  - Example value: `VERCEL_PROJECT_ID_FE_SINGLE`

### 4) Optional Repository Variables

- `FE_SINGLE_SYSTEM_NAME` (default: `Frontend-Root`)
- `FE_SINGLE_WORKING_DIR` (default: `.`)
- `FE_SINGLE_IMAGE_NAME` (default: `fe-single-web`)
- `FE_SINGLE_PR_TOKEN_SECRET` (default: `GH_PR_TOKEN`)

### 5) Vercel Project Settings

- Link this repository to a Vercel project.
- Set Vercel Root Directory to `.` for this single frontend setup.

## Notes

- Unit tests generate `coverage/coverage-summary.json` for the test workflow.
- `Dockerfile` is included so the existing Docker build workflow on `main` can run.
