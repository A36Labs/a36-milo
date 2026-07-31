# A36 Milo

> An open-source AI community manager for Telegram, built by A36 Labs.

[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![Cloudflare Workers](https://img.shields.io/badge/Cloudflare-Workers-F38020?logo=cloudflare&logoColor=white)](https://workers.cloudflare.com/)
[![Telegram Bot API](https://img.shields.io/badge/Telegram-Bot%20API-26A5E4?logo=telegram&logoColor=white)](https://core.telegram.org/bots/api)
[![Gemini](https://img.shields.io/badge/Google-Gemini-4285F4?logo=google&logoColor=white)](https://ai.google.dev/)

**A36 Milo** is an intelligent Telegram community manager designed to help communities stay active, useful and welcoming.

Milo can understand untagged conversations, respond in multiple languages, answer questions, remember short-term context, share verified organization information, welcome discussions, celebrate community milestones and automatically post scheduled prompts and technology observances.

The project runs on Cloudflare Workers and uses Google Gemini for intelligent conversations.

## Built by

**A36 Labs**  
https://a36labs.com

Original creator and maintainer:

**Laksh Dilliwal**  
https://x.com/LakshDilliwal

## Why Milo?

Most Telegram bots respond only to commands or mentions.

Milo is designed to behave more like an active community manager. It can understand ongoing discussions, identify when someone needs help, continue follow-up conversations and join relevant chats without taking over the group.

It is useful for:

- Developer communities
- Startup ecosystems
- Open-source communities
- University communities
- Technology groups
- Founder and investor networks
- Hackathons and builder programs
- Regional and global communities

## Features

### Intelligent community conversations

- Responds to tagged and untagged messages
- Understands normal conversational language
- Continues follow-up conversations without requiring another tag
- Detects questions, builder updates, milestones and help requests
- Uses recent member and group context
- Avoids replying to every message
- Supports configurable engagement levels

### Multilingual greetings

Milo can recognize and respond to greetings in multiple languages, including:

- English
- Spanish
- Portuguese
- French
- German
- Italian
- Hindi and Hinglish
- Arabic
- Japanese
- Chinese
- Korean
- Indonesian
- Russian

### Community engagement

- Daily conversation prompts
- Builder check-ins
- Project and launch discussions
- Supportive replies when members are stuck
- Positive milestone reactions
- Short, community-friendly responses
- Configurable response cooldowns

### Telegram integration

- Telegram webhook support
- Bot command menu
- Inline buttons
- Message reactions
- Typing indicators
- Group privacy diagnostics
- Support for untagged group messages
- Restriction to one approved community
- Automatic exit from unauthorized groups
- Protection against repeated webhook updates

### Scheduled observances

Milo can automatically recognize and post short explanations for global and technology-related observances, including:

- World Wide Web Day
- Bitcoin Pizza Day
- Bitcoin White Paper Day
- World Quantum Day
- World Backup Day
- Data Privacy Day
- Programmers’ Day
- Software Freedom Day
- World Standards Day
- International Internet Day
- World Computer Literacy Day
- World Science Day
- World Engineering Day
- International Day of Light
- World Intellectual Property Day
- Republic Day of India
- Independence Day of India
- Other configurable observances

Custom and date-specific observances can also be added by the administrator.

### Organization knowledge

Milo can answer verified questions about:

- Organization information
- Events
- Opportunities
- Partnerships
- Community links
- Newsletters
- Podcasts
- Programs
- Current activities
- Custom administrator-added knowledge

### Safety and access controls

- Secrets remain inside Cloudflare
- Private bot conversations can be limited to the administrator
- Only one approved Telegram group can use the bot
- Messages from other bots are ignored
- Automatic channel forwards can be ignored
- Spam-like messages are filtered
- Financial predictions and personalized investment calls are restricted
- Live information is not invented when browsing is unavailable

## Technology stack

- **Cloudflare Workers** for serverless hosting
- **Cloudflare Workers KV** for settings, context and persistent knowledge
- **Telegram Bot API** for Telegram messaging
- **Google Gemini API** for intelligent responses
- **JavaScript** with no external runtime dependencies

## Project structure

```text
a36-milo/
├── worker.js
├── README.md
├── LICENSE
├── NOTICE
├── package.json
├── wrangler.jsonc
├── .gitignore
├── .dev.vars.example
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
└── .github/
    ├── workflows/
    │   └── deploy.yml
    ├── PULL_REQUEST_TEMPLATE.md
    └── ISSUE_TEMPLATE/
```

## Requirements

Before deploying Milo, create:

1. A Telegram bot through BotFather
2. A Google Gemini API key
3. A Cloudflare account
4. A Cloudflare Worker
5. A Cloudflare Workers KV namespace
6. A Telegram community group

## Environment variables and secrets

Configure the following values in Cloudflare Workers.

### Required secrets

```text
TELEGRAM_BOT_TOKEN
TELEGRAM_WEBHOOK_SECRET
GEMINI_API_KEY
```

### Required variables

```text
BOT_NAME
BOT_USERNAME
ADMIN_USERNAME
DAILY_AI_LIMIT
GEMINI_MODEL
```

Example values:

```text
BOT_NAME=Milo
BOT_USERNAME=YourTelegramBotUsername
ADMIN_USERNAME=YourTelegramUsername
DAILY_AI_LIMIT=100
GEMINI_MODEL=gemini-3.5-flash-lite
```

### Required KV binding

```text
Variable name: MILO_KV
KV namespace: your KV namespace
```

Never commit real API keys, bot tokens, webhook secrets or Cloudflare credentials to GitHub.

## Telegram bot configuration

Inside BotFather:

1. Create a bot using `/newbot`
2. Disable group privacy using `/setprivacy`
3. Select the bot
4. Choose **Disable**
5. Allow the bot to join groups
6. Add the bot to your Telegram community
7. Promote it to administrator

Milo does not need permission to delete messages, ban users or pin messages unless you intentionally add moderation features.

## Cloudflare deployment

### Dashboard deployment

1. Open Cloudflare
2. Go to **Workers & Pages**
3. Create a Worker
4. Open **Edit code**
5. Replace the example code with `worker.js`
6. Add the required variables and secrets
7. Bind the KV namespace as `MILO_KV`
8. Deploy the Worker

### Register the Telegram webhook

After deployment, open:

```text
https://YOUR-WORKER.workers.dev/setup-webhook
```

A successful response should include:

```json
{
  "ok": true,
  "bot_privacy_disabled": true
}
```

Check the connection using:

```text
https://YOUR-WORKER.workers.dev/telegram-status
```

The response should show:

```json
{
  "privacy_mode_disabled": true,
  "community_administrator": true,
  "should_receive_untagged_group_messages": true
}
```

## Link the Telegram community

First, privately message Milo:

```text
/whoami
```

Then send this command inside the intended Telegram community:

```text
/chatid
```

Milo will save that group as the approved community.

After the group is linked, Milo will leave other groups where it is added.

## Cron trigger

Create a Cloudflare Cron Trigger:

```text
30 * * * *
```

This invokes Milo once every hour.

The Worker checks whether a daily prompt or observance is due. It does not automatically send a message every hour.

Default schedule:

```text
Holiday greeting: 9:00 AM local time
Daily prompt: 7:00 PM local time
```

Cloudflare Cron Triggers use UTC. Milo applies its configured timezone offset internally.

## Public commands

```text
/start
/about
/events
/earn
/partner
/signal
/podcast
/radar
/today
/links
/rules
/forgetme
/help
```

## Administrator commands

Administrator commands should normally be used in Milo’s private chat.

```text
/whoami
/status
/diagnostics
/knowledge
/setknowledge key | information
/deleteknowledge key
/setactivity text
/clearactivity
/setpersona instruction
/clearpersona
/setengagement low
/setengagement balanced
/setengagement high
/settimezone offset_in_minutes
/setprompttime hour
/setholidaytime hour
/setdaily on
/setdaily off
/setholidays on
/setholidays off
/setreactions on
/setreactions off
/setholiday MM-DD | Name | Short reason
/setholiday YYYY-MM-DD | Name | Short reason
/deleteholiday date
/holidays
/testholiday MM-DD
/holidaytoday
/announce text
/prompt text
/clearcontext
/resetcooldowns
/pause
/resume
/adminhelp
```

## Examples

### Add organization knowledge

```text
/setknowledge residency | Applications for the new residency will open soon.
```

### Update current activity

```text
/setactivity A36 Labs is organizing a builder meetup this month.
```

### Add a recurring observance

```text
/setholiday 08-12 | Open Source Community Day | A day to celebrate open collaboration and community-led software.
```

### Add a one-time observance

```text
/setholiday 2026-11-08 | Diwali | Diwali celebrates light, renewal and hope over darkness.
```

### Set India timezone

```text
/settimezone 330
```

### Change engagement level

```text
/setengagement high
```

## AI usage limits

Milo includes an internal daily AI usage counter.

The default limit is:

```text
100 AI responses per UTC date
```

This is an application-level limit used to control usage. It is separate from Google Gemini’s own API quotas.

Change the internal limit through the Cloudflare variable:

```text
DAILY_AI_LIMIT
```

## Privacy

Milo stores limited short-term conversation context in Cloudflare Workers KV so it can continue recent conversations.

Default behavior:

- Member conversation context expires automatically
- Group context expires automatically
- Follow-up memory expires automatically
- Members can use `/forgetme` to clear recent stored context
- The bot does not require access to private messages from regular members
- Administrator private messages are used for configuration

Community operators should clearly disclose the use of automated community assistance and review applicable privacy requirements before deployment.

## Security

Do not commit real credentials.

Keep these values encrypted:

```text
TELEGRAM_BOT_TOKEN
TELEGRAM_WEBHOOK_SECRET
GEMINI_API_KEY
CLOUDFLARE_API_TOKEN
```

To report a security issue, follow the instructions in `SECURITY.md`.

Do not publish security vulnerabilities in public GitHub issues.

## Contributing

Contributions from developers, builders and community operators are welcome.

Useful contribution areas include:

- New language support
- Improved conversation classification
- Better moderation tooling
- Community analytics
- Safer knowledge management
- Additional Telegram features
- Better observance support
- Testing and documentation
- Deployment improvements
- Support for additional AI providers

Read `CONTRIBUTING.md` before opening a pull request.

## Roadmap

Potential future improvements:

- Optional moderation tools
- Community analytics dashboard
- Semantic long-term knowledge search
- AI-provider adapters
- Configurable personality presets
- Message summarization
- Community onboarding flows
- Event and opportunity integrations
- Human handoff workflows
- Admin web dashboard
- Multi-community support
- Plugin and integration system

Roadmap items are proposals, not guaranteed commitments.

## License

A36 Milo is licensed under the Apache License 2.0.

See the [LICENSE](LICENSE) file for the complete license terms.

```text
Copyright 2026 A36 Labs
```

Contributors retain copyright in their contributions and provide them under the project’s Apache 2.0 license.

## Attribution

An open-source project by **A36 Labs**.

Built by **Laksh Dilliwal**  
https://x.com/LakshDilliwal

## Community

- Website: https://a36labs.com
- Events: https://luma.com/a36
- X: https://x.com/A36Labs
- LinkedIn: https://linkedin.com/company/a36labs
- Instagram: https://www.instagram.com/a36labs
- YouTube: https://www.youtube.com/@a36labs
- Telegram: https://t.me/A36Labs
- Global community: https://t.me/A36Global
- Discord: https://discord.gg/8rzpt4tCqE
- Newsletter: https://a36signal.substack.com/

---

**Build. Connect. Launch.**
