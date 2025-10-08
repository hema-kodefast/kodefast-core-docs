## DevOps Runbook — queue-kodefast-com

### Overview

- Cloudflare Worker (Hono) exposing admin/service APIs for queue/topic management
- AWS SNS for messaging; Cloudflare D1 for metadata (clients, topics, endpoints)
- Drizzle ORM for schema/migrations; Inversify for dependency injection

### Dependencies and Accounts

#### Runtime and tooling

- Node.js 18+ and npm
- Wrangler CLI 3.x (Cloudflare)
- Drizzle Kit

#### NPM libraries (production)

- @aws-sdk/client-sns, @aws-sdk/client-sqs (SNS is used; SQS ready)
- drizzle-orm
- hono
- inversify, reflect-metadata
- nanoid
- openai (optional; sample code is commented)

#### Cloud accounts and access

- Cloudflare
  - Services: Workers, D1, DNS/Zone for `queue-*.kodefast.com`
  - API token permissions: Workers Scripts (Edit), D1 (Edit), Account Read
- AWS
  - IAM user/role for SNS with minimum permissions:
    - sns:CreateTopic, sns:DeleteTopic, sns:Publish, sns:Subscribe, sns:ConfirmSubscription, sns:Unsubscribe
    - sns:ListTopics, sns:ListSubscriptionsByTopic, sns:GetTopicAttributes, sns:SetTopicAttributes
  - Set region according to your SNS usage
- OpenAI (optional)
  - API key only if you enable the sample code

### Vendor lock-in alternatives and mitigations

- Cloudflare Workers
  - Alternatives: AWS Lambda@Edge/API Gateway, Vercel Edge Functions, Netlify Edge, Fastly Compute@Edge
  - Mitigation: Hono is portable; keep request handlers framework-agnostic
- Cloudflare D1 (SQLite)
  - Alternatives: Turso/libSQL (SQLite), Neon/Cloud SQL/Postgres, PlanetScale/MySQL
  - Mitigation: Drizzle ORM supports multiple drivers; repositories already abstract data access
- AWS SNS
  - Alternatives: Google Pub/Sub, Azure Service Bus, Apache Kafka (MSK/Confluent/Redpanda), NATS, RabbitMQ, or SQS-only
  - Mitigation: Keep a messaging service interface; SNS calls live behind service classes

### Configuration and secrets

#### Required environment variables (per env)

- AWS_ACCESS_KEY_ID
- AWS_SECRET_ACCESS_KEY
- ADMIN_TOKEN (for `/admin/*`)
- OPENAI_API_KEY (optional)

#### Cloudflare bindings

- D1 database binding name: `DB`

#### Files and notes

- `wrangler.toml` contains `[env.dev]` with route `queue-dev.kodefast.com` and `[[env.dev.d1_databases]]` binding `DB`.
- Add `[env.staging]` and `[env.production]` blocks before using `deploy:staging` and `deploy:prod` scripts.
- `drizzle.config.ts` uses `dbName: "queue_service"`; ensure it aligns with each environment or manage via env-specific configuration.

#### Security

- Do NOT commit secrets. Use `wrangler secret` for all environments.
- Current `.dev.vars` contains credentials; rotate immediately and remove from history. Prefer `wrangler secret` even for dev.

### Local development

#### Install

```bash
npm install -g wrangler
npm install
```

#### Run (remote dev by default)

```bash
npm run dev
```

#### Local DB and migrations (D1)

```bash
# Generate migrations from Drizzle schema
npm run migrations:generate

# Apply migrations to local D1
npm run migrations:apply:local

# List local migrations
npm run migrations:list:local
```

#### Secrets for local testing

- For remote dev environment secrets:

```bash
wrangler secret put AWS_ACCESS_KEY_ID --env dev
wrangler secret put AWS_SECRET_ACCESS_KEY --env dev
wrangler secret put ADMIN_TOKEN --env dev
wrangler secret put OPENAI_API_KEY --env dev
```

- If you use `--local`, Wrangler can read `.dev.vars`, but prefer `wrangler secret` to avoid committing secrets.

### Environment provisioning (dev/staging/prod)

#### Cloudflare D1

```bash
# Create a D1 database
wrangler d1 create <db_name>
```

Bind in `wrangler.toml` under the matching env:

```toml
[[env.<env>.d1_databases]]
binding = "DB"
database_name = "<db_name>"
database_id = "<db_id>"
```

#### DNS/Route

- Ensure zone `kodefast.com` is managed in Cloudflare.
- Add env routes with custom domains, e.g. `{ pattern = "queue-<env>.kodefast.com", custom_domain = true }`.

#### Secrets

- Add AWS/OpenAI/Admin token via `wrangler secret put ... --env <env>`.

#### IAM

- Attach least-privilege SNS policy as listed above to the deploy runtime principal.

### Deployment steps

1. Prepare `wrangler.toml`

   - Ensure `[env.dev]`, `[env.staging]`, `[env.production]` blocks exist with `routes` and `[[env.<env>.d1_databases]]` binding `DB`.

2. Run migrations for the target env

```bash
# list/apply for dev (swap dev → staging/production as needed)
npm run migrations:list:dev
npm run migrations:apply:dev
```

3. Deploy

```bash
# Dev / Staging / Prod
npm run deploy:dev
npm run deploy:staging
npm run deploy:prod
```

4. Verify

```bash
# Health endpoint
curl -s https://queue-<env>.kodefast.com/ | jq

# Tail logs
wrangler tail --env <env>
```

#### Example env blocks (add to `wrangler.toml`)

```toml
[env.staging]
routes = [
	{ pattern = "queue-staging.kodefast.com", custom_domain = true }
]
workers_dev = false

[[env.staging.d1_databases]]
binding = "DB"
database_name = "queue_service_staging"
database_id = "<staging-d1-id>"

[env.production]
routes = [
	{ pattern = "queue.kodefast.com", custom_domain = true }
]
workers_dev = false

[[env.production.d1_databases]]
binding = "DB"
database_name = "queue_service_prod"
database_id = "<prod-d1-id>"
```

### Rollback and operations

- Rollback: deploy a prior commit after checkout using `wrangler deploy --env <env> --minify src/index.ts`.
- Logs: `wrangler tail --env <env>`.
- DB admin: `wrangler d1 execute <db_name> --command "SELECT 1"` or manage via migrations.
- Access control: Rotate `ADMIN_TOKEN` and AWS keys upon any suspicion of leak.

### Notes

- The OpenAI integration in `src/index.ts` is commented out; omit `OPENAI_API_KEY` unless enabling it.
- Align `drizzle.config.ts` database naming with each env to avoid migration drift.
