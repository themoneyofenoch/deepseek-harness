# Ammaniel's DSH settings — backup

Snapshot of the local DeepSeek Harness setup. Taken 2026-10-19, America/Chicago.
Restoring these files onto a fresh Mac brings the same agent back.

## What is here

| Path | What it is | Restores to |
|---|---|---|
| `AGENTS.md` | the binding rules every Bot reads | `~/.dsh/AGENTS.md` |
| `persona.md` | who Ammaniel is, tone, how to talk | `~/.dsh/persona.md` |
| `DESIGN.md` | visual rules (light backgrounds, colours) | `~/.dsh/DESIGN.md` |
| `SAFARI-CONTROL.md` | how the Safari tool is driven | `~/.dsh/SAFARI-CONTROL.md` |
| `lessons.md` | lessons learned | `~/.dsh/lessons.md` |
| `skills/` | every installed skill (gpp, office, plugin-*, app-store-ship…) | `~/.dsh/skills/` |
| `bin/` | `storeship` (Apple + Google shipping), `safari` (real Safari control) | `~/.dsh/bin/` |
| `bots.json` | all 33 Bots: name, role, colour, model, effort, work dir, instructions, main flag | see restore below |
| `rooms.json` | the 7 group chats: name, mode, notice, members, admin | see restore below |
| `prefs.json` | theme + motion | see restore below |
| `profile/cordis.patch.yml` | profile overrides (default model, search keys, bot ratio…) | `~/.dsh/profiles/desktop/cordis.patch.yml` |
| `profile/desktop-package.json` | desktop profile bundle list | `~/.dsh/profiles/desktop/package.json` |
| `math-snippets.json` | composer text expansion (`yy` → `ai@nakfaai.com`) | `~/.dsh/math-snippets.json` |

## What is NOT here, on purpose

Secrets (`.credentials.yaml`, `bot/secrets.json`, API keys, tokens), chat sessions,
transcripts, logs, caches, `node_modules`.

## Restore, step by step

1. Install DeepSeek Harness, then open it once so `~/.dsh` is created.
2. Copy the top-level files back into `~/.dsh/` (`AGENTS.md`, `persona.md`, `DESIGN.md`,
   `SAFARI-CONTROL.md`, `lessons.md`, `math-snippets.json`), and `skills/` and `bin/` with them.
   Then `chmod +x ~/.dsh/bin/storeship ~/.dsh/bin/safari`.
3. Profile: `cp settings/profile/cordis.patch.yml ~/.dsh/profiles/desktop/` and
   `cp settings/profile/desktop-package.json ~/.dsh/profiles/desktop/package.json`,
   then reinstall the bundles it lists (`pnpm add` each, inside the profile folder).
4. Bots and rooms: `bots.json` and `rooms.json` are the source of truth. Re-create the Bots in
   the sidebar with the same name, role, colour, model and instructions (the `instructions`
   field is the Bot's full brief), then re-create the group chats with the same name, mode,
   notice and members.
5. Secrets must be re-entered by hand — the Bot settings page takes them as cards.
6. Reopen the app. Everything reads its rules from `~/.dsh/AGENTS.md` at the start of each turn.

## Rules that are easy to lose

- Ask before acting. Short replies. Tap-to-answer card first.
- Light backgrounds only, bright, never dark.
- Write the want, not the negation.
- Full absolute path for every file, no space, no apostrophe, checked with `ls -l` first.
- Apple App Store **Submit** and Google Play **publish** stay Ammaniel's click.
- `storeship state` is the first command of any shipping task.
