# Hermes Vault Instructions

## Purpose

This Vault is the central knowledge base for:

- Technical knowledge
- Full-stack application projects
- Hermes Agent knowledge
- Workflows and SOPs

## Rules

1. Read existing notes before creating new notes.
2. Search existing knowledge to avoid duplication.
3. Use Markdown format.
4. Use descriptive filenames.
5. Use YAML frontmatter where appropriate.
6. Use Obsidian internal links where relevant.
7. Never overwrite documentation without reviewing it.
8. Never delete notes without explicit authorization.
9. Never store passwords, API keys, tokens, or secrets.
10. Preserve the language of existing documentation.

## Folder Responsibilities

- 00-Inbox: Incoming notes.
- 01-Knowledge-Base: Reusable technical knowledge.
- 02-Projects: Project documentation.
- 03-Hermes: Agent instructions and workflows.
- 04-Research: Research and technical investigations.
- 05-Templates: Documentation templates.
- 06-Resources: References.
- 99-Archive: Historical documentation.

## Git Workflow

Before modifying:

1. Check git status.
2. Pull using fast-forward only.
3. Review existing files.

After modifying:

1. Review changed files.
2. Check for accidental secrets.
3. Commit meaningful changes.
4. Push to the configured remote.
5. Report commit hash and modified files.

Never force push.
Never discard uncommitted changes.
Never overwrite conflicting edits.
