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

By default, the deploy script mounts `./media` from your host into the container and exposes each top-level subfolder directly at the web root. Put audio files in subfolders so the app can access them.

Or provide a custom host media folder as the only argument:

```bash
./deploy.sh /path/to/your/media
```

Example with your own top-level media folder:

```bash
./deploy.sh /home/djones/Media
```

Then in the hidden configuration screen use:

- **Music Albums Folder Path**: `Music` (resolves to `/Music`)
- **Audio Books Folder Path**: `AudioBooks` (resolves to `/AudioBooks`)

### Worked example: deploy + configure end-to-end

If your host media folder looks like this:

```text
/home/djones/Media
├── Music
│   ├── Abbey Road
│   │   ├── 01 Come Together.mp3
│   │   └── 02 Something.mp3
│   └── Kind Of Blue
│       ├── 01 So What.flac
│       └── 02 Freddie Freeloader.flac
└── AudioBooks
    └── Moby Dick
        ├── 01 Chapter 1.mp3
        └── 02 Chapter 2.mp3
```

1. Deploy using that folder:

   ```bash
   ./deploy.sh /home/djones/Media
   ```

2. Open `https://localhost:3014` (or the printed LAN URL) and accept the self-signed cert warning the first time.
3. Open hidden configuration by tapping **Rest** 3 times quickly.
4. Set:
   - **Music Albums Folder Path**: `Music`
   - **Audio Books Folder Path**: `AudioBooks`
   - (Optional) **Internet Radio Source** to your JSON/M3U endpoint
5. Tap **Save Configuration**.

Result:
- The Books tab reads media from `/AudioBooks`.
- The Music tab reads media from `/Music`.
- You do **not** need to set or manage a separate media root in the app.

## Basic controls

- **Bottom tabs**: switch between **Radio**, **Books**, **Music**, and **Rest**.
- **Tap media cards**: start playback for a station/book/album.
- **Now Playing bar**: pause/resume, view current title, and close the player strip.
- **Hidden config screen**: tap the **Rest** tab 3 times quickly, then set Radio/Books/Music source paths. Saved values are persisted in browser storage and immediately used to load media libraries.
  - In that screen, you can also add/edit/remove **Custom Radio Stations** (name + stream URL). When at least one custom station is saved, the Radio tab uses that local list instead of the configured radio source path.
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
