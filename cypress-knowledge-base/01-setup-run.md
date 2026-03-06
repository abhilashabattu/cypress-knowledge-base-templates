# 01-setup-run

Purpose: install and run Cypress locally.

## 1. Check Node.js
- Run: `node -v`
- If installed: continue.
- If not installed: install Node.js (v16+), then continue.

## 2. Detect Package Manager
- Use lockfiles:
  - `package-lock.json` -> npm
  - `yarn.lock` -> yarn
  - `pnpm-lock.yaml` -> pnpm
- If none exist, use npm.

## 3. Ensure a Node Project Exists
- If `package.json` exists: continue.
- If not: ask user before running `npm init -y`.

## 4. Install Cypress (Project-Level)
- First, check if Cypress is already installed:
  - npm: `npm ls cypress --depth=0`
  - yarn: `yarn list --pattern cypress`
  - pnpm: `pnpm list cypress --depth=0`
- If not installed, install using detected package manager:
  - npm: `npm i -D cypress`
  - yarn: `yarn add -D cypress`
  - pnpm: `pnpm add -D cypress`

## 5. Verify Install
- npm: `npx cypress --version`
- yarn: `yarn cypress --version`
- pnpm: `pnpm cypress --version`

## 6. Initialize (first time only)
- If `cypress/` and `cypress.config.*` already exist: skip.
- Otherwise run:
  - npm: `npx cypress open`
  - yarn: `yarn cypress open`
  - pnpm: `pnpm cypress open`

## 7. Folder Structure (expected)
```
cypress/
  e2e/
  fixtures/
  support/
cypress.config.js (or .ts/.mjs/.cjs)
```

## 8. Run
- UI:
  - npm: `npx cypress open`
  - yarn: `yarn cypress open`
  - pnpm: `pnpm cypress open`
- Headless:
  - npm: `npx cypress run`
  - yarn: `yarn cypress run`
  - pnpm: `pnpm cypress run`
