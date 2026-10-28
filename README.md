# SBD ScanTrack - Trimble Connect extension (synced version)

Files: index.html (app), manifest.json (registration), icon.svg (menu icon), README.md (this guide).

## Deploy
1. Upload all four files to the GitHub repo `sbd-scantrack` (replace the old ones). GitHub Pages republishes in ~1 minute.
2. In Trimble Connect: Project Settings > Apps & Capabilities > Add Custom > paste
   https://majeedjawhar-gif.github.io/sbd-scantrack/manifest.json  (skip if already added; hard-refresh the page).

## How central data works
- Data is kept in ONE file, `sbd_scantrack_data.json`, in the project folder "SBD ScanTrack Data" (created automatically).
- The app reads/writes it with the Trimble Connect Core API using the signed-in user's own access token,
  so only people who have access to the Trimble Connect project (and write permission to save) can see or change data.
- Every 30 s the app checks for a newer file version and merges it (record-level, latest edit wins; deletions are kept as markers).
- A copy is cached in each browser so the app still works if the connection drops.

## First-time use
1. Open the extension, go to Sync & Connection, click "Request access token", approve consent.
2. Import SBD_ScanTrack.xlsx (Sync & Connection). Lists, equipment and log rows go to the central file.
3. Open the extension on another computer: the same data appears.

## If saving fails
Open Sync & Connection > Diagnostics and send the log lines. The upload call (`push()` in index.html) must match the
Trimble Core API schema for POST /files/fs/initiate and /files/fs/commit; it is the one part not yet verified against a live project.
Fallback: "Download data file (.json)", then upload it into the "SBD ScanTrack Data" folder in Trimble Connect; other users' apps will read it.
