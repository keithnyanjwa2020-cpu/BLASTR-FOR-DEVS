# Blastr — Remix Edition ⚡

A complete, self-contained streaming-music website in a handful of static files. No backend, no build step, no dependencies — every song in the seed catalog is **composed and rendered on your device** with the Web Audio API.

## Run it

Any static file server works:

```bash
cd blastr
python -m http.server 8000
# open http://localhost:8000
```

Opening `index.html` directly from disk also works (the service worker and install prompt are simply skipped on `file://`).

## What's inside

| File | Purpose |
|------|---------|
| `index.html` | The whole app — UI, player, admin studio, music engine |
| `manifest.json` | PWA manifest (installable app, theming) |
| `sw.js` | Service worker — offline cache (app shell + visited pages) |
| `icon.svg` | App icon / favicon |

## Highlights

- **Procedural music engine** — the 24 seed tracks are real compositions (drums, bass, pads, arps, lead melodies, reverb and bus compression) rendered offline to CD-quality WAV via `OfflineAudioContext`, then cached in memory with an LRU policy. Each track has its own style, key and tempo.
- **Endless radio** — when a queue finishes, playback keeps going with a random pick from the library.
- **Full admin studio** (sidebar → Admin Matrix, passcode `12345678`) — upload your own audio/covers/MP4 loops, manage artists & albums, bulk upload, custom genres, feature tracks, post home announcements.
- **Playlists, likes, follows, queue, drag-to-reorder home shelves, taste quiz, charts** computed from real play history.
- **Deep personalization** — themes, accent colors, live wallpapers, visualizer styles, equalizer, layout editor, profiles with PINs, keyboard shortcuts (`Space`, `←/→`, `N/P`, `L`, `M`, `F`, `Q`, `Ctrl+K`).
- **Offline-first** — uploads are stored in IndexedDB; the service worker caches the app shell so the site loads with no network.
- **Backup / restore** — Settings → “Backup to file” exports everything (metadata *and* media) as a single JSON you can restore anywhere.

## Notes

- Seed audio is generated per session (a moment of “Composing…” on first play), so the repo stays tiny and copyright-clean.
- Admin ID default is `12345678` — change it in Admin → Dashboard.
