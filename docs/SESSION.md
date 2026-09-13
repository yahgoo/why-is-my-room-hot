# Session snapshot — 12 Sep 2026

## Running locally

```bash
cd why-is-my-room-hot
npm install
npm run dev
```

- Web: http://127.0.0.1:5175
- API: http://127.0.0.1:3000
- Health: http://127.0.0.1:3000/api/clickhouse/health

## What works

| Integration | Status |
|-------------|--------|
| App (in-memory demo rooms) | Running |
| ClickHouse Cloud (Option B) | Connected — `hotroom` database + `apartment_events` table created |
| Airwallex sandbox keys | Configured in local `.env` |
| OpenAI live agent | Not configured (`OPENAI_API_KEY` empty — test fixture mode) |
| Airwallex webhooks | Placeholder secret — needs public HTTPS URL + real webhook secret |

## ClickHouse Cloud

- Host: `ac6l4ci6se.ap-southeast-1.aws.clickhouse.cloud:8443`
- Database: `hotroom`
- User: `default`
- Credentials: local `.env` only (not committed)

Verify:

```bash
curl http://127.0.0.1:3000/api/clickhouse/health
# {"configured":true,"status":"available"}
```

## Airwallex sandbox

- API base: `https://api-demo.airwallex.com/api/v1`
- Payment link smoke test worked earlier
- Webhook URL when deployed: `https://YOUR-PUBLIC-HTTPS-URL/api/webhooks/airwallex`

## Still to do

1. Set `OPENAI_API_KEY` for live agent mode
2. Configure Airwallex webhook + `AIRWALLEX_WEBHOOK_SECRET`
3. Optional: `DATABASE_URL` for persistent PostgreSQL instead of in-memory demo

## Secrets

All secrets live in `.env` (gitignored). Copy from `.env.example` and fill locally.
