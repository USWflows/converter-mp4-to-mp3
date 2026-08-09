# 🎵 Pulse Audio — WebAssembly Media Workstation

**Pulse Audio** is a lightweight, high-performance, browser-based media conversion suite powered by WebAssembly (FFmpeg). It allows users to convert video to audio and render audio files into shareable MP4 video containers directly on their device without uploading files to external servers.

---

## 👨‍💻 Created By

**USWflows**

---

## 💡 How It Works

Pulse Audio runs **100% client-side** inside the user's web browser:

1. **Virtual Filesystem (VFS):** When a file is uploaded via drag-and-drop or file picker, it is loaded into the browser memory using FFmpeg's Virtual Filesystem.
2. **In-Browser Processing:** The core audio/video processing engine relies on WebAssembly (`@ffmpeg/ffmpeg` / `ffmpeg-core-st`). FFmpeg commands execute locally in your browser environment without needing backend server resources.
3. **Local Export & Web Share:** Once processed, the engine generates an output Blob and Object URL. You can download the master file directly or save/share it using the native Web Share API on supported devices.

---

## ✨ Key Features

### 🎧 MP4 to MP3 Extraction (`index.html`)
- **Custom Bitrate Options:** Choose target audio bitrates (**128k, 192k, 256k, 320k**).
- **High-Fidelity Audio:** Encoded using `libmp3lame` for crystal-clear master tracks.
- **Dynamic Waveform Visualizer:** Real-time HTML5 `<canvas>` audio visualizer animation during playback and processing.
- **Multiple Video Formats:** Supports `.mp4`, `.mov`, `.m4v`, `.webm`, and `.mkv`.

### 🎬 MP3 to MP4 Video Generation (`mp3-to-mp4.html`)
- **Audio to Video Conversion:** Converts `.mp3`, `.wav`, or `.m4a` files into lightweight `.mp4` video containers.
- **Optimized Video Encoding:** Utilizes `libx264` and `aac` with a still image background frame for optimized file sizes and platform compatibility.

### 📱 Progressive Web App (PWA) & Offline Ready
- **PWA Integration:** Equipped with `manifest.json` and `sw.js` (Service Worker) for installability on mobile and desktop.
- **Privacy First:** Your files **never leave your device**—no cloud uploads, zero bandwidth costs, and complete data privacy.
- **Native Device Sharing:** Built-in support for `navigator.share()` allowing direct exports to iOS Photos/Files or Android share menus.
- **Modern UI:** Designed with a sleek glassmorphism aesthetic using Plus Jakarta Sans and Space Grotesk typography.

---

## 🚀 Getting Started

### Prerequisites
All you need is a modern web browser with WebAssembly support (Chrome, Edge, Safari, Firefox, Opera).

### Running Locally
1. Clone or download this repository.
2. Serve the directory using any HTTP local server (e.g., Live Server in VS Code, `npx serve`, or `python3 -m http.server`).
   > *Note: Running directly via `file://` protocol may block Service Worker registration or WebAssembly scripts due to browser CORS policies.*
3. Open `http://localhost:3000` (or your local server URL) in your browser.

---

## 🛠️ Built With

* **HTML5 / CSS3 / JavaScript (ES6+)**
* **[FFmpeg WebAssembly](https://github.com/ffmpegwasm/ffmpeg.wasm)** (`@ffmpeg/ffmpeg` v0.11.6)
* **HTML5 Canvas API**
* **Web Share API & Service Workers**

---

## 📄 License

Created with ❤️ by **USWflows**. Open for personal and educational use.
