## DevOps Runbook — notify.kodefast.com

### Overview

- Cloudflare Worker (Hono) exposing admin/service APIs for email and SMS notifications
- Email via SendGrid (internal account) or customer SMTP (external)
- SMS via Twilio (prod and sandbox)
- Supabase (Postgres) for persistence; Cloudflare KV (`NF_CLIENTS`) for client auth mapping

### Dependencies and Accounts

#### Runtime and tooling

- Node.js 18+ and npm
- Wrangler CLI 3.x (Cloudflare)
- TypeScript 5.x

#### NPM libraries (runtime)

- hono
- inversify, reflect-metadata
- @supabase/supabase-js

#### Cloud and SaaS accounts

- Cloudflare
  - Workers, KV namespaces, DNS/Zone for `notify-*.kodefast.com`
  - API token permissions: Workers Scripts (Edit), Workers KV (Edit), Account Read
- SendGrid (email)
  - API key(s) for mail send, templates, domain whitelabel, and (optionally) email validation
- Twilio (sms)
  - Account SID(s), Auth Token(s), From number(s) for prod and sandbox
- Supabase (Postgres)
  - Project URL and Service Role Key

### Vendor lock-in alternatives and mitigations

- Cloudflare Workers/KV
  - Alternatives: AWS Lambda + API Gateway, Vercel/Netlify Edge, Fastly Compute@Edge; KV → Upstash/Redis/Vercel KV
  - Mitigation: Hono is portable; keep storage behind repository interfaces; minimal KV usage (auth cache)
- SendGrid
  - Alternatives: AWS SES, Mailgun, Postmark, SMTP relays
  - Mitigation: Email service abstracted via `IEmailService` and `ISMTPEmailService`
- Twilio
  - Alternatives: MessageBird, Vonage (Nexmo), AWS SNS SMS
  - Mitigation: SMS service behind `ISMSService`
- Supabase (Postgres)
  - Alternatives: Neon, RDS/Aurora, Railway, Fly.io, PlanetScale (MySQL)
  - Mitigation: SQL kept standard; DB access encapsulated in `SupabaseDBCoreService`

### Configuration and secrets

#### Required environment variables (per env)

- ADMIN_TOKEN
- SUPABASE_URL, SUPABASE_KEY
- SG_BASE_URL (e.g., `https://api.sendgrid.com/v3`)
- SG_KEY (SendGrid API key for email send/templates)
- SG_EMAIL_VAL_KEY (SendGrid Email Validation key)
- TWL_BASE_URL (e.g., `https://api.twilio.com/2010-04-01`)
- TWL_ACCOUNT_SID, TWL_AUTH_TOKEN, TWL_FROM_NUMBER
- TWL_TEST_ACCOUNT_SID, TWL_TEST_AUTH_TOKEN, TWL_TEST_FROM_NUMBER (sandbox)
- NOTIFY_SMTP_BASE_URL (if SMTP enabled)
- NOTIFY_SMTP_API_KEY (if SMTP enabled)
- ENCRYPT_KEY (AES-GCM key for encryption endpoints)
- Optional: WEBHOOK_URL (if used by downstreams)

#### Cloudflare bindings

- KV Namespace: `NF_CLIENTS` (client API key → client details JSON)

#### Files and notes

- `wrangler.toml`
  - `[env.dev]` has `vars` for base URLs, `kv_namespaces` binding `NF_CLIENTS`, and route `notify-dev.kodefast.com`
  - `[env.production]` has `vars` for base URLs, `kv_namespaces` and route `notify.kodefast.com`
  - Add `[env.staging]` if needed (see example below)
- `package.json` scripts
  - `start` (dev): `wrangler dev --env dev --remote true`
  - deploy scripts: `deploy:dev`, `deploy:staging`, `deploy:prod`

#### Security

- Do NOT commit secrets. Use `wrangler secret` for all environments.
- If `.dev.vars` exists locally, rotate any leaked credentials and purge from VCS history. Prefer `wrangler secret` even for dev.

### Local development

#### Install

```bash
npm install -g wrangler
npm install
```

#### Run (remote dev by default)

```bash
npm run start
```

#### Dev secrets

