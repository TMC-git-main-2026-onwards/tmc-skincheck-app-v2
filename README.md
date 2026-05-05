# TMC Skin Check App v0.2

Free skin health check PWA for [The Mole Clinic](https://themoleclinic.co.uk). Profiles skin cancer risk, personalises UV safety advice, and drives clinic bookings.

This is a patient acquisition and lead generation tool. It is **not a diagnostic tool**.

**Live:** https://tmc-git-main-2026-onwards.github.io/tmc-skincheck-app-v2/

---

## What's New in v0.2

- **Personalised homepage dashboard** — returning users skip onboarding and land on their risk profile with live UV safety data
- **UV index integration** — real-time UV via Open-Meteo (keyless), displayed as a half-circle EADO gauge
- **Bias-corrected SPF recommendations** — per Monk Skin Tone Scale (Gadare et al., MIT 2026 debiasing principle)
- **Travel detection** — detects when users are abroad and shows a return-home banner
- **Three new consent screens** — location, travel tracking, and notifications

---

## Running Locally

No build step. Open `index.html` directly:

```bash
git clone https://github.com/TMC-git-main-2026-onwards/tmc-skincheck-app-v2.git
cd tmc-skincheck-app-v2
start index.html       # Windows
open index.html        # macOS
```

> **Note:** Geolocation requires HTTPS in most browsers. For local testing without GPS, the app falls back gracefully — UV card shows a "location not enabled" state. On GitHub Pages (HTTPS) the full flow works.

---

## Resetting the App (Demo / Testing)

The app stores the user profile in `localStorage` under the key `tmcProfile`. To re-run the onboarding flow:

1. Open DevTools → Application → Local Storage
2. Delete `tmcProfile` (and optionally `tmcLocationHistory`, `tmcTravelBannerDismissed`)
3. Refresh

---

## Tech Stack

| | |
|---|---|
| Structure | Single `index.html` — inline CSS and JS |
| Frameworks | None |
| Fonts | DM Sans + Fraunces (Google Fonts CDN) |
| UV / Weather | Open-Meteo API (keyless, no account required) |
| Geocoding | Nominatim / OpenStreetMap (keyless) |
| Photos | Stored client-side as base64 (no backend) |
| Persistence | `localStorage` only |
| Hosting | GitHub Pages — auto-deploys from `main` via Actions |
| PWA | `manifest.json` in root |

Supports iOS Safari, Android Chrome, and desktop browsers. Mobile-first, max-width 480px.

---

## Deployment

Push to `main` — GitHub Actions deploys automatically to the `gh-pages` branch within ~2 minutes.

```bash
git add .
git commit -m "[feat] Description

Trello: https://trello.com/c/iWUhQpVC"
git push
```
