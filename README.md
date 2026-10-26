# multimeter

A studio-style audio analyzer in a single HTML file. No install, no build, no dependencies: open it in a browser, load an audio or video file and four modules measure it in real time.

**Try it:** https://saverio-moretti-dev.github.io/multimeter/ (a demo track is preloaded; press play).

## What it does
- **Levels**: L/R and Mid/Side meters, loudness in LUFS.
- **Spectrum analyzer**: FFT over frequency.
- **Stereo field**: lissajous, polar view, correlation.
- **Spectrogram**: 2D and 3D, over time.
- Timeline with waveform, zoom up to 40×, loop region with draggable handles.
- Configurable layout and colors, presets, video export of the visualizers synced to the audio.
- Audio and video files (MP3, WAV, FLAC, AAC, MP4, WebM…); from a video only the audio track is used. Drag & drop works.

## How it works
Everything runs in the page with the **Web Audio API**: the file is decoded in the browser, the channels are split and analysed with FFT in time and frequency, and every graph is drawn on **Canvas**. Nothing is uploaded anywhere. Plain HTML, CSS and JavaScript, one file (`index.html`).

## Run locally
```
git clone https://github.com/saverio-moretti-dev/multimeter && cd multimeter
python3 -m http.server 8080    # then open http://127.0.0.1:8080
```
Opening `index.html` directly also works; the preloaded demo track needs the local server.

Full guide to every control (Italian): [`LEGGIMI.md`](LEGGIMI.md).

Demo track: «In my head (mix)» by SEM Brana, included for the demo only.

---

## Italiano
Analizzatore audio da studio in un solo file HTML, senza installazione: carichi un file audio o video e quattro moduli lo misurano in tempo reale (livelli L/R e Mid/Side con LUFS, analizzatore di frequenze, campo stereo, spettrogramma 2D e 3D). Tutto gira nel browser con la Web Audio API e Canvas, niente viene caricato in rete. Guida completa: [`LEGGIMI.md`](LEGGIMI.md).
