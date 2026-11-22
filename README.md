# Crypto Trading Journal (Web + Android APK)

A free, offline-capable trading journal. Data is stored in the browser on each device.

## Files in this repository

| File | Purpose |
|---|---|
| `index.html` | The entire app (dashboard, trades, calendar, cash flow, review, settings, backup) |
| `manifest.json` | Tells browsers and Android how to install the app |
| `sw.js` | Service worker: enables offline use and installability |
| `icon-192.png`, `icon-512.png` | App icons (required for the APK) |
| `icon.svg` | Source icon, also used by the service worker cache |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is |

All files must sit in the **root** of the repository (same level as `index.html`).

## Requirements

**To host (free):**
- A GitHub account (https://github.com)
- A web browser

**To build the APK (free, no installs needed):**
- Hosting over HTTPS (GitHub Pages provides this)
- A valid `manifest.json` with name, icons (192 and 512 px), and display mode
- A registered service worker (`sw.js`)
- PWABuilder account access (https://www.pwabuilder.com), which generates the APK in the browser

**Optional, to build locally instead:**
- Node.js 18 or newer
- Java JDK 17
- Android SDK (command-line tools) with build-tools
- Bubblewrap CLI: `npm install -g @bubblewrap/cli`

**To install on Android:**
- Android 8.0 or newer
- Permission to install apps from unknown sources (Settings, then Install unknown apps, for your file manager or browser)

## Deploy to GitHub Pages

1. Create a new **public** repository (for example `APK-TRADING-JOURNAL`).
2. Click **Add file → Upload files**, drag in every file from this folder, then **Commit changes**.
3. Go to **Settings → Pages**. Under *Build and deployment*, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then **Save**.
4. After about a minute, open `https://YOUR-USERNAME.github.io/APK-TRADING-JOURNAL/`.
5. Check these open correctly:
   - `.../manifest.json` (shows JSON)
   - `.../sw.js` (shows JavaScript)
   - `.../icon-512.png` (shows the icon)

## Build the APK with PWABuilder

1. Go to https://www.pwabuilder.com and paste your site address.
2. Click **Start**. Errors should be 0.
3. Click **Package For Stores**, choose **Android**.
4. Set a package ID such as `com.yourname.tradejournal`. Keep it the same for every future update.
5. Choose the option to generate a new signing key. **Download and keep the key file and its password.** You need them for updates.
6. Download the package and unzip it. Use the `.apk` file to install directly on your phone. Use the `.aab` only for Google Play.

## Install on your phone

1. Copy the `.apk` to the phone (Google Drive, email, or USB).
2. Open it from Files or Downloads and allow installation from that app when prompted.
3. Tap **Install**, then open **Crypto Trading Journal**.

## Backup your data

Data is stored per browser and per installed app, so the web version and the phone app keep separate data. Use **Settings → Backup → Copy backup** and paste it into **Import** on the other device. Type `REPLACE` in the confirm box first.

## Updating the app later

Edit files in GitHub and commit. GitHub Pages updates the website automatically. To update the APK, generate a new package in PWABuilder with the same package ID and sign it with your saved key. Increase the version code, or Android will refuse the update.
