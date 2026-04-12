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

Use the included script (fixed at `https://localhost:3014`):

```bash
./deploy.sh
```

By default, the deploy script mounts `./media` from your host into the container at `/app/Media` (served as `/Media/...` in the browser). Put audio files in that host folder so the app can access them.

Or provide a custom host media folder as the only argument:

```bash
./deploy.sh /path/to/your/media
```

Example with your own top-level media folder:

```bash
./deploy.sh /home/djones/Media
```

Then in the hidden configuration screen use:

- **Media Root Folder Path**: `/Media/`
- **Music Albums Folder Path**: `Music` (resolves to `/Media/Music`)
- **Audio Books Folder Path**: `AudioBooks` (resolves to `/Media/AudioBooks`)

## Basic controls

- **Bottom tabs**: switch between **Radio**, **Books**, **Music**, and **Rest**.
- **Tap media cards**: start playback for a station/book/album.
- **Now Playing bar**: pause/resume, view current title, and close the player strip.
- **Hidden config screen**: tap the **Rest** tab 3 times quickly, then set Radio/Books/Music source paths. Saved values are persisted in browser storage and immediately used to load media libraries.
- **Rest tab**:
  - Set **Sleep Timer** (15/30/60 minutes or Off).
  - Toggle **Background Noise** and choose White/Pink/Blue noise.
  - Adjust noise level with the volume slider.
- **Clock / status area**: shows time and sleep indicator when active.

## Roadmap

- Persist additional runtime settings (sleep timer, noise profile, volume).
- Add keyboard and screen-reader accessibility improvements.
- Add automated tests for interaction flows.
- Add CI workflow for lint/check/deploy validation.
