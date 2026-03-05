# Cypress Knowledge Base Templates (Setup Only)

This directory contains reusable, templated Cypress knowledge base files that can be installed into any project with a single prompt. The knowledge base gives agents structured, project-specific setup context without manual steps.

## Available Templates

| Template | Description |
|----------|-------------|
| [00-entry.md](00-entry.md) | Lightweight index listing all sections. The only file agents must read first. |
| [01-setup-run.md](01-setup-run.md) | How to install and run Cypress locally in any project. |

## Setting Up the Cypress Knowledge Base in Your Project

> **Important:** Run the prompt below from your projects root directory so the agent can read your setup and fill placeholders.

### Steps
1. Open the agent in your project directory.
2. Copy and paste the prompt below.
3. The agent will explore your repo, install the Cypress KB files, and ask for missing info.

### Prompt

```
I want to set up the Cypress knowledge base (setup-only) into this project.
Source repo: https://github.com/abhilashabattu/cypress-knowledge-base-templates (read the `cypress-knowledge-base/` directory for all template files).

Follow these steps exactly:
1. Explore this project's codebase shallowly � read README, top-level config files (package.json, pyproject.toml, .env.example, etc.), and top-level directory structure.
2. Check if `cypress-knowledge-base/` already exists in this project.
   - If it exists: stop and ask me how to proceed before making any changes.
   - If it does not exist: continue.
3. Read each template file from the source repo's `cypress-knowledge-base/` directory:
   - `00-entry.md`
   - `01-setup-run.md`
4. Copy each template to the same relative path under `cypress-knowledge-base/` in this project.
5. Replace all `{{PLACEHOLDER}}` values with project-specific values:
   a. Infer as many values as possible from your codebase exploration in step 1.
   b. For any placeholder you cannot confidently determine, ask me before proceeding. Present what you've inferred so far and ask only about the ones you're unsure of.
   c. Never guess. Never leave a `TODO:` annotation that you could have answered from the codebase.
6. Create or update a standalone Cypress KB file:
   - If `CYPRESS_KB.md` does not exist: create it and write the section below as the full content.
   - If `CYPRESS_KB.md` exists but has no "Cypress Knowledge Base" section: append the section below at the end.
   - If a "Cypress Knowledge Base" section already exists: skip — do not duplicate.

7. If `CLAUDE.md` exists:
   - Do NOT modify it.
   - Keep Cypress KB only in `cypress-knowledge-base/` and `CYPRESS_KB.md`.
   
   The section to add:
   ---
   ## Cypress Knowledge Base
   This project has a Cypress knowledge base at `cypress-knowledge-base/`. All agents that consume
   the knowledge base must follow the rules below.

   ### Reading Rules
   **Step 1 � Always read `cypress-knowledge-base/00-entry.md` first.**
   This is the index file. It lists all sections with one-line summaries. Based on
   the task at hand, decide which section files to load next. Never load all sections
   at once.

   **Step 2 � Load only the sections mapped to your agent role (see table below).**
   Do not load sections outside your mapping. If a task genuinely requires information
   from an out-of-mapping section, rely only on what the user has provided in their prompt.

   **Step 3 � Apply the No Assumptions rule.**
   Before using any section file, scan it for unfilled `TODO:` placeholders. If a section
   contains one or more `TODO:` lines, skip that section entirely. Do not infer, guess, or
   fabricate context from incomplete data. Proceed with only what is fully populated.

   ### Agent-to-Section Mapping
   | Agent | Sections to Load |
   |-------|------------------|
   | cypress-setup-agent | `01-setup-run.md` |
   | cypress-knowledgebase-router-agent | `00-entry.md` only |
   | cypress-knowledgebase-manager | All sections |

   ### No Disturbance Rule
   The knowledge base is **read-only** for all agents except `cypress-knowledgebase-manager`.
   No consuming agent may write to, modify, or delete knowledge base files.
   If the user provides explicit context in their prompt that differs from what the
   knowledge base says, **the user's prompt always takes precedence**. The knowledge
   base is supplementary context, not an override.

   ### Graceful Degradation
   If `cypress-knowledge-base/` does not exist, or `cypress-knowledge-base/00-entry.md`
   is missing or empty, proceed exactly as you would without a knowledge base.
   No error. No assumption. No behavioral change.
   ---

7. After setup is complete, show me a summary of:
   - Which `{{PLACEHOLDER}}` values were inferred and what they were set to
   - Which `TODO:` items remain and need manual input from me
   - Whether `CYPRESS_KB.md` was created or appended to
```
