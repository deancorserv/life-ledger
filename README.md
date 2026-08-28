# The Life Ledger

A shared leaderboard that ranks a group chat across six pillars: physical,
financial, independence, education, spiritual and gaming.

Single static page, no build step. Shared standings are stored in Supabase and
read and written straight from the browser with the publishable key.

## Scoring principles

- **Current form only.** Stop training and both lifts score zero. No historic PBs.
- **Everything relative.** Lifts are bodyweight multiples adjusted by masters age
  coefficients. The 5km is age graded.
- **No salary anywhere.** You enter what is left at the end of the month, and the
  market value of anything you get free (a room, food, a phone on the family
  contract) is charged back against it before scoring.

## Local development

Serve the folder over HTTP, since `file://` blocks browser storage in some browsers.

    python3 -m http.server 8000

## Data

Two tables in Supabase, `ledger_people` and `ledger_settings`, both open to the
anon role by design. Anyone with the link can read and edit the board.
