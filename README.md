# SimpleMedia

SimpleMedia is a single-page, touch-first media interface designed for older adults. It presents large controls, high-contrast visuals, and simple navigation for common listening tasks like radio, audiobooks, music playback, and sleep/noise settings.

## What the application is

- A static web app (`index.html`) with no build step required.
- Optimized for tablet-style touch interaction.
- Focused on accessibility through large tap targets and straightforward tab-based navigation.

## Build / run instructions

Because this is a static app, you can run it directly with any static file server.

### Option A: open directly

Open `index.html` in a browser.

### Option B: run a local static server (recommended)

```bash
python3 -m http.server 8080
```

Then open <http://localhost:8080>.

### Option C: deploy with Docker helper

Use the included script (defaults to port `3014`):

```bash
./deploy.sh
```

Or provide custom port and hostname:

```bash
./deploy.sh 8080 localhost
```

## Basic controls

- **Bottom tabs**: switch between **Radio**, **Books**, **Music**, and **Rest**.
- **Tap media cards**: start playback for a station/book/album.
- **Now Playing bar**: pause/resume, view current title, and close the player strip.
- **Rest tab**:
  - Set **Sleep Timer** (15/30/60 minutes or Off).
  - Toggle **Background Noise** and choose White/Pink/Blue noise.
  - Adjust noise level with the volume slider.
- **Clock / status area**: shows time and sleep indicator when active.

## Roadmap

- Connect UI controls to real streaming/audio playback sources.
- Add persistent storage for settings (sleep timer, noise profile, volume).
- Add keyboard and screen-reader accessibility improvements.
- Add automated tests for interaction flows.
- Add CI workflow for lint/check/deploy validation.