```bash
wrangler secret put ADMIN_TOKEN --env dev
wrangler secret put SUPABASE_URL --env dev
wrangler secret put SUPABASE_KEY --env dev
wrangler secret put SG_KEY --env dev
wrangler secret put SG_EMAIL_VAL_KEY --env dev
wrangler secret put TWL_ACCOUNT_SID --env dev
wrangler secret put TWL_AUTH_TOKEN --env dev
wrangler secret put TWL_FROM_NUMBER --env dev
wrangler secret put TWL_TEST_ACCOUNT_SID --env dev
wrangler secret put TWL_TEST_AUTH_TOKEN --env dev
wrangler secret put TWL_TEST_FROM_NUMBER --env dev
wrangler secret put NOTIFY_SMTP_API_KEY --env dev
wrangler secret put ENCRYPT_KEY --env dev
```

Note: Non-sensitive base URLs can live under `[env.<env>].vars` in `wrangler.toml`.

### Environment provisioning (dev/staging/prod)

#### Cloudflare KV

```bash
# Create KV namespace
wrangler kv:namespace create NF_CLIENTS --env dev
wrangler kv:namespace create NF_CLIENTS --env production
# For staging as needed
wrangler kv:namespace create NF_CLIENTS --env staging
```

Update the resulting `id` (and `preview_id`) in `wrangler.toml` under each env `[[env.<env>.kv_namespaces]]` block.

#### DNS/Route

- Ensure zone `kodefast.com` is managed in Cloudflare.
- Set routes per env with `custom_domain = true`.

#### Secrets

- Add all listed secrets via `wrangler secret put ... --env <env>` for each environment.

### Deployment steps

1. Prepare `wrangler.toml`

   - Ensure `[env.dev]`, `[env.production]` (and `[env.staging]` if used) have `routes`, `vars` (base URLs), and `[[env.<env>.kv_namespaces]]` binding `NF_CLIENTS`.

2. Seed KV (optional, per client onboarding)

```bash
# Map client API key → client details JSON
wrangler kv:key put --env <env> --binding NF_CLIENTS <client_api_key> '{"id":123,"email_usage_type":"internal","email_service":"sendgrid"}'
```

3. Deploy

```bash
npm run deploy:dev
npm run deploy:staging
npm run deploy:prod
```

4. Verify

```bash
curl -s https://notify-<env>.kodefast.com/status | jq
wrangler tail --env <env>
```

#### Example staging/prod env blocks (add to `wrangler.toml`)

```toml
[env.staging]
vars = { SG_BASE_URL = "https://api.sendgrid.com/v3", TWL_BASE_URL = "https://api.twilio.com/2010-04-01", NOTIFY_SMTP_BASE_URL = "https://smtp-notify-kodefast.up.railway.app" }
kv_namespaces = [
  { binding = "NF_CLIENTS", id = "<staging-kv-id>", preview_id = "<staging-preview-id>" },
]
routes = [{ pattern = "notify-staging.kodefast.com", custom_domain = true }]
workers_dev = false

[env.production]
vars = { SG_BASE_URL = "https://api.sendgrid.com/v3", TWL_BASE_URL = "https://api.twilio.com/2010-04-01", NOTIFY_SMTP_BASE_URL = "https://smtp-notify-kodefast.up.railway.app" }
kv_namespaces = [
  { binding = "NF_CLIENTS", id = "<prod-kv-id>", preview_id = "<prod-preview-id>" },
]
routes = [{ pattern = "notify.kodefast.com", custom_domain = true }]
workers_dev = true
```

### Rollback and operations

- Rollback: deploy a prior commit after checkout using `wrangler deploy --env <env>`
- Logs: `wrangler tail --env <env>`
- KV inspection: `wrangler kv:key list --env <env> --binding NF_CLIENTS`
- Access control: rotate `ADMIN_TOKEN`, SendGrid/Twilio/Supabase keys upon any suspicion of leak

### Notes

- If SMTP is selected (`email_service = 'smtp'`), domain whitelabel and SendGrid template flows are skipped; only `content` send is supported.
- Ensure `NOTIFY_SMTP_BASE_URL` and `NOTIFY_SMTP_API_KEY` are set in any env where SMTP is enabled.
- The service uses Bearer token auth with client lookup in `NF_CLIENTS`; onboarding must provision this KV entry.
