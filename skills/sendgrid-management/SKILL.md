---
name: sendgrid-management
description: |
  Use when managing SendGrid email services via CLI - sending emails, managing templates, contacts, lists,
  suppressions, domains, API keys, webhooks, and viewing stats.
  Triggers: "sendgrid send", "manage sendgrid", "sendgrid template", "sendgrid contacts", "sendgrid stats",
  "sendgrid domain", "sendgrid api key", "sendgrid webhook", "email bounces", "sendgrid suppressions",
  "verify sender", "sendgrid list", "marketing email", "transactional email".
  Provides comprehensive CLI for all SendGrid API operations without needing the dashboard.
---

# SendGrid Management

Complete CLI for managing SendGrid email services - send emails, manage templates, contacts, domains, and more.

## Quick Reference

| Task | Command |
|------|---------|
| **Send email** | `sendgrid mail send --to user@example.com --subject "Hello" --text "Body"` |
| **Send with template** | `sendgrid mail send --to user@example.com --template-id d-xxx --data '{"name":"John"}'` |
| **Send with attachment** | `sendgrid mail send ... --attachment ./report.pdf` |
| **Inline image (CID)** | `sendgrid mail send ... --html '<img src="cid:logo">' --inline ./logo.png` |
| **List templates** | `sendgrid template list` |
| **Add contact** | `sendgrid contact add --email user@example.com --first-name John` |
| **View stats** | `sendgrid stats global --days 7` |
| **List bounces** | `sendgrid suppression bounces` |
| **Create API key** | `sendgrid apikey create --name "My Key" --scopes mail.send` |

## Installation

```bash
# Option 1: Run with Deno
deno run --allow-all ~/.claude/skills/sendgrid-management/cli/mod.ts [command]

# Option 2: Compile to binary
cd ~/.claude/skills/sendgrid-management/cli && deno task compile
./dist/sendgrid --help

# Option 3: Install globally
deno install --allow-all -n sendgrid ~/.claude/skills/sendgrid-management/cli/mod.ts
```

## Authentication

```bash
# Set API key (saves to ~/.config/sendgrid/config.json)
sendgrid auth login --api-key SG.xxx

# Or use environment variable
export SENDGRID_API_KEY="SG.xxx"

# Check auth status
sendgrid auth status
```

## Command Groups

| Group | Description |
|-------|-------------|
| `auth` | Authentication and config management |
| `mail` | Send emails (transactional) |
| `template` | Manage dynamic templates |
| `contact` | Manage contacts |
| `list` | Manage contact lists |
| `segment` | Manage contact segments |
| `suppression` | View/manage bounces, blocks, spam reports |
| `sender` | Manage verified senders |
| `domain` | Domain authentication (DKIM, SPF) |
| `stats` | View email statistics |
| `webhook` | Manage event webhooks |
| `apikey` | Manage API keys |
| `validate` | Validate email addresses |

## Core Workflows

### Workflow 1: Send Transactional Email

```bash
# Simple email
sendgrid mail send \
  --to recipient@example.com \
  --from sender@example.com \
  --subject "Welcome!" \
  --html "<h1>Hello</h1><p>Welcome to our service!</p>"

# With dynamic template
sendgrid mail send \
  --to recipient@example.com \
  --from sender@example.com \
  --template-id d-f43daeeaef504760851f727007e0b5d0 \
  --data '{"name": "John", "order_id": "12345"}'

# Multiple recipients
sendgrid mail send \
  --to user1@example.com,user2@example.com \
  --from sender@example.com \
  --subject "Announcement" \
  --text "Important update..."

# Schedule for later
sendgrid mail send \
  --to recipient@example.com \
  --from sender@example.com \
  --subject "Scheduled" \
  --text "This was scheduled" \
  --send-at "2024-12-25T10:00:00Z"

# With file attachment (downloadable)
sendgrid mail send \
  --to recipient@example.com \
  --subject "Q4 report" \
  --html "<p>See attached.</p>" \
  --attachment ./report.pdf \
  --attachment ./summary.xlsx

# With inline image (CID-embedded — renders without "show images" prompt)
# CID defaults to the filename without extension; here it's "logo"
sendgrid mail send \
  --to recipient@example.com \
  --subject "Welcome" \
  --html '<p><img src="cid:logo" width="180"></p><p>Hello!</p>' \
  --inline ./logo.png

# Inline image with custom CID — append :customcid to the path
sendgrid mail send \
  --to recipient@example.com \
  --subject "Newsletter" \
  --html '<img src="cid:hero"> ... <img src="cid:footer">' \
  --inline ./header.png:hero \
  --inline ./footer-banner.png:footer
```

