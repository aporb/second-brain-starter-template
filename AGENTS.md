# AGENTS.md — Agent-Agnostic Instructions

This file provides operating instructions for any AI agent working in this vault — whether that's Claude Code, OpenAI Codex, OpenCode, Cursor, GitHub Copilot, or any other agentic harness.

## Read This First

**All operating rules live in `/schema/agent-protocol.md`.** That file is the single source of truth. This file adds agent-agnostic guidance only.

## Vault Architecture

This is a four-zone Second Brain vault:

| Zone | Path | Owner | Agent Access |
|------|------|-------|-------------|
| Sources | `/sources/` | Human | **Read only** |
| Wiki | `/wiki/` | Agent | **Read + write** |
| Journal | `/journal/` | Human | **Read only** |
| Schema | `/schema/` | Human | **Read only** (unless instructed) |

## Core Workflows

### Ingest a Source
1. Read the source file in `/sources/`.
2. Update its frontmatter `status` to `reading`.
3. Create or update wiki pages in `/wiki/` that synthesize the source content.
4. Use `[[source-filename]]` citations in wiki pages.
5. Update the source frontmatter `status` to `processed`.

### Research a Topic
1. Search existing wiki pages and sources for relevant content.
2. If gaps exist, the human provides new sources to `/sources/`.
3. Ingest new sources (see above).
4. Create a wiki page synthesizing findings.

### Daily Journal
1. Create a file at `/journal/YYYY-MM-DD.md` using the journal template.
2. The human fills in the content. You read it for context.

### Vault Status
1. Scan `/sources/` for `status: unread` files.
2. Scan `/wiki/` for `status: draft` pages that haven't been updated recently.
3. Check `/wiki/contradictions.md` for unresolved conflicts.
4. Report findings to the human.

## Key Rules

1. **Never modify `reviewed` or `stable` wiki pages** without explicit instruction.
2. **Never modify files in `/sources/`.**
3. **Always include frontmatter** — see `/schema/agent-protocol.md` for formats.
4. **Flag contradictions** in `/wiki/contradictions.md`.
5. **No fabrication.** If the source doesn't say it, don't write it.
6. **One concept per wiki page.** Split broad pages.

## Agent-Specific Files

Different agents use different instruction files. All point to the same source of truth:

| Agent | Instruction File |
|-------|-----------------|
| Claude Code | `CLAUDE.md` + `.claude/commands/` |
| Cursor | `.cursorrules` |
| GitHub Copilot | `copilot-instructions.md` |
| Other | This file (`AGENTS.md`) |
