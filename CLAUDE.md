# CLAUDE.md — Claude Code Instructions

You are operating inside a Second Brain vault — a persistent, interlinked markdown knowledge base that you build and maintain.

## Read This First

**All operating rules live in `/schema/agent-protocol.md`.** That file is the single source of truth. This file adds Claude Code-specific guidance only.

## Vault Zones

| Zone | Path | Your Access |
|------|------|-------------|
| Sources | `/sources/` | Read only |
| Wiki | `/wiki/` | Read + write |
| Journal | `/journal/` | Read only |
| Schema | `/schema/` | Read only (unless instructed) |

## Slash Commands

You have 7 custom slash commands available:

| Command | What It Does |
|---------|-------------|
| `/ingest` | Read a source, create wiki pages, cross-reference |
| `/ask` | Query the wiki using existing synthesized knowledge |
| `/research` | Research a topic, ingest sources, build wiki pages |
| `/daily` | Create or update today's journal entry scaffold |
| `/sync` | Git pull, add, commit, push |
| `/status` | Show vault health (unprocessed sources, stale pages, contradictions) |
| `/expand` | Take a wiki page and deepen it from sources |

## Key Rules

1. **Never modify `reviewed` or `stable` wiki pages** without explicit instruction.
2. **Never modify files in `/sources/`** — they are immutable.
3. **Always include frontmatter** on wiki and source pages. See `/schema/agent-protocol.md` for formats.
4. **Flag contradictions** in `/wiki/contradictions.md`. Do not silently resolve.
5. **Cite sources** with `[[source-filename]]` syntax in wiki pages.
6. **Use wikilinks** `[[page-name]]` to build the knowledge graph.
7. **Commit after each meaningful unit of work.** Message format: `ingest: source-name`, `wiki: page-name`, etc.

## Before You Start

1. Read `/schema/agent-protocol.md` for the full operating rules.
2. Read `/schema/tags.md` for the tag taxonomy.
3. Check `/wiki/index.md` for the current state of the knowledge base.
