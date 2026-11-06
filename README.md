# Taylor Bank keep-awake

Pings https://taylor-envelopes.onrender.com/healthz so the free Render service
does not spin down during **7:00 AM – 7:00 PM America/Denver, Monday–Saturday**.

## Status (verified 2026-11-06)

GitHub Actions `workflow_dispatch` works. GitHub Actions `schedule` does **not**
fire on this repo/account — zero `schedule` runs after 4+ hours and multiple
re-registers (UTC dual cron, timezone cron, plain UTC offset cron, linked
`justinctaylor77` commit author, disable/enable, plus a separate canary workflow).
Do **not** rely on `schedule` alone until a real `schedule` run appears in Actions.

Current compensating keep-awake: a Grok Bot / external HTTP cron (or temporary
box-side loop) must ping `/healthz` during bank hours. Manual "Run workflow"
still works.

## Notes

- `/healthz` returns static `ok` and does **not** touch Neon Postgres.
- App pages that query the ledger may still take ~0.5s if Neon compute was scaled
  to zero; that is not the Render "Application loading" screen.
- PWA `start_url` is `/` on `https://taylor-envelopes.onrender.com`.
- Public repo on purpose so Actions minutes stay free.

Owned by Justin Taylor / G (PMO). Not the Taylor Bank app source.
