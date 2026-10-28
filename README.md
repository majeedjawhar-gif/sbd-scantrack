# SBD ScanTrack – Trimble Connect extension

Files: `index.html` (the app), `manifest.json` (tells Trimble Connect about the app), `icon.svg`.

## Step 1 – Host the files on HTTPS (GitHub Pages, free)
1. Create a GitHub repository named `sbd-scantrack` (public).
2. Upload `index.html`, `manifest.json`, `icon.svg`, `README.md`.
3. Repository Settings → Pages → Source: "Deploy from a branch" → `main` / root → Save.
4. Wait ~1 minute. Your site is `https://YOUR-USERNAME.github.io/sbd-scantrack/`.

## Step 2 – Edit manifest.json
Replace every `YOUR-USERNAME` with your GitHub username (or use your own domain).
Open `https://YOUR-USERNAME.github.io/sbd-scantrack/manifest.json` in a browser to confirm it loads.
GitHub Pages sends CORS headers, which Trimble Connect needs to read the manifest.
Other hosts must send `Access-Control-Allow-Origin`.

## Step 3 – Add the extension in Trimble Connect
1. Sign in at https://web.connect.trimble.com and open your project.
2. You must be a **project administrator**.
3. Project Settings → **Apps & Capabilities** → **Add Custom**.
4. Paste the manifest URL and confirm.
5. "SBD ScanTrack" appears in the left navigation with Dashboard, Scanning Log and Trimble Connection.

## Step 4 – Grant access token consent (optional)
Open "Trimble Connection" → **Request access token** → approve the consent message.
The token is needed only if you later call Trimble Connect REST APIs.

## What is stored where
Scanning entries are saved in the browser's localStorage, per Trimble project, per user and device.
For shared team data you need a backend and database (see the main SBD ScanTrack plan).
