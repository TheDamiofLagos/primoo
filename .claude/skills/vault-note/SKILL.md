---
name: vault-note
description: Write or update a Markdown note in the PrimOO Obsidian vault
  following Obsidian conventions. Use when the user asks to save, log,
  capture, note down, or write up a conversation, decision, investigation,
  or piece of work, or when they mention the vault or Obsidian.
---

# Writing notes to the PrimOO Obsidian vault

## Before you write

1. Search the vault for an existing note on this topic. Prefer updating
   an existing note over fragmenting the vault. Only create a new note
   if the subject is genuinely distinct.
2. Decide which template applies (see below), then read that template
   file from this skill's `assets/` directory.
3. If you are unsure whether to append or create, ask.

## Where notes go

All notes go in `PrimOO Obsidian Vault/`, flat at the root unless the
user has already created a subfolder for that topic. Never write to
`.obsidian/`.

## Choosing a template

Pick one. If a session produced two kinds of output, write two notes and
link them rather than stretching one template.

| Template | Use when | Filename |
| --- | --- | --- |
| `assets/session-log.md` | Work happened on a date. Investigations, debugging, builds, analysis runs. | `2026-08-29 Loan Tape Reconciliation.md` |
| `assets/decision-record.md` | A choice was made between real alternatives and you will be asked why later. | `Use Incremental Models for Loan Tape.md` |
| `assets/reference.md` | Durable knowledge with no expiry. Concepts, conventions, how a system works. | `dbt Contract Generation.md` |

Only session logs get a date prefix. Decisions and references are
evergreen and titled by subject.

If a session log contains a decision worth defending, extract it into
its own decision record and link the two. Do not leave the reasoning
buried in a dated note.

## Filenames

Title Case with spaces. Never use `: / \ # ^ [ ] |` in a filename,
because those characters break wikilinks.

## Section discipline

Copy the chosen template and replace every `{{placeholder}}`.

Frontmatter is always fully filled. Leave `updated` empty on creation
of a session log or decision; set it on every edit to a reference note.

- `created` is today's date, ISO format. Never change it on an update.
- `tags` are nested and lowercase: `primoo/dbt`, `primoo/lending`,
  `primoo/data-quality`. Two or three, not ten. Tags go in frontmatter,
  never inline in the body.
- `aliases` is how the user would naturally refer to the note in
  conversation, not a restatement of the title.

Body sections are conditional. Include a section only if you have real
content. Delete the heading entirely otherwise. Never write "N/A",
"None", or leave a heading empty.

Always required: the summary callout, plus Context and What we did for
session logs, Problem and Decision for decision records, What it is and
How we use it at Primoo for references.

Give options and decisions block IDs (`^optA`, `^decision`, `^d1`) so
later notes can link to a specific part rather than the whole note.

## Linking rules

- Internal links are wikilinks by note name, not path: `[[Loan Tape Audit]]`.
- Alias display text with a pipe: `[[Loan Tape Audit|the audit]]`.
- Link a specific heading with `[[Note Name#Heading]]`, a block with
  `[[Note Name#^d1]]`.
- Embed with `![[Note Name]]`. Use sparingly, it clutters reading view.
- Check the target note exists before writing a wikilink. If it does not,
  either create a stub note for it or tell the user the link will be
  unresolved. Never silently emit links to notes that do not exist.
- Link to code with a relative Markdown link, not a wikilink:
  `[models/staging/stg_loans.sql](../models/staging/stg_loans.sql)`.
  Wikilinks only resolve inside the vault.

## Content rules

- Write what was decided and why, not a transcript. Where a decision was
  made, the reasoning behind it is the valuable part.
- Record the shape of data, not the data. No customer names, account
  numbers, or loan-level records in the vault.
- Prefer prose over bullets for reasoning. Bullets for enumerations.

## Updating existing notes

Reference notes are edited in place, and `updated` is bumped.

Session logs are append-only. Add a dated subsection rather than
rewriting history.

Decision records are never edited once `status: accepted`. To change a
decision, write a new record, set its `supersedes` field to the old
note, and set `superseded-by` on the old one.

## After writing

Report the filename you used and the sections you filled, in one line.
Do not paste the note back into chat.

`_Index.md` builds itself from Dataview queries over frontmatter, so no
manual index update is needed. This holds only if the frontmatter is
complete, which is why it is the one part with no optional fields.