# Weilliptic Claude Code Plugin

Claude Code plugin that audits AI-assisted code changes on Weilchain. Automatically records every file edit, session, and commit as a receipt — providing tamper-proof provenance for AI-generated code.

## Setup

### Prerequisites

- [Claude Code](https://claude.ai/code) installed
- A Weilliptic account file (set as `WEILLIPTIC_ACCOUNT_FILE` environment variable)

```bash
export WEILLIPTIC_ACCOUNT_FILE="/path/to/your/account.json"
```

### Install

```bash
/plugin install weilliptic
```

Or test locally:

```bash
claude --plugin-dir /path/to/claude-code-hooks
```

## What it does

| Hook | Trigger | Purpose |
|---|---|---|
| `audit-hook` | Every Write/Edit/Bash tool use | Records each file edit as a blockchain receipt |
| `session-start-hook` | Session start | Initializes session tracking |
| `session-end-hook` | Session end | Persists session receipts to Weilchain |
| `git-commit-hook` | Git post-commit | Persists receipt ledger on commit |

## Commands

- `/install-git-hooks` — Installs Weilliptic git hooks for commit-time receipt persistence

## View Receipts

[Codensics](https://codensics.weilliptic.ai) lets you load any GitHub repository and view the audit receipts for each commit — showing who changed what, when, and with which AI session.

## License

MIT
