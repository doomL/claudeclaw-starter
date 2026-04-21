# claudeclaw-starter

> A production-ready starter for [ClaudeClaw](https://github.com/moazbuilds/claudeclaw) — Claude Code as your personal AI assistant, running 24/7 via Telegram.

---

## What is this?

ClaudeClaw turns Claude Code into a persistent, identity-aware assistant that lives on your server and talks to you over Telegram (or Discord). It's not a chatbot wrapper — it's Claude Code itself, with full access to your tools, files, and shell, controlled from your phone.

This starter gives you a pre-configured setup with:

- **Telegram bot** — chat with your assistant anywhere, send voice messages, images
- **OpenRouter support** — use any model (Claude, GPT, Gemini, Llama...) as primary or fallback
- **Image generation** — ask for an image, get one inline via Gemini or any OpenRouter image model
- **Agentic mode** — auto-routes messages to the right model based on intent (planning vs implementation)
- **Heartbeat daemon** — always-on background process, survives session resets
- **Cron jobs** — schedule recurring prompts (daily reports, server checks, reminders)
- **Web UI** — optional browser dashboard at `localhost:4632`
- **Plugin ecosystem** — one-command install for code review, browser automation, loops, hooks, and more

---

## Quick start

```bash
git clone https://github.com/doomL/claudeclaw-starter my-claudeclaw
cd my-claudeclaw
chmod +x setup.sh && ./setup.sh
```

Copy the settings template and fill in your credentials:

```bash
cp config/claudeclaw-settings.template.json .claude/claudeclaw/settings.json
```

Edit `.claude/claudeclaw/settings.json` — at minimum set:
- `telegram.token` — your bot token from [@BotFather](https://t.me/BotFather)
- `telegram.allowedUserIds` — your Telegram user ID (get it from [@userinfobot](https://t.me/userinfobot))
- `api` — your Anthropic API key (or leave empty to use Claude Code's default auth)
- `fallback.api` — optional OpenRouter key for fallback/image models

Then edit `CLAUDE.md` — give your assistant a name, personality, and fill in your context.

```bash
claude .
```

---

## Telegram features

Once your bot is running, you can:

| What | How |
|------|-----|
| Send a message | Just text it |
| Send a voice note | Transcribed automatically via Whisper |
| Send an image | Attached as context to your message |
| Ask for an image | "generate me a..." → image comes back inline |
| Schedule a task | "remind me to check the server every day at 8am" |
| Run a one-shot prompt | `/start "summarize my git log"` |

---

## Agentic model routing

ClaudeClaw can automatically pick the right model based on what you're asking:

```json
"agentic": {
  "enabled": true,
  "modes": [
    { "name": "planning", "model": "opus", "keywords": ["plan", "design", "research"] },
    { "name": "implementation", "model": "sonnet", "keywords": ["code", "fix", "deploy"] }
  ]
}
```

Use OpenRouter models as fallback: `"model": "openrouter/google/gemini-2.5-pro"`.

---

## Plugins

After setup, install plugins inside Claude Code with `/install-skill`:

| Plugin | What it does |
|--------|--------------|
| `ralph-loop@claude-plugins-official` | Autonomous loop mode — runs prompts on repeat |
| `hookify@claude-plugins-official` | Prevent unwanted behaviors with pre-tool hooks |
| `commit-commands@claude-plugins-official` | `/commit`, `/push`, `/pr` shortcuts |
| `code-review@claude-plugins-official` | AI code review on your diffs |
| `pr-review-toolkit@claude-plugins-official` | Full PR review suite |
| `dev-browser@dev-browser-marketplace` | Browser automation with persistent state |
| `plugin-dev@claude-plugins-official` | Tools for building your own plugins |

---

## File structure

```
.
├── CLAUDE.md                              # Assistant identity + your personal context
├── config/
│   ├── settings.json                      # Claude Code: registers claudeclaw marketplace
│   └── claudeclaw-settings.template.json  # ClaudeClaw: credentials + behavior template
├── setup.sh                               # One-shot setup script
└── README.md
```

The ClaudeClaw runtime config lives at `.claude/claudeclaw/settings.json` inside your project — **not** the Claude Code `settings.json`. Two different files, both important.

---

## Credits

Built on [ClaudeClaw](https://github.com/moazbuilds/claudeclaw) by [moazbuilds](https://github.com/moazbuilds).
