# claudeclaw-starter

A minimal starter template for [ClaudeClaw](https://github.com/moazbuilds/claudeclaw) — a personal assistant layer for Claude Code.

## What's this?

ClaudeClaw turns Claude Code into a persistent, identity-aware assistant that:
- Remembers who you are across sessions via `CLAUDE.md`
- Runs as a Telegram/Discord bot (heartbeat daemon)
- Supports plugins for code review, scheduling, browser automation, and more

## Quick start

```bash
git clone https://github.com/doomL/claudeclaw-starter my-claudeclaw
cd my-claudeclaw
chmod +x setup.sh && ./setup.sh
```

Then edit `CLAUDE.md` — fill in your name, timezone, context, and give your assistant a personality.

Finally:
```bash
claude .
```

## Structure

```
.
├── CLAUDE.md              # Assistant identity + your personal context
├── config/
│   └── settings.json      # Registers claudeclaw marketplace, enables plugin
├── setup.sh               # One-shot setup script
└── README.md
```

## Plugins

After setup, install optional plugins inside Claude Code via `/install-skill`. Recommended:

- `ralph-loop@claude-plugins-official` — autonomous loop mode
- `hookify@claude-plugins-official` — prevent unwanted behaviors with hooks
- `commit-commands@claude-plugins-official` — git commit/push/PR shortcuts
- `dev-browser@dev-browser-marketplace` — browser automation

## Credits

Built on [ClaudeClaw](https://github.com/moazbuilds/claudeclaw) by moazbuilds.
