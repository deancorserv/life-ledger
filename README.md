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

## Privacy

Raw numbers never reach the server. The browser scores you locally and uploads
only the six pillar scores, your name, your age and your badges. The board table
has explicit columns and no blob for person data, so a client physically cannot
upload cash flow, net worth, lifts or body fat even by accident.

Your own figures live in this browser's local storage. That means you can edit
your entry only from the device you entered it on, and the Copy backup data
button in the Rulebook is how you move it to another phone.

Changing the pillar weights re-ranks everyone live, because the overall is
recomputed from pillar scores. Changing the imputed charge back rates only
affects people once they next save, since rescoring needs the raw numbers.

## Data

`ledger_board` holds scores only, `ledger_settings` holds the shared weights.
Both are open to the anon role by design.
