# 01-setup-run

Purpose: install and run Cypress locally.

## 1. Check Node.js
- Run: `node -v`
- If installed: continue.
- If not installed: install Node.js (v16+), then continue.

## 2. Check Package Manager
- Run: `npm -v` (or `yarn -v`)
- If installed: continue.
- If not installed: install npm/yarn, then continue.

## 3. Install Cypress (Project-Level)
- `npm i -D cypress`

## 4. Verify
- `npx cypress --version`

## 5. Initialize (first time)
- `npx cypress open`
- Creates `cypress/` + `cypress.config.*`

## 6. Folder Structure
```
cypress/
  e2e/
  fixtures/
  support/
cypress.config.js
```

## 7. Run
- UI: `npx cypress open`
- Headless: `npx cypress run`