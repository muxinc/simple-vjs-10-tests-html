# simple-vjs-10-tests-html

Simple HTML test pages for [Video.js v10](https://videojs.com/) (beta), loaded entirely from CDN — no build step required. Useful for quickly prototyping and testing VJS 10 custom elements, skins, and media sources.

## Pages

| Page | Description |
|------|-------------|
| `video.html` | Basic MP4 playback |
| `audio.html` | MP4 audio-only playback |
| `hls-video.html` | HLS via `hls-video` + hls.js |
| `dash-video.html` | DASH via `dash-video` + dash.js |
| `simple-hls-video.html` | HLS via `simple-hls-video` + the browser's native Streaming Protocol Framework (SPF) |

Each page includes a skin toggle to switch between the **default** and **minimal** VJS 10 skins.

## Running locally

No install required. Serve the files with any static HTTP server, e.g.:

```bash
npm start
# opens http://localhost:8080
```

This uses [`http-server`](https://github.com/http-party/http-server) via `npx` — no prior install needed.

Alternatively, use any server you prefer:

```bash
npx serve .
python3 -m http.server 8080
```

> The pages must be served over HTTP (not opened as `file://`) due to ES module and CORS requirements.

## Modifying

All dependencies are loaded from CDN ([esm.sh](https://esm.sh) and [jsDelivr](https://cdn.jsdelivr.net)), so there is nothing to install or build.

**To change the VJS version**, update the version string in the CDN imports at the top of each HTML file:

```html
import 'https://esm.sh/@videojs/html@10.0.0-beta.6/video/player';
```

**To change the media source**, update the `SRC` constant in the `<script>` block of the relevant page. For `simple-hls-video`, the source must use CMAF/fMP4 segments — TS-based HLS streams are not supported.

**To add a new test page**, copy any existing page as a starting point and update the element imports and `SRC` as needed. Add a link to `index.html` so it shows up in the index.
