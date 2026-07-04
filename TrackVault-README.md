# TrackVault

**A complete, single-file DJ toolkit that runs entirely in your browser.**

No install. No backend. No internet required after the first load. Download one HTML file, open it, and you have a full DJ library manager, dual-deck player, waveform analyzer, harmonic mixer, and set exporter — all in one place.

---

## How to Use

1. Download `TrackVault.html`
2. Open it in Chrome or Edge (Firefox supported with minor limitations — see below)
3. Drop your audio files in and start working

That's it. No npm. No config. No accounts.

---

## Features

### Library Management
- Drag-and-drop audio import (MP3, WAV, FLAC, AAC, M4A, OGG)
- Auto-parses title and artist from filename
- Persistent library across sessions — tracks survive browser refresh
- Offline relink — close and reopen, files reconnect automatically when you drop them back in
- Duplicate detection
- 5-star rating system
- Play count tracking

### Audio Analysis
- **BPM detection** — autocorrelation-based tempo detection
- **Musical key detection** — Krumhansl-Schmuckler profile algorithm, displays in standard notation and Camelot format
- **Spectral energy analysis** — real FFT-based scoring across four frequency bands (bass, low-mid, high-mid, presence) plus transient density; produces a meaningful 0–100 energy score for cross-track comparison
- Beat grid generation
- Waveform visualization with beat markers

### Playback
- Full transport controls (play, pause, seek, next, previous)
- Volume and gain control
- Dual-deck mode (Deck A and Deck B — independent players with manual crossfader)
- Beat-synced Auto-Mix engine
- Pitch/tempo control — ±8% or ±16% range per deck
- Loop engine — set IN/OUT points manually or snap to 1, 2, 4, or 8 bars
- 3-band EQ per deck (hi, mid, lo) with kill switches
- 8 hot cue points per track
- Tap tempo with automatic beat grid rebuild

### Mixing Tools
- Camelot wheel harmonic compatibility display
- AI-powered set planner — sequences tracks by BPM flow and harmonic key compatibility
- Frequency spectrum analyzer

### Library Organization
- Smart sort: by date added, title, artist, BPM, key, rating, energy, or duration
- Filters: all tracks, rated only, unanalyzed, duplicates
- Drag-to-reorder queue
- Playlist management
- Session history log

### Export
- **M3U** — universal playlist format
- **Rekordbox XML** — direct import into Pioneer Rekordbox
- **Traktor NML** — Native Instruments Traktor
- **Serato CSV** — Serato DJ
- **CSV Spreadsheet** — Excel / Google Sheets
- **Synapse CSV** — Synapse-compatible format with exact schema (`id, title, artist, bpm, key, energy, genre, vocal_presence`), Camelot key format, energy scaled 0–100
- **Set Sheet HTML** — printable set list with full metadata

### Metadata
- ID3 tag reader (v2.3/v2.4) — reads title, artist, album, BPM, key, genre, cover art
- ID3 tag writer — edit and write tags back to file, download as tagged MP3
- Inline title/artist editing — double-click any track in the library or now-playing panel to edit in place

### Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Space` | Play / Pause |
| `N` / `P` | Next / Previous track |
| `→` / `←` | Seek ±5 seconds |
| `↑` / `↓` | Volume ±5% |
| `M` | Mute toggle |
| `S` | Set cue at current position |
| `1`–`8` | Jump to cue 1–8 |
| `I` / `O` | Loop In / Out point (Deck A) |
| `L` | Toggle loop on/off (Deck A) |
| `?` | Keyboard shortcut reference |
| `Esc` | Close any open modal |

---

## Browser Compatibility

| Browser | Status |
|---------|--------|
| **Chrome 90+** | ✅ Full support — recommended |
| **Edge 90+** | ✅ Full support |
| **Firefox** | ⚠️ Works with limitations — File System Access API not supported, so offline relink uses fallback behavior |
| **Safari** | ⚠️ Partial — Web Audio API quirks may affect BPM detection accuracy |

> **Note:** The app must be opened directly as a local file or served from a web server. Some features (File System Access, audio decode) are blocked in sandboxed iframe embeds.

---

## AI-Powered Features

TrackVault includes an AI Set Planner that uses the **Anthropic Claude API** to generate optimized track sequences. To use this feature:

1. Analyze your tracks first (click **ANALYZE ALL**)
2. Open the Set Planner panel
3. Enter your Anthropic API key when prompted

The key is only stored in your browser session — it is never sent anywhere except directly to the Anthropic API. If you don't have an API key, all other features work without it.

Get an API key at [console.anthropic.com](https://console.anthropic.com).

---

## Privacy

TrackVault is 100% client-side. Your audio files never leave your computer. The only external network requests are:
- Google Fonts (Bebas Neue, Space Mono) — on first load only
- Anthropic API — only when you use the AI Set Planner with your own key

---

## Track Count & Performance

There is no hard-coded track limit. The practical ceiling is browser RAM:

| Format | Avg 5-min track | Comfortable library size |
|--------|----------------|--------------------------|
| MP3 320kbps | ~12 MB | 60–80 tracks |
| AAC/M4A | ~8 MB | 80–100 tracks |
| WAV 16-bit | ~50 MB | 15–25 tracks |
| FLAC | ~25 MB | 30–50 tracks |

For a live session, 20–40 MP3s in the queue is the sweet spot. The offline relink system means your library metadata persists indefinitely — only the tracks you actively use in a session need their audio files loaded.

---

## Technical Notes

- **Zero external dependencies** — no frameworks, no libraries, no CDN
- **Single file** — the entire application is one HTML file (~215 KB)
- **Web Audio API** — all audio processing is native browser
- **Canvas API** — waveform and spectrum rendering
- **IndexedDB / localStorage** — persistence without a backend
- **Pure JS FFT** — spectral energy analysis uses a hand-written radix-2 Cooley-Tukey FFT, no DSP libraries

---

## License

Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)

Free to use, share, and modify for personal and non-commercial purposes. Attribution required. Commercial use requires written permission.

© Don · AudioDsgn

---

## About

Built by **Don** at **AudioDsgn** — 25+ years behind the decks, building tools the DJ community actually needs.

Developed with [Claude](https://anthropic.com) by Anthropic.
