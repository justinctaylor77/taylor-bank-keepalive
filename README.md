# Taylor Bank keep-awake

GitHub Actions pings https://taylor-envelopes.onrender.com/healthz about every 10 minutes
during **7:00 AM – 7:00 PM America/Denver, Monday–Saturday**, so the free Render
service does not spin down from idle.

- First ping of the day is around **6:07–6:57 AM** Mountain so the app is warm by 7:00 AM.
- Last ping is around **6:57 PM** Mountain (keeps the instance up through 7:00 PM).
- Cron uses `timezone: America/Denver` and minutes `7,17,27,37,47,57` (offset from :00) per GitHub docs to reduce schedule drops under load.
- Public repo on purpose: Actions minutes are free; a private repo would burn most of
  the 2,000 free Linux minutes/month just on this schedule.
- Note: GitHub `schedule` is best-effort (can delay or drop). `/healthz` is a static `ok`
  and does **not** wake Neon Postgres; app pages that hit the DB may still take ~0.5s
  if Neon compute was scaled to zero.

Owned by Justin Taylor / G (PMO). Not the Taylor Bank app source.
