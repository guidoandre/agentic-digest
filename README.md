# agentic-digest

A weekly, personalized digest on **agentic coding**, built to answer one question: *what should I try this week to get better at working with coding agents?*

Every Saturday morning an AI agent (Claude, running as a scheduled task) reads ~15 sources, filters out what I already use, and emails me 3–5 things worth trying, each with a one-line "why it matters to me" and the exact command to try it.

## How it works

```
 sources.yaml ──┐
                ├─► 1. Extract   candidate items from each source separately
 Gmail label ───┤   2. Dedupe    merge items covering the same thing
 (newsletters)  │   3. Select    new to me · tryable in <30 min · useful for my work
 web pages ─────┘   4. Remember  skip past proposals, learn from my "kept / dropped" replies
                    5. Compose   fill template.html → send one email
 setup.md ─────────► (what I already have: never re-proposed)
```

- **No code to deploy.** The agent reads this repo at run time; changing a file here changes next week's digest.
- **Feedback loop.** I reply to the email with e.g. `2 kept, 4 dropped`; the next run reads my reply and adjusts.
- **Safety.** Source content is treated as data, never as instructions. The agent only reads and proposes; it never installs or subscribes to anything.

## Files

| File | Purpose |
|---|---|
| [`instructions.md`](instructions.md) | The method: extraction, filtering criteria, memory, output rules |
| [`sources.yaml`](sources.yaml) | Newsletters, changelogs, skill repos, blogs |
| [`setup.md`](setup.md) | My current setup (skills, plugins, MCP servers) |
| [`template.html`](template.html) | Email template (inline-styled tables, Gmail-safe) |

## Sources

Newsletters (via a dedicated Gmail alias + label): Simon Willison, Elevate (Addy Osmani), AI Coding Daily, Latent Space / AINews, TLDR AI, Unwind AI, Vibe Coding Weekly, Maverick AI.
Web: Claude Code release notes, Anthropic Engineering, Codex and Cursor changelogs, Claude skill/plugin repos, practitioner blogs, Hacker News.

Sources that never contribute a kept item get pruned after a few weeks.
