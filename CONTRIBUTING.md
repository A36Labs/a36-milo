# Contributing to A36 Milo

Thank you for contributing to A36 Milo.

A36 Milo is an open-source AI community manager for Telegram, developed and maintained by A36 Labs.

We welcome contributions from developers, builders, community managers, designers, researchers, technical writers and open-source contributors worldwide.

## Ways to contribute

You can help improve Milo by:

- Fixing bugs
- Improving documentation
- Optimizing Worker performance
- Adding language support
- Improving conversation quality
- Improving community engagement logic
- Adding Telegram features
- Improving privacy and security
- Adding tests and validation
- Improving deployment workflows
- Suggesting useful features
- Reviewing issues and pull requests

Contributions should support Milo’s goal of being a useful, safe and community-friendly AI assistant.

## Before contributing

Before submitting a change:

1. Read the project `README.md`.
2. Review existing issues and pull requests.
3. Avoid creating duplicate issues.
4. Keep each change focused on one feature or problem.
5. Do not include credentials, private data or production identifiers.
6. Follow the project’s Code of Conduct.
7. Preserve existing copyright, attribution and license notices.

## Editing through GitHub

The project can be edited entirely through the GitHub website. Local development is optional.

### A36 Labs maintainers

Maintainers with write access to `A36Labs/a36-milo` do not need to fork the repository.

For small documentation, configuration or typo fixes:

1. Open the relevant file on GitHub.
2. Click the pencil icon.
3. Make the required changes.
4. Click **Commit changes**.
5. Add a clear commit message.
6. Select **Commit directly to the `main` branch**.
7. Confirm the commit.

For larger features, code changes or security-related updates:

1. Open the relevant file on GitHub.
2. Click the pencil icon.
3. Make the required changes.
4. Click **Commit changes**.
5. Select **Create a new branch for this commit and start a pull request**.
6. Use a descriptive branch name.
7. Review the changes in the pull request.
8. Merge the pull request after approval and testing.

### Community contributors

Contributors without write access can still propose changes through GitHub.

You may:

1. Open the relevant file.
2. Click the pencil icon.
3. Make your changes.
4. GitHub may create a personal fork automatically.
5. Submit the change as a pull request to `A36Labs/a36-milo`.

You can also create an issue before beginning a major feature so the idea can be discussed with the maintainers.

## Reporting bugs

Before reporting a bug, search the existing issues to check whether it has already been reported.

A useful bug report should include:

- A clear title
- A description of the problem
- Steps to reproduce it
- Expected behavior
- Actual behavior
- Relevant error messages
- Cloudflare Worker or Wrangler version
- Telegram bot configuration details
- Screenshots when useful
- Sanitized logs with all credentials removed

Never include:

```text
TELEGRAM_BOT_TOKEN
TELEGRAM_WEBHOOK_SECRET
GEMINI_API_KEY
CLOUDFLARE_API_TOKEN
CLOUDFLARE_ACCOUNT_ID
Private Telegram user IDs
Private Telegram group IDs
Production KV namespace IDs
```

Do not post security vulnerabilities as public GitHub issues. Follow the private reporting process in `SECURITY.md`.

## Suggesting features

Feature requests should explain:

- The problem being solved
- Who would benefit from the feature
- How the feature should work
- How it fits Milo’s purpose
- Privacy or security considerations
- Telegram permission requirements
- Possible AI usage or infrastructure costs
- Alternative solutions considered

Features should not make Milo unnecessarily intrusive, spammy or unsafe.

## Code guidelines

Please follow these guidelines when changing `worker.js`:

- Use clear and readable JavaScript.
- Prefer small and focused functions.
- Use descriptive function and variable names.
- Avoid unnecessary external dependencies.
- Handle Telegram API errors safely.
- Handle Gemini API errors safely.
- Never log credentials or secret values.
- Validate external input before processing it.
- Preserve webhook secret validation.
- Preserve duplicate-update protection.
- Preserve administrator access controls.
- Preserve the approved-community allow-list.
- Do not connect testing to the production KV namespace.
- Do not invent current or live information when browsing is unavailable.
- Keep Telegram responses concise and readable.
- Test multilingual behavior carefully.
- Avoid replying to every community message.
- Respect member privacy and context-expiration controls.
- Update documentation when behavior or commands change.

## A36 knowledge and links

Changes to official A36 Labs information should use verified links and details.

Official project references include:

- Website: https://a36labs.com
- Events: https://luma.com/a36
- X: https://x.com/A36Labs
- Telegram channel: https://t.me/A36Labs
- Global community: https://t.me/A36Global
- Discord: https://discord.gg/8rzpt4tCqE
- Newsletter: https://a36signal.substack.com/
- LinkedIn: https://linkedin.com/company/a36labs
- Instagram: https://www.instagram.com/a36labs
- YouTube: https://www.youtube.com/@a36labs

Do not replace official links with unofficial, shortened or unverified links.

## Security requirements

Every contribution must protect project and community data.

Do not commit:

```text
.env
.env.*
.dev.vars
.dev.vars.*
API keys
Telegram bot tokens
Webhook secrets
Cloudflare API tokens
Private logs
Production database exports
Member conversation data
```

Only placeholder values should appear in example files.

Safe example:

```text
GEMINI_API_KEY="replace_with_your_gemini_api_key"
```

Unsafe example:

```text
GEMINI_API_KEY="actual-secret-key"
```

