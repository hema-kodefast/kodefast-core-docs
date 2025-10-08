## DevOps Runbook — cache-manager

### Overview

- Deno + Hono service providing namespaced JSON cache over HTTP
- Storage: Deno KV (managed key-value store)
- Auth: Admin endpoints protected by `x-admin-token`; client endpoints use `x-api-key` and Deno KV lookup
- Compression: Brotli for cached JSON values

### Dependencies and Runtime

- Deno runtime (latest stable with `--unstable-kv` support)
- Hono 4.x
- zod for configuration and request validation
- Node compat for Buffer and zlib (via `node:` imports)

#### Deno tasks

- Start: `deno task start`
  - Expands to: `deno run --env-file --allow-net --allow-read --allow-env --allow-scripts --unstable-kv --watch main.ts`

### Configuration and Environment

Defined in `env.ts` using zod validation. Required variables:

- APP_ENV: one of `development|production|staging` (default: development)
- APP_NAME
- API_VERSION (e.g., `/api/v1`)
- LOG_LEVEL: one of `fatal|error|warn|info|debug|trace`
- PORT: 1024..65535 (default: 3000)
- ADMIN_TOKEN
- MAX_TTL: ms, 1,000..2,592,000,000 (30 days) (default: 30 days)
- DEF_TTL: ms, 1,000..86,400,000 (24 hours) (default: 24 hours)
- MAX_VALUE_SIZE: bytes, 1,024..1,048,576 (default: 1 MB)

Load via `.env` file (deno `--env-file`) or environment.

### Storage and Bindings

- Deno KV is opened per request in `factory.ts` and stored as `c.var.kv`
- Client credentials (namespace and api_key) are stored under key tuple `['clients', api_key]`
- Cached JSON is stored under `[client.namespace, key]` with TTL

### Security

- Admin endpoints require header `x-admin-token: <ADMIN_TOKEN>`
- Client endpoints require header `x-api-key: <client_api_key>`; server loads client from Deno KV
- Do not commit `.env` with secrets; inject via deploy environment

### Local Development

```bash
deno task start
# Service listens on PORT; base path is API_VERSION
```

### API Routes (high level)

- Health: `GET /` → 200, Service Up
- Base path: `${API_VERSION}`
- Clients (admin)
  - `POST ${API_VERSION}/clients` create client; returns `api_key` and namespace
  - `GET ${API_VERSION}/clients` fetch client by `x-api-key` header
- Cache (client)
  - `POST ${API_VERSION}/cache` body: `{ key, value(json-string), ttl(seconds)? }` → cache
  - `GET ${API_VERSION}/cache/:key` → returns JSON
  - `DELETE ${API_VERSION}/cache/:key` → remove key

### Deployment

#### Deno Deploy (recommended, deno.json deploy config present)

- Ensure `deno.json` has deploy config:
  - project: `05f3b2c7-e01d-494a-bc27-de56636b27fa`
  - entrypoint: `main.ts`
- Steps:
  1. Create a Deno Deploy project or use the configured `project` ID
  2. Set environment variables in Deno Deploy dashboard: APP_NAME, API_VERSION, LOG_LEVEL, PORT (optional), ADMIN_TOKEN, TTL limits
  3. Deploy from repo or via CLI (`deployctl`) pointing to `main.ts`
  4. Configure custom domains and routes in Deno Deploy as needed

#### Alternative: Self-host (Docker or bare metal)

- Build an image with Deno installed, run the service with required permissions:

```bash
deno run --env-file --allow-net --allow-read --allow-env --allow-scripts --unstable-kv main.ts
```

- Expose PORT; put behind reverse proxy (NGINX/Caddy)

### Provisioning and Operations

- Bootstrap Admin Token: set `ADMIN_TOKEN` in env
- Create client credentials (admin endpoint) to provision `x-api-key` entries into Deno KV
- KV backup: Deno KV is managed; plan periodic export if needed (custom job reading keys/prefixes)
- Observability: add logs via `hono-pino` (imported), set `LOG_LEVEL`

### Limits and Tunables

- TTL: default `DEF_TTL` and per-request `ttl` (seconds) converted to ms
- Value size: `MAX_VALUE_SIZE` enforced at validation (ensure handlers/validators respect it)
- Max TTL: `MAX_TTL` upper bound (enforce via validation schema)

### Vendor Lock-in and Alternatives

- Deno KV
  - Alternatives: Redis (Upstash/ElastiCache), Cloudflare KV/D1, SQLite + LRU layer
  - Mitigation: isolate storage access via `c.var.kv` usage and small helper layer; design migration scripts to export/import keys
- Deno Deploy
  - Alternatives: Fly.io, Railway, Cloudflare Workers (with minor porting), Node runtime
  - Mitigation: Hono framework is portable; avoid Deno-specific APIs outside KV

### Runbooks

- Rollback: redeploy previous commit in Deno Deploy dashboard or revert and redeploy via CI
- Health check: `GET /` returns 200 and message
- Rotate Admin Token: update env and restart/redeploy
