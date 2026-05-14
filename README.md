# OmniVoice Studio Portable

Portable OmniVoice Studio-style app for local voice cloning and voice design.
It is built to be extracted into any folder and launched with one double-click.

## Download

Latest release download:

 [Buzzheavier mirror](https://buzzheavier.com/qhvr22lgxpvt)

Thanks to Buzzheavier for free hosting of large files.
For faster downloads without interruptions or ads, the releases may also
include `BuzzheavierTool.exe` as a companion downloader for Buzzheavier-hosted
files. To download through my tools you can insert the ID `qhvr22lgxpvt`.

Alt Google Drive:

[Google Drive 001](https://drive.google.com/file/d/1QQVv1HJour3Q2g3GuTF9qcYKflgFQWc8/view?usp=sharing)

[Google Drive 002](https://drive.google.com/file/d/1cKZP_62tAlcL5AHjqYcnQSDOf4I_Ph30/view?usp=sharing)

Split, because the file is too big for a free google drive, sorry :3
But it will always be available, since buzz has a shelf life, and I don't always have time to upload the archive on time.
You should have downloaded 7z, put both archives in the same folder, then run `7z x omnivoice-studio-portable-split.7z.001`.

## Quick Start

1. Download the release archive or clone this repo.
2. Extract it anywhere you want.
3. Double-click `start.bat`.
4. Wait for the first model load to finish.
5. The browser opens automatically at `http://127.0.0.1:8000`.

## What You Get

- FastAPI backend that serves OmniVoice synthesis.
- React + Vite frontend inspired by OmniVoice Studio and the Hugging Face demo flow.
- Local Whisper transcription for reference audio.
- Local portable ffmpeg binaries.
- Local Python runtime inside the app folder.

## Portable Layout

Everything lives next to the app, not in a fixed drive location:

- `runtime\` - bundled Python and virtual environment
- `cache\` - Hugging Face, Whisper, and other model caches
- `tools\ffmpeg\` - portable ffmpeg and ffprobe
- `data\` - generated audio and uploaded reference clips

This means you can unpack the app into any directory and run it without
changing paths manually.

## GPU and CPU Behavior

The launcher detects NVIDIA hardware and installs a CUDA-enabled PyTorch build
when available. On NVIDIA systems, OmniVoice runs on GPU automatically.

If no supported GPU is available, the app falls back to CPU mode instead of
failing.

## First Launch

The first run downloads OmniVoice weights and any missing model assets into the
local `cache\` folder. That can take a while, especially on the first launch.
Later launches reuse the local cache.

## Scripts

- `start.bat` - one-click launcher for end users.
- `start.ps1` - starts the backend, waits for health, then opens the browser.
- `stop.ps1` - stops the backend and clears stale listeners on port `8000`.
- `setup-portable.ps1` - bootstrap script for building or refreshing the local runtime.
- `package-portable.ps1` - creates the distributable `.7z` archive.

## Build From Source

If you are rebuilding the portable package on a maintainer machine, you can
override helper tool locations with environment variables:

- `OMNIVOICE_PYTHON_SOURCE`
- `OMNIVOICE_NODE_HOME`
- `OMNIVOICE_SEVENZIP`

Example:

```powershell
$env:OMNIVOICE_PYTHON_SOURCE = 'F:\DevTools\Python311'
$env:OMNIVOICE_NODE_HOME = 'F:\DevTools\Portable\NodeJS'
powershell -NoProfile -ExecutionPolicy Bypass -File .\setup-portable.ps1
```

## Environment Variables

Useful runtime variables:

- `OMNIVOICE_MODEL` - model repo or checkpoint, defaults to `k2-fsa/OmniVoice`
- `OMNIVOICE_ASR_MODEL` - ASR model used for reference transcription
- `OMNIVOICE_DATA_DIR` - base folder for uploads and generated files
- `OMNIVOICE_OUTPUT_DIR` - generated audio folder
- `OMNIVOICE_UPLOAD_DIR` - uploaded reference audio folder
- `OMNIVOICE_CACHE_DIR` - local cache root

## Notes

- Clone mode accepts a reference clip and optional transcript.
- Design mode uses the voice-attribute grammar from the HF demo style flow.
- Auto mode generates without clone or instruction prompts.
- The UI, backend, and caches are all relative to the extracted folder.

## Troubleshooting

- If the browser does not open, run `start.ps1` manually and check the logs in
  `runtime\backend.err.log`.
- If port `8000` is busy, `stop.ps1` clears the stale process and you can start
  again.
- If first launch is slow, it is usually model download or cache warmup, not a
  broken install.
