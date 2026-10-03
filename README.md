# ShaneIT6github.io
ScrimbaMobile
# Scrimba Offline Notes – PWA with Login & Sync

A complete **offline-first Progressive Web App** inspired by Scrimba courses (Firebase + PWA lessons).

## Features

- **Login / Account creation** – stored locally in IndexedDB (any username + password works)
- **Offline support** – Service Worker + Cache API + IndexedDB
- **Background sync queue** – changes made offline are queued and automatically replayed when the connection returns
- **Installable PWA** – add to home screen on mobile or desktop
- **Real-time status indicator** – Online / Offline / Syncing
- **Pending vs Synced visual cues** on each note

## How to run

### Option 1 – Local static server (recommended)

```bash
# From this folder
npx serve .
# or
python3 -m http.server 3000
```

Then open http://localhost:3000

### Option 2 – Just open index.html

Some browsers restrict Service Workers and IndexedDB on `file://` protocol.  
A local server is strongly recommended.

## How it works

| Layer            | Technology              | Purpose                          |
|------------------|-------------------------|----------------------------------|
| Auth             | IndexedDB + localStorage| Local username/password accounts |
| Data storage     | IndexedDB               | Notes + sync queue               |
| Offline shell    | Service Worker + Cache  | App loads without network        |
| Sync             | Queue + online event    | Replay create/update/delete      |
| Installability   | Web App Manifest        | Add to home screen               |

## Testing offline behaviour

1. Open the app and log in.
2. Open DevTools → Network → check “Offline”.
3. Add or delete notes – they appear with a “pending sync” badge.
4. Uncheck Offline – the status turns to “Syncing…” then “Online” and notes become synced.

## Project structure

```
scrimba-offline-app/
├── index.html
├── manifest.json
├── sw.js                 # Service Worker
├── css/styles.css
├── js/
│   ├── db.js             # IndexedDB helpers
│   ├── auth.js           # Local auth
│   ├── sync.js           # Offline queue + replay
│   └── app.js            # UI logic
├── icons/
│   ├── icon-192.png
│   └── icon-512.png
└── README.md
```

## Notes for Scrimba learners

This project demonstrates the same concepts taught in Scrimba’s:

- “Build a Mobile App with Firebase” (PWA conversion)
- “Learn Firebase” (auth + realtime data patterns)

Here we replace Firebase with pure browser APIs so the whole app works 100 % offline without any backend or API keys.

Enjoy building!
