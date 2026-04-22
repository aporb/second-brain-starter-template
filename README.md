<div align="center">

# 🧠 Second Brain Starter Template

### A persistent knowledge base you build with your AI agent.

**Clone → Open in Obsidian → Connect your agent → Start building.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![Agent Agnostic](https://img.shields.io/badge/agent-agnostic-blue?style=flat-square)](https://github.com/aporb/second-brain-starter-template)
[![Zero Plugins](https://img.shields.io/badge/zero_plugins-required-green?style=flat-square)](https://obsidian.md)
[![Markdown](https://img.shields.io/badge/pure-markdown-white?style=flat-square)](https://en.wikipedia.org/wiki/Markdown)

</div>

---

## The Idea

You read things. Articles, papers, books, transcripts. You learn from them. Then you forget most of it.

Note-taking apps don't solve this. They're filing cabinets — you dump things in and never find them again. Search helps, but search only finds what you already know you wrote.

**This template does something different.** Your AI agent reads your sources, synthesizes them into connected wiki pages, and builds a living knowledge graph that grows every time you add something new. You curate. The agent connects. You both remember.

This is sometimes called an **LLM Wiki** — a knowledge base that an AI agent actively maintains, not just a folder of notes you hope to revisit.

---

## How It Works

```
You drop sources in →    /sources/     (you own this)
                          ↓
Agent reads & connects → /wiki/        (agent writes, you review)
                          ↓
You think & reflect in → /journal/     (you own this too)
                          ↑
Agent follows rules from → /schema/    (you set the rules)
```

**Four zones. Clear ownership. No confusion about who does what.**

| Zone | What Goes Here | Who Owns It | What the Agent Does |
|------|---------------|-------------|-------------------|
| **Sources** | Articles, papers, transcripts — raw material | You | Reads them. Never modifies. |
| **Wiki** | Synthesized knowledge — connected pages | Agent (you review) | Creates and updates pages. |
| **Journal** | Daily notes, reflections, decisions | You | Reads for context. Never modifies. |
| **Schema** | Rules, tags, templates | You | Follows them. Never changes. |

### The Workflow

1. **You** save an article into `/sources/` (as a markdown file).
2. **You** tell the agent to process it (one command).
3. **The agent** reads the source, identifies key concepts, creates wiki pages, and links everything together.
4. **You** review the wiki pages. If something's wrong, fix it. If it's right, mark it reviewed.
5. Repeat. Over time, you get a connected web of knowledge that the agent maintains for you.

### Safety Built In

- The agent **cannot modify** anything you've reviewed and approved.
- The agent **cannot change** your source files. Ever.
- When sources contradict each other, the agent **flags the conflict** instead of silently picking one. You decide.
- The agent **never fabricates** — every claim in a wiki page cites its source.

---

## Quick Start

### What You Need

- **[Obsidian](https://obsidian.md)** — free note-taking app. Download it.
- **An AI agent** — Claude Code, Cursor, GitHub Copilot, or any agent that can read files and follow instructions.
- **A GitHub account** — to download this template. Free.

### Step 1: Download This Template

Click the green **"Code"** button above and select **"Download ZIP"**, or if you use the terminal:

```bash
git clone https://github.com/aporb/second-brain-starter-template.git my-vault
```

### Step 2: Open in Obsidian

1. Open Obsidian.
2. Click **"Open folder as vault"**.
3. Select the folder you just downloaded.
4. That's it. No plugins to install. No settings to configure.

### Step 3: Connect Your Agent

Point your AI agent at the vault folder. The agent reads instruction files that are already in the repo — no setup needed on your end.

| Your Agent | What It Reads |
|-----------|--------------|
| **Claude Code** | `CLAUDE.md` + 7 built-in slash commands |
| **Cursor** | `.cursorrules` |
| **GitHub Copilot** | `copilot-instructions.md` |
| **Anything else** | `AGENTS.md` |

All of them point to the same source of truth: `/schema/agent-protocol.md`. You update the rules in one place, every agent stays in sync.

### Step 4: Start Building

1. Save an article as a markdown file in `/sources/` (use the template there).
2. Tell your agent to process it:
   - Claude Code: type `/ingest`
   - Other agents: "Read the source file in /sources/ and create wiki pages from it"
3. Check `/wiki/` — your agent created pages and linked them together.
4. Review the pages. Mark them `reviewed` when you're satisfied.
5. Add more sources. Repeat.

---

## Built-in Commands (Claude Code)

If you use Claude Code, you get 7 slash commands out of the box:

| Command | What It Does |
|---------|-------------|
| `/ingest` | Process a source → create wiki pages → cross-reference |
| `/ask` | Ask a question → get an answer from your wiki |
| `/research` | Research a topic → ingest sources → build wiki pages |
| `/daily` | Create today's journal entry scaffold |
| `/sync` | Save your work (pull, commit, push to GitHub) |
| `/status` | Show vault health — what needs attention |
| `/expand` | Take a wiki page and deepen it from sources |

Using a different agent? The same workflows are documented in `AGENTS.md`.

---

## What's In The Box

```
second-brain-starter-template/
├── CLAUDE.md                 ← Claude Code reads this
├── AGENTS.md                 ← Any agent reads this
├── .cursorrules              ← Cursor reads this
├── copilot-instructions.md   ← GitHub Copilot reads this
├── llms.txt                  ← Agent discovery (short)
├── llms-full.txt             ← Agent discovery (full reference)
│
├── sources/                  ← You put raw material here
│   ├── README.md             (how to use this folder)
│   └── _template.md          (copy this for new sources)
│
├── wiki/                     ← Agent builds knowledge here
│   ├── README.md             (how this folder works)
│   ├── _template.md          (page template)
│   ├── index.md              (table of contents)
│   └── contradictions.md     (where conflicts get flagged)
│
├── journal/                  ← Your daily thinking
│   ├── README.md             (how to use this folder)
│   └── _template.md          (daily entry template)
│
├── schema/                   ← The rules
│   ├── README.md             (what's in here)
│   ├── agent-protocol.md     (the full operating rules)
│   ├── tags.md               (tag taxonomy)
│   └── templates.md          (page templates)
│
├── scripts/
│   └── sync.sh               ← Save your work in one command
│
└── .claude/commands/         ← 7 slash commands for Claude Code
    ├── ingest.md
    ├── ask.md
    ├── research.md
    ├── daily.md
    ├── sync.md
    ├── status.md
    └── expand.md
```

---

## FAQ

**Do I need to know how to code?**
No. If you can save a file and type a sentence to an AI agent, you can use this template. The Quick Start above walks you through everything.

**What if I don't use Claude Code?**
The template works with any AI agent. Claude Code gets the best experience (7 slash commands), but the core workflows — ingest sources, build wiki pages, flag contradictions — work with any agent that can read and write markdown files. Instructions for all agents are in `AGENTS.md`.

**Do I need Obsidian plugins?**
No. Zero plugins required. Obsidian works out of the box with this vault. Add plugins on your own if you want, but you don't need any.

**What's an LLM Wiki?**
A term coined by Andrej Karpathy. Instead of passively filing notes, an AI agent actively reads your sources, synthesizes them into connected pages, and maintains the knowledge base over time. The vault grows smarter as you add more to it.

**Can I use this with my team?**
Yes. The template supports branching workflows — each person works on a branch, then you merge after review. See the Git Workflow section in `AGENTS.md`.

**What if the agent writes something wrong?**
You review it. Wiki pages start as `draft` — the agent can modify them freely. Once you mark a page `reviewed`, the agent cannot change it without your explicit permission. You're always in control.

**Where does my data live?**
On your machine. Pure markdown files. No cloud, no database, no lock-in. You own everything.

**What does "agent-agnostic" mean?**
This template doesn't care which AI tool you use. Claude Code, Cursor, GitHub Copilot, OpenAI Codex, or anything else — they all read the same instruction files and follow the same rules.

---

## What This Is Not

- ❌ Not a plugin collection — zero plugins required
- ❌ Not a sync service — your data stays local
- ❌ Not a database — pure markdown, portable forever
- ❌ Not tied to one AI tool — works with any agent

---

## License

[MIT](LICENSE) — use it however you want. No attribution required.

---

<div align="center">

Built with the idea that knowledge should be **alive**, not filed away.

</div>
