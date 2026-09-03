# PrimOO Workspace

## Layout
- Repo root: all Primoo work. Code, dbt projects, SQL, notebooks, scripts.
- `PrimOO Obsidian Vault/`: Obsidian vault. Markdown notes only.
- `PrimOO Obsidian Vault/.obsidian/`: Obsidian configuration.

## Hard rules
- Never write `.py`, `.sql`, `.yml`, `.csv` or data files into the vault.
- Never write working notes or scratch `.md` files into the repo root.
  Notes belong in the vault. `AGENTS.md` and `CLAUDE.md` are the only
  Markdown files that belong at the root.
- Never edit files inside `.obsidian/`. Reading it is fine when I ask you
  to diagnose vault or plugin configuration.
- Never commit `.DS_Store`.

## Data handling
The vault is a separate private repository and is never pushed to a
shared remote. Borrower and staff names are permitted in vault notes.

Never write BVN, NIN, account numbers, phone numbers, or residential
addresses into any file in this workspace, vault or repo.
Never paste raw query output containing customer records into a note.
Summarise: counts, rates, and named examples only where the name is
itself the finding.

## Session start
Read `PrimOO Obsidian Vault/_index.md` for prior context before starting
substantive work.

## Capturing notes
When I ask you to save, log, capture, or write up anything, use the
`vault-note` skill. All Obsidian conventions and the three templates are
defined there.