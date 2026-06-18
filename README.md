# Last Frame

A private, mobile-first video frame extractor that runs entirely in the browser. Choose a video, extract its final decodable frame, and download it as a full-resolution PNG.

![No backend](https://img.shields.io/badge/backend-none-17211b)
![Processing](https://img.shields.io/badge/processing-on--device-d8ff66)
![License](https://img.shields.io/badge/license-MIT-17211b)

## Features

- Fully client-side processing—videos are never uploaded
- Native video dimensions preserved in the exported image
- Lossless PNG output
- Mobile-first, responsive interface
- Tap-to-select and desktop drag-and-drop
- No framework, build tool, account, or server required

## Use it

Open `index.html` in a modern browser, or serve the directory locally:

```bash
python3 -m http.server 8080
```

Then visit `http://localhost:8080`.

1. Choose or drop a video.
2. Select **Extract last frame**.
3. Preview the result and select **Download full-quality PNG**.

## How it works

The browser loads the selected file through a temporary object URL, seeks to the final decodable moment, and draws that frame to a canvas at the video's native width and height. The canvas is encoded as a lossless PNG and exposed through a temporary local download URL.

No video or extracted image is sent across the network. Tailwind CSS is loaded from its CDN, so an internet connection is needed for styling unless the stylesheet is bundled locally.

## Quality and compatibility

The PNG keeps the decoded frame's original pixel dimensions and does not add JPEG compression. It cannot recover detail already removed by the video's codec. Exact frame seeking depends on the browser, container, and codec.

Format support also follows the browser. MP4 with H.264 and WebM usually provide the broadest compatibility; MOV support varies by device and codec.

## Tech

- HTML5 Video API
- Canvas API
- Blob and Object URL APIs
- Tailwind CSS Play CDN

## License

MIT
