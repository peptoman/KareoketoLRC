# Kareoketo LRC

Browser-only karaoke video → `.lrc` editor. The project follows the supplied specification: local video preview, heuristic white/yellow highlighting analysis, synchronized verification, metadata, manual timing correction, and LRC export. fileciteturn1file0L20-L39

## Run locally

```bash
npm install
npm run dev
```

Build with `npm run build` and preview with `npm run preview`.

## How it works

The first implementation samples the video through an HTML5 video element and Canvas, classifies bright/yellow pixels, groups likely highlight transitions, and presents them as editable lyric events. This is intentionally heuristic: the specification calls for transparent handling of imperfect detection and recommends MP4/H.264 and WebM first. fileciteturn1file2L374-L384

Normal line-level LRC is the export format. Metadata fields include Artist, Title, Album, Album Artist and Offset. fileciteturn1file1L250-L287

## Privacy

Video processing stays in the browser; no upload service is used. fileciteturn1file3L619-L627

## GitHub Pages

For a Vite deployment, set the Vite `base` to the repository path when deploying as a project page, then build and publish the `dist` directory using your preferred GitHub Pages workflow.

## Limitations

Automatic detection cannot reliably recover arbitrary lyric text from pixels without OCR/transcription data. The current implementation therefore generates editable placeholder events from detected highlight transitions rather than pretending to know unseen lyric words. Low-confidence results should be corrected in the editor. The requested product specification explicitly treats detection as heuristic and asks for manual correction. fileciteturn1file3L546-L583
