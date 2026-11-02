# tickerwire-uptime

Keeps the Tickerwire services awake by requesting them every 5 minutes from GitHub Actions
(`.github/workflows/ping.yml`):

- https://awire.pplx.app/port/5000/api/tape (news server — it only polls feeds and sends alerts while awake)
- https://awire.pplx.app/
- https://tickerwire-verifier.onrender.com/health (Apple purchase verifier)

GitHub runs scheduled workflows on a best-effort basis, so intervals can occasionally be longer than 5 minutes.
GitHub also disables schedules after 60 days without repository activity; the workflow commits
`last-active.txt` once a week (Monday 00:00 UTC run, and on every manual run) to prevent that.

Run it manually from the Actions tab → ping → Run workflow. No secrets are used.
