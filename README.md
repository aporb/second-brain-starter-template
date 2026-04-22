# Second Brain Starter Template

A persistent, interlinked markdown knowledge base that you and your AI agent build together.

**Clone it. Open in Obsidian. Connect your agent. Start building.**

---

## What Is This?

This is a starter template for building an **LLM Wiki** — a living knowledge base where you curate sources and your AI agent synthesizes them into interconnected wiki pages. It implements the [Karpathy LLM Wiki](https://x.com/karpathy) pattern: the vault isn't passive filing, it's an active knowledge graph the agent maintains.

The template is **agent-agnostic**. It works with Claude Code, OpenAI Codex, OpenCode, Cursor, GitHub Copilot, or any agent that can read markdown and follow instructions.

## Architecture

Four zones, each with a distinct owner and access rules:

```
/sources/    → Raw materials. You curate, agent ingests. Immutable.
/wiki/       → Synthesized knowledge. Agent writes, you review.
/journal/    → Your thinking. You write, agent reads.
/schema/     → The rules. You set them, agent follows them.
```

| Zone | Agent Access | Human Access |
|------|-------------|-------------|
| Sources | Read only | Read + write |
| Wiki | Read + write (drafts only) | Read + write (all) |
| Journal | Read only | Read + write |
| Schema | Read only | Read + write |

### Status Lifecycle

- Sources: `unread → reading → processed`
- Wiki: `draft → reviewed → stable`
- Once a wiki page is `reviewed` or `stable`, the agent cannot modify it without your explicit instruction.

### Contradictions

When sources disagree, the agent flags the conflict in `/wiki/contradictions.md` instead of silently picking one version. You decide.

## Quick Start

### 1. Clone and Open

```bash
git clone https://github.com/aporb/second-brain-starter-template.git my-vault
cd my-vault
```

Open the `my-vault` folder in Obsidian. Zero plugins required — it works out of the box.

### 2. Connect Your Agent

Point your AI agent at the vault directory. The agent reads the instruction files:

| Agent | Instruction File |
|-------|-----------------|
| Claude Code | `CLAUDE.md` + `.claude/commands/` |
| Cursor | `.cursorrules` |
| GitHub Copilot | `copilot-instructions.md` |
| Any other | `AGENTS.md` |

All four files point to `/schema/agent-protocol.md` as the single source of truth. Update the protocol once, all agents stay in sync.

### 3. Start Building

1. Drop a source into `/sources/` (article, paper, transcript — as markdown).
2. Run `/ingest` (Claude Code) or tell your agent to process the source.
3. The agent reads the source, creates wiki pages, links them together.
4. Review the wiki pages. Mark them `reviewed` when you're satisfied.
5. Repeat.

## Slash Commands (Claude Code)

| Command | What It Does |
|---------|-------------|
| `/ingest` | Read a source, create wiki pages, cross-reference |
| `/ask` | Query the wiki using existing synthesized knowledge |
| `/research` | Research a topic, ingest sources, build wiki pages |
| `/daily` | Create today's journal entry scaffold |
| `/sync` | Git pull, add, commit, push |
| `/status` | Show vault health (unprocessed sources, stale pages, contradictions) |
| `/expand` | Take a wiki page and deepen it from sources |

For other agents, equivalent workflows are documented in `AGENTS.md`.

## Git Workflow

### For Solo Use

Commit directly to `main`. The `/sync` command or `scripts/sync.sh` handles the cycle:

```bash
./scripts/sync.sh "wiki: added page on topic-x"
```

Or without a message — it auto-detects what changed:

```bash
./scripts/sync.sh
# → "update: sources:1,wiki:2"
```

### For Collaborative Use

Branch per session, merge after review:

```bash
git checkout -b agent/2024-01-15-research-topic
# ... agent does work ...
git push origin agent/2024-01-15-research-topic
# review and merge via PR
```

### Commit Message Format

| Prefix | When |
|--------|------|
| `ingest:` | After processing a source |
| `wiki:` | After creating or updating a wiki page |
| `journal:` | After a journal entry |
| `schema:` | After updating schema files |
| `update:` | Mixed changes |

## Date Handling

**The agent always runs `date +%Y-%m-%d` to get the local system date** before creating or updating any file. Never infer dates from timestamps or metadata — the system clock is the source of truth. This ensures frontmatter dates are accurate regardless of timezone or session context.

## Agent Discovery

This repo includes `llms.txt` and `llms-full.txt` at the root, following the [llmstxt.org](https://llmstxt.org) convention. Any agent that hits this repo gets a quick orientation file automatically.

## What This Is Not

- **Not a plugin collection** — zero plugins required. Obsidian works out of the box.
- **Not a sync solution** — bring your own git workflow. The `scripts/sync.sh` is a helper, not a framework.
- **Not a database** — pure markdown + git. Your data is always portable.
- **Not agent-specific** — works with any agent that reads markdown and follows instructions.

## Directory Structure

```
/
├── CLAUDE.md                    # Claude Code instructions
├── AGENTS.md                    # Agent-agnostic instructions
├── .cursorrules                 # Cursor rules
├── copilot-instructions.md      # GitHub Copilot instructions
├── llms.txt                     # Agent discovery (short)
├── llms-full.txt                # Agent discovery (full reference)
├── README.md                    # You are here
├── .claude/commands/            # Claude Code slash commands
│   ├── ingest.md
│   ├── ask.md
│   ├── research.md
│   ├── daily.md
│   ├── sync.md
│   ├── status.md
│   └── expand.md
├── sources/                     # Raw materials (immutable)
│   ├── README.md
│   └── _template.md
├── wiki/                        # Synthesized knowledge
│   ├── README.md
│   ├── _template.md
│   ├── index.md
│   └── contradictions.md
├── journal/                     # Human thinking
│   ├── README.md
│   └── _template.md
├── schema/                      # Rules
│   ├── README.md
│   ├── agent-protocol.md
│   ├── tags.md
│   └── templates.md
└── scripts/                     # Utility scripts
    └── sync.sh
```

## License

MIT — use it however you want. No attribution required.
