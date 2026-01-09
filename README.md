# OverlayMediaCapture(Bookmarklet)
A lightweight bookmarklet that injects a floating overlay into any webpage with an HTML5 video, allowing you to capture screenshots (PNG) and record short clips (MP4) directly from the video currently playing. No extensions. No installs. Just click and capture.

## Features
- Floating, minimal overlay UI (pill-style) on the top-right corner
- Automatically detects the active <video> element on the page
- One-click screenshot capture (PNG)
- Start/stop video recording (canvas-based, MP4 download)
- 30 FPS recording using canvas.captureStream()
- Automatic timestamped filenames (YYYYMMDDHHmmss)
- Works on most modern sites with HTML5 video

## System Requirements
Modern browser with support for HTMLVideoElement, CanvasRenderingContext2D, canvas.captureStream(), and MediaRecorder. Recommended: Chrome, Edge, Firefox (latest versions). Note: Some sites use DRM or CORS restrictions. In those cases, the video may appear black or fail to record. This is a browser security limitation.

## Installation
Option A — Bookmarklet (Recommended): Create a new bookmark in your browser, name it MediaCaptureOverlay, paste the full bookmarklet code in the URL/Location field, and save. Option B — Developer Mode (Console): Save the code into a file (for example mediacaptureoverlay.js), open DevTools on any page (F12), paste the code into the Console and press Enter.

## Usage
Open any webpage with an HTML5 video, start playing the video, click the MediaCaptureOverlay bookmark, and a small overlay will appear in the top-right corner with two buttons.

## Buttons
Capture: Takes a snapshot of the current frame and downloads it as image_YYYYMMDDHHmmss.png. Record / Stop: Click Record to start recording the video, click Stop to finish and automatically download video_YYYYMMDDHHmmss.mp4.

## How It Works
Scans all <video> elements on the page, selects the first one that is playing, not paused, not ended, and has valid dimensions, draws the video frames into a <canvas> at ~30 FPS, uses MediaRecorder to record the canvas stream, and exports the result as a downloadable file.

## Limitations
Audio capture is browser-dependent. In Safari 26.x, audio is not captured due to limitations in canvas.captureStream() and inconsistent support for video.captureStream(). Chrome and some other browsers may capture audio when supported, but this is not guaranteed. DRM-protected streams (Netflix, Prime, etc.) will not work. Cross-origin (CORS) restrictions may result in black frames or failed recordings. Some browsers may output WebM internally even if the file is named .mp4. Performance depends on system resources and video resolution.

## Example Filenames
image_20260107142355.png  
video_20260107142410.mp4

## Development Notes
The entire tool is implemented as a single self-contained bookmarklet using Vanilla JavaScript, HTML5 Canvas, MediaRecorder API, and dynamic DOM injection for the UI. No dependencies. No build step.

## Author
Gregori M.

## License
MIT License
