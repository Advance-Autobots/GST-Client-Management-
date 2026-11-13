# Changelog

## v1.0.1 — 2026-11-13

### Added
- **One-tap Telegram connection.** Each client gets a personal, signed link
  (`https://t.me/<bot>?start=<code>`). The client taps it and presses **Start**; the app
  saves their chat id automatically and the bot replies "Connected". No bot searching and
  no typing of chat ids. The link can be sent on WhatsApp from the Clients page, and new
  connections are picked up on every reminder run or via **Check for New Connections**.
- `packages.txt` so Chromium can start on Streamlit Community Cloud.
- Deployment and Gmail App Password setup instructions.

### Changed
- New **professional blue design**: navy sidebar with brand block, gradient page banners,
  coloured stat cards, centered login card, styled buttons / tables / forms.
- Headings, buttons, filters and table column headers now use **Title Case**.
- Reminder Log table shows proper column names.
- GST watcher shows a short, readable message when the browser cannot start
  (instead of a long error dump).

## v1.0.0 — 2026-11-12 (first release)

### Added
- Admin login gate on every page.
- Clients CRUD with GSTIN / PAN / email validation, applicable-compliance selection, and 12-month deadline auto-generation.
- Editable compliance templates (GSTR-1, GSTR-3B monthly + QRMP, GSTR-7/8/9, TDS payment + returns, PF/ESI, advance tax).
- Editable deadlines table.
- Dashboard: Overdue / Due in 7 days / Upcoming / Filed this month, red-amber-green table, filters, Mark as filed.
- Reminder bot: HTML email at 7/3/1/0 days + overdue, no duplicates, daily staff digest, full logging, `DRY_RUN` mode, failure-safe.
- Telegram reminder channel and WhatsApp click-to-chat links.
- GST news due-date watcher (Playwright, headless, public page only).
- Assisted GST return-status check (visible browser, human solves captcha, screenshot proof).
- APScheduler process: reminders 09:00 IST, watcher 09:30 IST.
- Bot Activity, Reminder Log and Reports pages (chart + Excel export).
- CSV client import with downloadable error report.
- Demo data (`seed.py`, 8 dummy clients).
- Support for Streamlit secrets (hosting) and automatic Chromium install for Playwright.
