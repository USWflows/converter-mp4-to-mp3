USW Pulse Studio 2.0
An upgraded, privacy-minded audio/video converter for your browser. Built from the supplied converter-mp4-to-mp3-main project by USWflows. The app does not require an account or a server to process media: files are read and converted locally in the browser using FFmpeg WebAssembly.
What's new
- A refreshed, responsive interface with accessible keyboard controls and light/dark themes.
- Video → audio with MP3, M4A (AAC), WAV (16-bit PCM), and FLAC output.
- Audio → MP4 video with optional cover art or automatically generated artwork and 720p/1080p export.
- Batch queue with up to 20 files, individual progress, errors, file previews, and separate downloads.
- 128–320 kbps encoding, 44.1/48 kHz sample rate, mono/stereo.
- Start/end trimming, adjustable output volume, and optional loudness normalization.
- Optional native system sharing (where supported), saved preferences, and PWA manifest/icons.
- Safer memory limits, output cleanup, stop/restart controls, explicit engine-load errors, and UI-shell caching.
Files (keep all of these together)
File	Purpose
index.html	Main interface
styles.css	Layout, themes, responsive styling
app.js	Queue, FFmpeg integration, controls, previews
manifest.json	Installable app metadata
sw.js	Cache for the local app interface
icon-192.png	Small app icon
icon-512.png	Large app icon
README.md	Setup and usage
LICENSE	Original license retained
.github/workflows/blank.yml	Project syntax checks on GitHub
.github/workflows/static.yml	GitHub Pages deployment workflow


All media files are kept in your browser memory, not uploaded by this app. External Google Fonts from the old project were removed, so only the conversion engine is a third-party runtime dependency. The app downloads the @ffmpeg/ffmpeg@0.11.6 script and @ffmpeg/core-st@0.11.1 WebAssembly engine from CDNs; internet access is required for that first load (and again when the engine is not browser-cached). The service worker caches the local app shell only; it does not guarantee offline transcoding.
Run locally (Windows, simple)
1. Put the separately downloaded files inside one folder, with the names shown above.
2. In that folder, open Windows Terminal or Command Prompt and run:
   py -m http.server 8000
   If py isn't available, try python -m http.server 8000. Python isn't needed on a normal HTTPS hosting service.
3. Open http://localhost:8000/ in Chrome or Edge, with internet connected.
4. Drag in your video or audio files, choose settings, select Convert files, and use Download beside each result.
You can also deploy all these files to the same folder on a standard static HTTPS web host (including GitHub Pages). No server-side conversion code is required.
Known limits and accuracy notes
- Browser memory and WebAssembly runtime constraints are far tighter than desktop FFmpeg. To reduce crashes, each input is capped at 400 MB; very long or complex videos may still exceed browser memory. Do smaller batches if memory is limited.
- A 320 kbps output setting does not restore quality lost in a lower-quality source. WAV/FLAC preserve the output of decoding, not an original's lost information.
- The MP4 cover is a 2 fps still image encoded to H.264 and AAC. Encoding 1080p is slower than 720p. Unsupported formats/codec combinations may not work even if a filename extension is recognized.
- Media without an audio stream cannot be extracted; such files show an error.
- Stop terminates and reloads the FFmpeg WebAssembly engine. Work on the active file is discarded; completed exports remain available.
- Some browsers limit automatic multi-file downloads. Every result has a reliable individual Download link.
- Some mobile browsers have lower memory limits or limited WebAssembly support.
- Do not open using file:// if the conversion engine won't load. Serve over http://localhost or HTTPS.
- The service worker requires localhost/HTTPS and is optional; external FFmpeg resources aren't pre-cached by it.
Source and licensing
Keeps the original project license in LICENSE. The FFmpeg runtime is independently licensed; review licensing terms when distributing an app with bundled codec components. Third-party engine dependency URLs can be found in index.html and app.js.
