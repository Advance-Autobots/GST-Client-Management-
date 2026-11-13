# Roadmap — planned for future versions

These are **not** in v1.0.0. Order is a suggestion, not a commitment.

## v1.1 — Hosting & reliability
- Persistent hosted database (PostgreSQL via `DATABASE_URL`) so data survives restarts on cloud hosting.
- Docker image + `docker-compose` (app + scheduler) for easy VPS / office-server deployment.
- Scheduler runnable as a GitHub Actions cron / hosted worker.
- Automatic database backup and restore (Excel/JSON).
- Auto-load demo data option for testers.

## v1.2 — Users & security
- Multiple staff accounts with hashed passwords and roles (admin / staff / read-only).
- Audit trail: who changed which due date or status, and when.
- Optional two-factor login.

## v1.3 — Smarter reminders
- Configurable reminder days and message templates per compliance and per client (editable email / Telegram text).
- Repeat overdue reminders every N days (v1 sends one).
- Client-facing document checklist and "documents received" tracking.
- Reminders in regional languages.
- Direct WhatsApp Business API / SMS channel (v1 has click-to-chat links only).

## v1.4 — More automation (RPA)
- Auto-suggest updated due dates when the watcher finds an extension (one-click "apply to all affected deadlines").
- Watch additional public sources (CBIC, Income Tax e-filing news, EPFO/ESIC notices).
- Bulk assisted status checks queue (one captcha at a time, proofs saved per client).
- Bot health alerts to staff by email / Telegram when a run fails.

## v1.5 — Practice management
- Client portal / read-only share link for clients to see their own status.
- Fee, invoice and billing tracking per client.
- Document upload and storage per deadline.
- Dashboards by staff member / workload.
- More compliances: ROC / MCA filings, ITR, audit dates, professional tax.
- Excel / Tally import of the client master.

## Ideas under consideration
- Mobile-friendly layout and installable PWA.
- Calendar (.ics / Google Calendar) sync.
- Penalty / interest estimator for late filing.
- Multi-firm (multi-tenant) support.
