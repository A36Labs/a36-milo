# Security Policy

Security is important to A36 Milo and the communities that use it.

A36 Milo processes Telegram messages, administrator commands, AI requests and temporary conversation context. Security issues involving tokens, webhooks, access controls, stored context or community permissions should be reported privately.

## Supported versions

Security updates are provided for the latest version of A36 Milo available on the `main` branch.

| Version | Supported |
|---|---|
| Latest `main` branch | Yes |
| Latest published release | Yes |
| Older releases and copies | No |
| Modified third-party deployments | Best effort |

Community operators are encouraged to keep their deployment updated with the latest reviewed version.

## Reporting a vulnerability

Do not report security vulnerabilities through:

- Public GitHub issues
- Public pull requests
- Telegram community chats
- Discord public channels
- Social media posts

Please report vulnerabilities privately using one of the following methods.

### GitHub private vulnerability reporting

Use GitHub’s **Report a vulnerability** option in the repository’s Security section when it is available.

Repository:

https://github.com/A36Labs/a36-milo

### Email

Send the report to:

```text
hello@a36labs.com
```

Use the subject:

```text
[SECURITY] A36 Milo vulnerability report
```

## Information to include

Please include as much of the following information as possible:

- A clear description of the vulnerability
- The affected file, function or endpoint
- Steps to reproduce the issue
- Expected behavior
- Actual behavior
- Potential security impact
- A proof of concept, when safe
- Suggested remediation, when available
- Whether the vulnerability has been publicly disclosed
- Your preferred name for acknowledgment

Remove all real credentials and personal information from screenshots, logs and examples.

## Sensitive information

Never include real values for:

```text
TELEGRAM_BOT_TOKEN
TELEGRAM_WEBHOOK_SECRET
GEMINI_API_KEY
CLOUDFLARE_API_TOKEN
CLOUDFLARE_ACCOUNT_ID
Production KV namespace IDs
Private Telegram user IDs
Private Telegram group IDs
Member messages or conversation history
```

Replace sensitive values with placeholders.

Example:

```text
TELEGRAM_BOT_TOKEN="[REDACTED]"
```

## Security areas

Reports may include vulnerabilities involving:

- Telegram webhook authentication
- Telegram bot tokens
- Gemini API credentials
- Cloudflare API credentials
- Administrator authentication
- Administrator-only commands
- Approved-community restrictions
- Unauthorized group access
- Unauthorized private-message access
- Webhook replay or duplicate processing
- Cloudflare Workers KV data
- Conversation context exposure
- Prompt injection
- Knowledge manipulation
- Secret leakage in logs
- Message spoofing
- Command injection
- Cross-community data exposure
- Excessive AI usage or quota abuse
- Unsafe external links
- Dependency vulnerabilities
- Deployment configuration

## Response process

After receiving a valid report, A36 Labs will aim to:

1. Acknowledge the report.
2. Review and reproduce the issue.
3. Assess its severity and impact.
4. Develop and test a fix.
5. Coordinate disclosure with the reporter.
6. Publish an update or advisory when appropriate.

Response and remediation times depend on the complexity and severity of the issue.

Submission of a report does not guarantee a particular response time, reward or bounty.

## Coordinated disclosure

Please allow A36 Labs reasonable time to investigate and fix a vulnerability before publishing technical details.

Do not:

- Access data belonging to other users
- Modify or delete production data
- Disrupt the production bot or community
- Perform denial-of-service testing
- Send spam or automated abuse
- Use social engineering
- Expose credentials or member data
- Publicly disclose an unresolved vulnerability

Testing should use your own deployment, test bot, test group and development KV namespace whenever possible.

## Safe testing

Security researchers should:

- Test only systems they own or are authorized to test
- Use development credentials
- Use a separate Telegram test bot
- Use a separate Telegram test group
- Use a separate Cloudflare Worker
- Use a separate KV namespace
- Limit requests to avoid service disruption
- Stop immediately if private data is encountered
- Delete any accidentally collected private information

Do not test experimental changes against the production A36 Labs community without written authorization.

## Deployment security

Community operators deploying A36 Milo should:

- Store credentials as Cloudflare encrypted secrets
- Never place credentials inside `worker.js`
- Never commit `.dev.vars`
- Keep webhook-secret validation enabled
- Keep duplicate-update protection enabled
- Keep administrator checks enabled
- Keep the approved-community allow-list enabled
- Use separate development and production resources
- Regularly rotate exposed credentials
- Review logs before sharing them publicly
- Keep Cloudflare and Telegram permissions minimal
- Review community privacy requirements

## Exposed credentials

When a token or API key is exposed:

1. Revoke or rotate it immediately.
2. Remove it from the current repository content.
3. Remove it from Git history where necessary.
4. Update the corresponding Cloudflare secret.
5. Redeploy the Worker.
6. Review logs and usage for unauthorized activity.
7. Verify the Telegram webhook again.
8. Do not continue using the compromised credential.

Deleting a secret from the latest commit alone may not remove it from Git history.

## Security updates

Security fixes may be released through:

- Commits to the `main` branch
- GitHub releases
- Repository security advisories
- Updates to the project documentation

Operators are responsible for applying updates to their own deployments.

## Third-party services

A36 Milo uses third-party infrastructure and APIs, including:

- Cloudflare Workers
- Cloudflare Workers KV
- Telegram Bot API
- Google Gemini API
- GitHub

Security issues affecting those services should also be reviewed against the relevant provider’s official security guidance.

A36 Labs cannot guarantee the security, availability or behavior of third-party services.

## Scope

This security policy applies to the original source code published at:

https://github.com/A36Labs/a36-milo

A36 Labs is not responsible for vulnerabilities introduced by unofficial forks, modified copies, third-party deployments or incorrectly configured infrastructure.

## Recognition

A36 Labs may acknowledge researchers who responsibly disclose valid vulnerabilities, subject to their consent.

The project currently does not operate a paid bug-bounty program.

## Contact

**A36 Labs**

Website: https://a36labs.com  
Email: hello@a36labs.com  
GitHub: https://github.com/A36Labs  
X: https://x.com/A36Labs

Original project creator:

**Laksh Dilliwal**  
https://x.com/LakshDilliwal

---

Copyright 2026 A36 Labs
