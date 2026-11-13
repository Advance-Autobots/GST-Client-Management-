# Tester Guide — CA Compliance Reminder Bot v1.0.0

Thank you for testing. Use **DRY_RUN=true** unless the owner tells you otherwise,
so no real emails / messages are sent.

## Get started
1. Open the app link from the project README (https://gstclientmanagement.streamlit.app).
2. Log in with the admin password the owner gave you.
3. If the app is empty, add a client (Clients page) or import the sample CSV
   (Clients → *Import clients from CSV* → *Download sample CSV* → upload it).

## Test checklist

| # | Area | Steps | Expected |
|---|---|---|---|
| 1 | Login | Wrong password, then correct one | Wrong is rejected; correct opens dashboard. Other pages locked before login |
| 2 | Add client | Clients → New client, GSTIN `123`, Save | Error shown; the other fields you typed are **kept** |
| 3 | Add client (valid) | Name `Test Co`, GSTIN `27AABCS1234A1Z5`, PAN `AABCS1234A`, pick GSTR-1 (Monthly), TDS Payment, Save | Saved; deadlines appear on Dashboard |
| 4 | PAN mismatch | Use GSTIN `27AABCS1234A1Z5` with PAN `AABCS9999A` | "PAN does not match GSTIN" error |
| 5 | Dashboard | Check 4 metric cards, red/amber/green statuses, filters | Counts match the table |
| 6 | Mark as filed | Tick rows, **Mark as filed** | Rows become Filed; "Filed this month" increases |
| 7 | Edit deadline | Deadlines page → change a due date → Save | Change persists after refresh |
| 8 | Edit template | Templates → change a due day → Save | Saved; new clients use the new day |
| 9 | Reminder bot | Dashboard → **Run reminder bot now** | Status line shows counts; Reminder Log has DryRun rows |
| 10 | No duplicates | Set `DRY_RUN=false` with SMTP configured, run twice | Second run sends nothing new ("already sent") |
| 11 | Failure handling | Client with no email, run bot | `Failed` row "Client has no email address"; app does not crash |
| 12 | Reminder Log | Filter by client / status / dates | Table filters correctly |
| 13 | GST watcher | Bot Activity → **Run GST watcher** | ~20 headlines read; Bot run history gets a row; flagged items show "Possible due date change" |
| 14 | CSV import | Upload a CSV with one good and one bad row | Good imported; error report CSV downloads |
| 15 | WhatsApp | Dashboard → click 💬 Chat | WhatsApp opens with prefilled message |
| 16 | Telegram | Clients → pick a client → *Connect This Client on Telegram* → open the link on your phone, press Start → **Check for New Connections**. Then run bot with `DRY_RUN=false` | Bot replies "Connected"; reminder arrives in Telegram |
| 17 | Reports | Reports page | Chart shows; Excel downloads and opens with 3 sheets |
| 18 | Scheduler | Run `python scheduler.py` (local only) | Log says "Scheduler started"; runs at 09:00 / 09:30 IST |
| 19 | Assisted check | Bot Activity → Assisted check (local desktop only) | Browser opens, GSTIN pre-filled, you solve the captcha, proof screenshot saved |

## Known limitations (not bugs)
- Single admin password; no multiple users.
- On free cloud hosting the database may reset and the scheduler / assisted check are unavailable (items 18 and 19 are for the project owner's PC only).
- The GST portal may reject automated navigation; this is outside the app's control.

## Reporting a bug
Please include: page name, what you clicked, what you expected, what happened,
and a screenshot or the red error text.