Before committing, search your changes for:

```text
AIza
bot token
api_key
secret
password
Bearer
Authorization
```

Remove any real sensitive values immediately.

## Cloudflare KV

Use a separate development KV namespace for testing.

Do not connect local development, previews, forks or pull requests to the production A36 Milo KV namespace.

Production KV may contain:

- Administrator configuration
- Community configuration
- Custom knowledge
- Conversation context
- Engagement settings
- Scheduled observances
- Usage counters

Changes affecting KV keys should document:

- New keys being created
- Expiration times
- Migration requirements
- Backward compatibility
- Privacy impact

## Telegram testing

When changing Telegram behavior, test the relevant scenarios.

Recommended checks include:

- Private `/start`
- Private `/status`
- Private `/diagnostics`
- Public command responses
- Tagged group messages
- Untagged group messages
- Follow-up conversation memory
- Multilingual greetings
- Administrator-only commands
- Unauthorized private messages
- Unauthorized group behavior
- Automatic channel forwards
- Duplicate webhook updates
- Telegram message reactions
- Inline buttons
- AI limit handling
- Gemini failure fallback
- Context clearing with `/forgetme`

Do not test experimental code in the production A36 community without approval.

## Documentation changes

Documentation contributions are welcome.

Documentation should be:

- Clear
- Accurate
- Easy to follow
- Written in simple English
- Free from unnecessary jargon
- Consistent with the current code
- Updated when commands or configuration change

Do not document features that are not implemented.

## Branch naming

Use short and descriptive branch names.

Examples:

```text
feature/add-language-support
feature/community-onboarding
fix/webhook-duplicate-update
fix/discord-link
docs/improve-readme
security/validate-telegram-payload
refactor/context-storage
performance/reduce-kv-requests
```

## Commit messages

Use clear commit messages that describe the change.

Recommended format:

```text
type: description
```

Examples:

```text
feat: add French greeting detection
fix: prevent duplicate webhook processing
docs: improve Cloudflare setup guide
security: strengthen webhook validation
refactor: simplify conversation context storage
performance: reduce unnecessary KV reads
chore: update development configuration
```

Common commit types:

- `feat` for a new feature
- `fix` for a bug fix
- `docs` for documentation
- `security` for security improvements
- `refactor` for code restructuring
- `performance` for optimization
- `test` for tests
- `chore` for maintenance or configuration

## Pull requests

Every pull request should:

- Have a clear title
- Explain what changed
- Explain why the change is needed
- Reference related issues
- Describe how it was tested
- Include screenshots when relevant
- Avoid unrelated changes
- Update documentation when required
- Contain no credentials or private information
- Preserve copyright and attribution notices
- Follow the Apache License 2.0

A pull request may be closed if it:

- Introduces harmful or unsafe behavior
- Exposes credentials or personal data
- Removes essential security controls
- Adds unnecessary tracking
- Adds spam-oriented behavior
- Makes unrelated large changes
- Copies code without proper licensing
- Violates the Code of Conduct

Submission does not guarantee that a contribution will be merged.

## Pull request checklist

Before submitting a pull request, confirm:

```text
[ ] I reviewed the existing issues and pull requests.
[ ] My change is focused on one feature or problem.
[ ] I did not include secrets or private data.
[ ] I tested the relevant Telegram behavior.
[ ] I preserved security and privacy protections.
[ ] I updated the documentation when required.
[ ] I preserved A36 Labs copyright and attribution notices.
[ ] I agree to license my contribution under Apache License 2.0.
```

## Optional local development

Local development is optional.

To test Milo locally:

```bash
git clone https://github.com/YOUR_USERNAME/a36-milo.git
cd a36-milo
npm install
```

Create a local secrets file:

```bash
cp .dev.vars.example .dev.vars
```

Add development credentials to `.dev.vars`.

Never commit `.dev.vars`.

Start the Worker locally:

```bash
npm run dev
```

Validate the Worker configuration:

```bash
npm run check
```

Use development Telegram, Gemini and Cloudflare resources rather than production credentials.

## Copyright and licensing

The original A36 Milo project is:

```text
Copyright 2026 A36 Labs
```

A36 Milo is licensed under the Apache License, Version 2.0.

By submitting a contribution, you agree that your contribution may be distributed under the Apache License 2.0 used by this repository.

Contributors retain copyright in their original contributions while licensing those contributions under Apache License 2.0.

Do not remove or alter:

- The `LICENSE` file
- The `NOTICE` file
- A36 Labs copyright notices
- Original creator attribution
- Existing third-party attribution notices

## Original creator

A36 Milo was originally built by:

**Laksh Dilliwal**  
https://x.com/LakshDilliwal

## Code of Conduct

All contributors must follow `CODE_OF_CONDUCT.md`.

Be respectful, constructive and welcoming when communicating through issues, discussions and pull requests.

Harassment, discrimination, personal attacks, spam and abusive behavior are not accepted.

## Questions

For general project discussions, open a GitHub issue or use the A36 Labs community channels.

For security concerns, follow `SECURITY.md` and do not create a public issue.

## Community

- A36 Labs: https://a36labs.com
- GitHub: https://github.com/A36Labs
- X: https://x.com/A36Labs
- Telegram: https://t.me/A36Global
- Discord: https://discord.gg/8rzpt4tCqE

Thank you for helping improve A36 Milo.

**Build. Connect. Launch.**