**Default sender**: if `--from` is omitted, the CLI uses `SENDGRID_FROM_EMAIL` env var or `fromEmail` from `~/.config/sendgrid/config.json`. Same for `--from-name` / `SENDGRID_FROM_NAME` / `fromName`.

**Auto-MIME**: `--attachment` and `--inline` infer `Content-Type` from file extension. Supported: `png`, `jpg`/`jpeg`, `gif`, `webp`, `svg`, `pdf`, `txt`, `csv`, `json`, `html`. Other types are sent without an explicit MIME (SendGrid will still accept).

**Hosted vs inline images** — pick based on goal:
- **Hosted URL** (`<img src="https://...">`): simpler templates; many clients block remote images by default until the user clicks "show images". SendGrid's own image-hosting CDN (`cdn.mcauto-images-production.sendgrid.net/...`) tends to be whitelisted in more clients than third-party CDNs.
- **Inline CID** (`--inline path` + `<img src="cid:...">`): bulletproof rendering — image arrives with the message and shows immediately. Cost: larger message size (base64 ~33% overhead).

### Workflow 2: Manage Templates

```bash
# List all templates
sendgrid template list

# Get template details
sendgrid template get <template-id>

# Create template
sendgrid template create --name "Welcome Email" --generation dynamic

# Create/update version
sendgrid template version create <template-id> \
  --name "v1" \
  --subject "Welcome {{name}}!" \
  --html-file welcome.html \
  --active
```

### Workflow 3: Contact Management

```bash
# Add single contact
sendgrid contact add \
  --email user@example.com \
  --first-name John \
  --last-name Doe \
  --list-ids abc123,def456

# Import from file
sendgrid contact import --file contacts.csv

# Search contacts
sendgrid contact search --query "email LIKE '%@example.com'"

# Export contacts
sendgrid contact export --list-id abc123 --output contacts.csv

# Get contact count
sendgrid contact count
```

### Workflow 4: List Management

```bash
# Create list
sendgrid list create --name "Newsletter Subscribers"

# List all lists
sendgrid list all

# Add contacts to list
sendgrid list add-contacts <list-id> --emails user1@example.com,user2@example.com

# Remove contacts from list
sendgrid list remove-contacts <list-id> --contact-ids id1,id2

# Delete list
sendgrid list delete <list-id>
```

### Workflow 5: Suppression Management

```bash
# View bounces
sendgrid suppression bounces [--start-time 2024-01-01] [--end-time 2024-12-31]

# View blocks
sendgrid suppression blocks

# View spam reports
sendgrid suppression spam-reports

# View unsubscribes
sendgrid suppression unsubscribes

# Delete specific bounce
sendgrid suppression delete bounce user@example.com

# Add to global unsubscribe
sendgrid suppression add unsubscribe user@example.com
```

### Workflow 6: Domain Authentication

```bash
# List authenticated domains
sendgrid domain list

# Authenticate new domain
sendgrid domain create --domain example.com

# Get DNS records to add
sendgrid domain get <domain-id>

# Validate domain (after adding DNS)
sendgrid domain validate <domain-id>

# Set as default
sendgrid domain set-default <domain-id>
```

### Workflow 7: Sender Verification

```bash
# List verified senders
sendgrid sender list

# Create sender identity
sendgrid sender create \
  --from-email noreply@example.com \
  --from-name "My Company" \
  --reply-to support@example.com

# Resend verification
sendgrid sender resend <sender-id>

# Delete sender
sendgrid sender delete <sender-id>
```

> ⚠️ **`sender create` requires a Full Access API key.** SendGrid's `POST /v3/verified_senders` endpoint ignores granular scopes — even with `sender_verification_eligible` and `whitelabel.create`/`update`/`delete` enabled, a restricted key returns `403 access forbidden`. Workarounds: (a) create senders in the SendGrid web UI at <https://app.sendgrid.com/settings/sender_auth/senders/new>, or (b) generate a temporary Full Access key, run the create, then delete the key. `sender list`/`get`/`delete`/`resend` work fine with the standard `sender_verification_eligible` read scope.

### Workflow 8: Statistics

