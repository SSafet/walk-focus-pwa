# Momentum Logger

A lightweight phone-first PWA for tracking daily metrics: walking, focused work, shutdown, and bedtime. Timer + manual logging, local-only storage, works fully offline.

**Live app: https://ssafet.github.io/walk-focus-pwa/**

## Features

- Timer with start/pause/resume/reset
- Manual logging with optional notes
- Quick bedtime log
- Daily summary with color-coded stat cards
- Past 14 days history
- Wake Lock API keeps screen on during timer
- Export logs as JSON
- Installable PWA — works offline after first visit

## Metrics

| Metric | Protocol |
|---|---|
| Walking (easy) | 30 min @ 2.5-3.0 km/h + 10kg vest |
| Walking (intense) | 15 min @ 4.5-5.0 km/h + 10kg vest |
| Focused work | Minutes of deep work |
| Shutdown done | End-of-day event |
| Bedtime | Timestamp event |
| Custom | Free text |

## Install on phone

1. Open https://ssafet.github.io/walk-focus-pwa/ in your phone's browser
2. **iOS**: Tap Share > Add to Home Screen
3. **Android**: Tap the browser menu > Install app / Add to Home Screen
4. The app now works fully offline — no internet needed

## Local development

```bash
# Serve locally (for development only — offline/PWA won't work over HTTP)
python3 -m http.server 8080
# Open http://localhost:8080

# For HTTPS (needed to test service worker/offline):
brew install mkcert
mkcert -install
mkcert -cert-file cert.pem -key-file key.pem localhost
python3 server.py
# Open https://localhost:8443
```

## Deploy

The app auto-deploys to GitHub Pages on every push to `main` via `.github/workflows/pages.yml`.

## Tech stack

Single HTML file, no build step, no dependencies:
- Vanilla HTML/CSS/JS
- localStorage for persistence
- Service worker for offline caching
- Web App Manifest for installability

## Data

All data stays in your browser's localStorage under the key `momentum_logger_v1`. Nothing is sent to any server. Use the Export button to back up your logs as JSON.
