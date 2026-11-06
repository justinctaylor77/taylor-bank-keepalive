# Taylor Bank keep-awake

GitHub Actions pings https://taylor-envelopes.onrender.com/healthz every 10 minutes
during **7:00 AM – 7:00 PM America/Denver, Monday–Saturday**, so the free Render
service does not spin down from idle.

- First ping of the day is **6:50 AM** Mountain so the app is warm by 7:00 AM.
- Last ping is **6:50 PM** Mountain (keeps the instance up through 7:00 PM).
- Public repo on purpose: Actions minutes are free; a private repo would burn most of
  the 2,000 free Linux minutes/month just on this schedule.

Owned by Justin Taylor / G (PMO). Not the Taylor Bank app source.