```bash
# Global stats (last 7 days)
sendgrid stats global --days 7

# Stats by category
sendgrid stats category --categories transactional,marketing --days 30

# Stats by mailbox provider
sendgrid stats mailbox-providers --days 7

# Stats by browser
sendgrid stats browsers --days 7

# Stats by device
sendgrid stats devices --days 7
```

### Workflow 9: Webhooks

```bash
# List webhooks
sendgrid webhook list

# Create webhook
sendgrid webhook create \
  --url https://example.com/webhook \
  --events delivered,opened,clicked,bounced

# Update webhook
sendgrid webhook update <webhook-id> --enabled false

# Test webhook
sendgrid webhook test <webhook-id>

# Delete webhook
sendgrid webhook delete <webhook-id>
```

### Workflow 10: API Keys

```bash
# List API keys
sendgrid apikey list

# Create API key
sendgrid apikey create \
  --name "Production API" \
  --scopes mail.send,templates.read

# Create full access key
sendgrid apikey create --name "Admin Key" --full-access

# Update key name
sendgrid apikey update <key-id> --name "New Name"

# Delete key
sendgrid apikey delete <key-id>
```

## JSON Output

All commands support `--json` for machine-readable output:

```bash
sendgrid template list --json | jq '.[].id'
sendgrid stats global --days 7 --json > stats.json
```

## Environment Variables

| Variable | Description |
|----------|-------------|
| `SENDGRID_API_KEY` | API key (required) |
| `SENDGRID_FROM_EMAIL` | Default from email |
| `SENDGRID_FROM_NAME` | Default from name |

## API Coverage

| Category | Endpoints | Status |
|----------|-----------|--------|
| Mail Send | send, schedule, batch | Complete |
| Templates | CRUD, versions | Complete |
| Contacts | add, import, search, export | Complete |
| Lists | CRUD, add/remove contacts | Complete |
| Segments | list, get | Partial |
| Suppressions | bounces, blocks, spam, unsubs | Complete |
| Senders | CRUD, verify | Complete |
| Domain Auth | CRUD, validate | Complete |
| Stats | global, category, geo, device | Complete |
| Webhooks | CRUD, test | Complete |
| API Keys | CRUD | Complete |
| Validation | single email | Complete |

## Common Issues

| Error | Solution |
|-------|----------|
| `401 Unauthorized` | Check API key is valid and has required scopes |
| `403 Forbidden` on `sender create` | Endpoint requires a **Full Access** API key — granular scopes are insufficient. See Workflow 7. |
| `403 Forbidden` (other) | API key lacks permission for this action — verify with `curl -H "Authorization: Bearer $KEY" https://api.sendgrid.com/v3/scopes` |
| `429 Rate Limited` | Too many requests; wait and retry |
| `400 Bad Request` | Check request parameters |
| `400 categories array... must have at least one category` | You're on an outdated CLI binary. Reinstall (see "Recent Fixes" below). |

## Recent Fixes

Reinstall the CLI to pick up these fixes (`deno install --global --config ~/.claude/skills/sendgrid-management/cli/deno.json --allow-all -n sendgrid -f ~/.claude/skills/sendgrid-management/cli/mod.ts`):

- **`mail send` empty-array bug**: previously sent `categories: []`, `cc: []`, `bcc: []` when those flags weren't passed, causing SendGrid to reject the request with `400 categories array must have at least one category` (and similar for cc/bcc). Now omitted when empty.
- **`--inline` flag added**: embed images/files with `Content-Disposition: inline` and a `Content-ID` so HTML can reference them via `<img src="cid:...">`. Custom CIDs supported as `--inline path:custom-cid`.
- **Auto-MIME inference**: `--attachment` and `--inline` now derive `Content-Type` from file extension (`png`, `jpg`/`jpeg`, `gif`, `webp`, `svg`, `pdf`, `txt`, `csv`, `json`, `html`). Was missing before — most clients still rendered, but inline PNGs were unreliable.
- **Base64 chunked encoding**: the previous `btoa(String.fromCharCode(...bytes))` implementation hit a stack overflow on attachments larger than ~64KB. Now encodes in 32KB chunks.

## Resources

- [references/api-endpoints.md](references/api-endpoints.md) - Full API endpoint reference
- [references/scopes.md](references/scopes.md) - API key scopes reference
- **Official Docs**: https://www.twilio.com/docs/sendgrid/api-reference
