# OpenClaw Backup Restore

**Backup, restore, rollback, validate, and GitHub-sync critical OpenClaw state.**

`openclaw-backup-restore` protects the files that make an OpenClaw agent feel like itself: personality, operator instructions, memory scaffolding, and optional real config.

**Best for:** backup, restore, rollback, daily GitHub backup, and recovery readiness.

---

# Why teams use it

- Protect `SOUL.md`, `USER.md`, `AGENTS.md`, and related state files
- Recover quickly after bad edits, deletions, or config mistakes
- Validate backup integrity with checksums
- Keep versioned recovery points instead of hoping git history is enough
- Push daily backups off-machine to GitHub

---

# What it protects

Core workspace state such as:

- `SOUL.md`
- `USER.md`
- `AGENTS.md`
- `IDENTITY.md`
- `TOOLS.md`
- `HEARTBEAT.md`
- `BOOTSTRAP.md`
- optional `~/.openclaw/openclaw.json`

By default, config backup is sanitized unless you explicitly choose real-config mode.

---

# Quick start

Install:

```bash
npm install
```

Create a backup:

```bash
node scripts/backup.mjs
```

Include real config:

```bash
node scripts/backup.mjs --raw-openclaw-config
```

List backups:

```bash
node scripts/list.mjs
```

Restore latest backup:

```bash
node scripts/restore.mjs
```

Dry-run restore:

```bash
node scripts/restore.mjs --dry-run
```

Validate integrity:

```bash
node scripts/validate.mjs
```

---

# GitHub backup flow

Create a backup and push it off-machine:

```bash
node scripts/backup-and-push.mjs --remote origin
```

Push sanitized-config-only backup:

```bash
node scripts/backup-and-push.mjs --remote origin --sanitized-config-only
```

This repo is designed for daily backup workflows, rollback drills, and off-machine recovery.

---

# Core features

- timestamped backups
- named backups for milestones
- rollback after bad restore
- file-level restore
- checksum validation
- optional real config backup
- git add / commit / push workflow for off-machine copies

---

# Typical use cases

- “Back up my OpenClaw workspace”
- “Restore yesterday’s working state”
- “Roll back this bad change”
- “Validate that my backups are not corrupt”
- “Push daily OpenClaw backups to GitHub”

---

# Files

- `SKILL.md` — agent-facing routing and usage guide
- `RUNBOOK.md` — operations and recovery scenarios
- `FEATURE_DEFINITION.md` — positioning and roadmap
- `scripts/backup.mjs` — create a backup
- `scripts/restore.mjs` — restore a backup
- `scripts/list.mjs` — list available backups
- `scripts/validate.mjs` — verify backup integrity
- `scripts/backup-and-push.mjs` — create backup and git-push it

---

# Important limits

- Backups are only useful if restore paths are tested
- Real `openclaw.json` backups should live in private backup repos
- This repo improves recovery readiness, but it does not replace disaster-recovery drills

---

# Bottom line

If your OpenClaw agent matters, its workspace state should be recoverable on demand. This repo gives you the backup + restore foundation for that.
