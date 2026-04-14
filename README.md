# OmniVoice Studio Portable

Portable Windows package for OmniVoice Studio, built from open-source components and bundled so it runs out of the box after extraction.

[Download the archive on BuzzHeavier](https://buzzheavier.com/4g92h9spsvue)

Thanks to BuzzHeavier for free file hosting.

## What This Build Includes

- Local Studio-style web UI for voice clone and voice design.
- FastAPI backend in `studio_api.py`.
- Bundled Python runtime in `runtime\python311`.
- Bundled FFmpeg runtime in `tools\ffmpeg`.
- Preloaded caches and portable paths so the app can run without a separate install.

## Requirements

- Windows 10 or Windows 11.
- A writable local drive for extraction.
- NVIDIA CUDA is recommended for best performance.
- AMD GPUs and CPU fallback are supported, but slower.

## How To Run

1. Extract the archive to a local folder on Windows.
2. Start the app with `start-ui.cmd`.
3. Open the local UI at `http://127.0.0.1:8000`.
4. Stop it with `stop-ui.cmd`.

The `.cmd` wrappers call the PowerShell entry points:

- `start-ui.cmd` -> `start-ui.ps1`
- `stop-ui.cmd` -> `stop-ui.ps1`

## How It Works

1. `start-ui.cmd` launches the portable runtime.
2. On first launch, `repair-runtime.ps1` rewrites runtime-local paths so the bundled environment works from its new location.
3. `studio_api.py` starts the backend API and serves the bundled frontend.
4. `studio_app.py` provides the Gradio-based studio interface.
5. Generated audio is written to `out\`, while reference inputs are stored under `input\profiles\`.

## Notes

- This package is focused on voice clone and voice design workflows.
- Video dubbing is not included in this portable build.
- Windows users do not need any extra installer beyond the archive itself.
- If your GPU is not CUDA-capable, the app still runs, but generation will be slower.

## Portable Layout

- `input\profiles` - reference audio for saved voice profiles
- `out` - generated WAV files
- `cache` - local model and framework caches
- `frontend` - the bundled frontend source and build output
- `runtime\python311` - portable Python runtime
- `tools\ffmpeg` - bundled FFmpeg binaries

## Credits

All third-party projects used here are listed in [THIRD_PARTY.md](THIRD_PARTY.md).

