# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository nature

This is **not a source-code project** — it is an Obsidian documentation vault for a project called **My Coffee Store**. The repo contains only Markdown documents (organized under `docs/`) and Obsidian configuration (`.obsidian/`). There is no build, lint, or test tooling because there is no code to build, lint, or test. All content is written in Thai.

## Structure and workflow

Documents are organized under `docs/` by workflow stage, and the numeric prefixes encode the intended reading/production order:

- `docs/01-requirements/` — project requirements, split into `01-spec` (source-of-truth requirements/specs), `02-plan` (roadmap/milestones), `03-task` (actionable task breakdown)
- `docs/02-design/` — design output, split into `01-prototypes` (UI/UX mockups, wireframes, user flow) and `02-technical` (architecture, database schema, API design)
- `docs/03-testing/` — testing artifacts, split into `01-test-plan` (test cases/scenarios) and `02-test-result` (actual results, bugs found)
- `docs/04-retrospectives/` — end-of-phase/sprint/milestone retrospectives
- `docs/05-log/` — chronological changelog and decision log, recorded continuously alongside all other work
- `docs/00-archived/` — superseded or cancelled documents, kept for historical reference (never delete docs from the project — move them here instead)

The intended flow is **requirements → design → testing → retrospectives**, with `05-log` written in parallel throughout and `00-archived` catching anything replaced or cancelled along the way. Every folder currently contains only an `index.md` describing its purpose and linking to adjacent folders via Obsidian `[[wikilink]]` syntax — treat these as the folder-level table of contents to keep updated when adding real content.

## Working in this repo

- When adding new documents, place them in the stage-appropriate subfolder (spec vs. plan vs. task, prototype vs. technical design, test-plan vs. test-result) rather than at the top level.
- Preserve the existing `[[wikilink]]` cross-references between an index and its parent/sibling/child indexes when editing them, and add new cross-references when new documents are introduced.
- Keep new content in Thai to match the existing documentation, unless the user requests otherwise.
- Don't delete documents that become obsolete — move them into `docs/00-archived/` per the convention stated in that folder's index.
