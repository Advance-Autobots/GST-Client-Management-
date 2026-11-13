# CA Compliance Reminder Bot

**Version 1** — a web app for a Chartered Accountant (CA) firm that tracks client
compliance deadlines and uses bots (RPA) to send reminders automatically.

## 🔗 Try it

**Live app:** https://gstclientmanagement.streamlit.app

* Login password: ask the project owner (shared privately, not published here).
* Data resets whenever the free host restarts or sleeps. After logging in, add a client
  or import the sample CSV (Clients → *Import Clients from CSV* → *Download Sample CSV*).
* Step-by-step test checklist: **[TESTING.md](TESTING.md)**

> The source code is maintained privately. This repository holds the project
> documentation only.

---

## What it does

Missing a GST, TDS, PF/ESI or advance-tax due date means penalties for the client.
This app keeps every client's deadlines in one place and reminds people automatically.

### Features

| Area | What you get |
|---|---|
| **Client management** | Add / edit / delete clients with GSTIN and PAN validation, duplicate checks, and a CSV bulk import with a downloadable error report |
| **Auto deadlines** | Pick the compliances that apply to a client (GSTR-1, GSTR-3B monthly or QRMP, GSTR-7/8/9, TDS, PF/ESI, advance tax); deadlines for the next 12 months are generated automatically |
| **Editable due dates** | Government extensions are common, so templates and individual deadlines can be edited in the app |
| **Dashboard** | Overdue / Due in 7 Days / Upcoming / Filed This Month cards, red-amber-green status table, filters, one-click *Mark as Filed* |
| **Reminder bot** | Emails clients at 7, 3, 1 and 0 days before the due date and once when overdue; never sends the same reminder twice; daily digest to the firm's staff |
| **Telegram** | Optional reminders on Telegram. Each client connects with **one tap** on a personal link — no chat ids to type |
| **WhatsApp** | One-click chat link with a ready-made message for each deadline |
| **GST watcher (RPA)** | A browser bot reads the public GST portal news page and flags headlines about extensions or due-date changes |
| **Assisted status check (RPA)** | Opens a visible browser, pre-fills the GSTIN, the **human** solves the captcha, and a proof screenshot is saved |
| **Scheduler** | Runs the reminder bot every day at 09:00 IST and the watcher at 09:30 IST |
| **Reports** | Filed-vs-pending chart by month and an Excel export (Deadlines, Clients, Reminder Log) |
| **Logs** | Every message sent and every bot run is recorded and filterable |
| **Safe mode** | `DRY_RUN` logs what would be sent without sending anything |

**Design principle:** the bots never automate GST portal login, captcha or OTP.

### Built with (all free)
Python · Streamlit · SQLAlchemy + SQLite · APScheduler · Gmail SMTP · Telegram Bot API ·
Playwright (Chromium) · pandas · openpyxl

---
<!-- ![Dashboard](images/dashboard.png) -->

## Known limitations (Version 1)

* One shared admin password; no separate user accounts or roles.
* On the free cloud host the database is temporary, and the daily scheduler and the
  assisted status check are not available there (they run on the owner's PC).
* Standard due dates are seeded for convenience — always confirm against current
  government notifications. The app does not give legal or tax advice.
* The GST watcher depends on the portal's page layout and may need an update if it changes.

## Documents

| File | Contents |
|---|---|
| [TESTING.md](TESTING.md) | Tester checklist (19 tests) and how to report a bug |
| [CHANGELOG.md](CHANGELOG.md) | What changed in each version |
| [ROADMAP.md](ROADMAP.md) | Planned features for future versions |

## Reporting problems

Open an **Issue** in this repository and include: the page name, what you clicked,
what you expected, what happened, and a screenshot or the red error text.

---

*RPA college project. Zero-cost, open-source libraries only.*
