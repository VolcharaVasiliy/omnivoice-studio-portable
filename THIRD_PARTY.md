# Third-Party Credits

This project is a portable OmniVoice-based app built from upstream model,
UI, and runtime components. See the upstream projects below for their
respective licenses and usage terms.

## Core References

| Project | Link | Used For |
| --- | --- | --- |
| OmniVoice | https://github.com/k2-fsa/OmniVoice | Core TTS model and generation behavior. |
| OmniVoice model | https://huggingface.co/k2-fsa/OmniVoice | Pretrained model weights used by the backend. |
| OmniVoice HF Space | https://huggingface.co/spaces/k2-fsa/OmniVoice | Behavioral reference for the clone/design flow and output style. |
| OmniVoice Studio | https://github.com/debpalash/OmniVoice-Studio | Frontend and layout inspiration for the studio-style UI. |
| Whisper | https://github.com/openai/whisper | Local speech transcription fallback for reference audio. |

## Runtime and Build Stack

| Project | Link | Used For |
| --- | --- | --- |
| Python | https://www.python.org/ | Bundled backend runtime. |
| FastAPI | https://fastapi.tiangolo.com/ | HTTP API layer. |
| Uvicorn | https://www.uvicorn.org/ | ASGI server. |
| PyTorch | https://pytorch.org/ | Model inference runtime. |
| torchaudio | https://github.com/pytorch/audio | Audio I/O helpers. |
| Transformers | https://huggingface.co/docs/transformers | Model loading utilities. |
| Accelerate | https://huggingface.co/docs/accelerate | Device orchestration. |
| soundfile | https://python-soundfile.readthedocs.io/ | WAV output writing. |
| NumPy | https://numpy.org/ | Audio array handling. |
| React | https://react.dev/ | Frontend framework. |
| Vite | https://vite.dev/ | Frontend build and dev tooling. |
| Lucide | https://lucide.dev/ | UI icons. |

## Portable Binary Dependencies

| Project | Link | Used For |
| --- | --- | --- |
| ffmpeg | https://ffmpeg.org/ | Local audio conversion and media helpers. |
| Gyan.dev FFmpeg builds | https://www.gyan.dev/ffmpeg/builds/ | Portable Windows ffmpeg binaries used in the package. |

## Notes

- The packaged archive includes the local Python runtime, ffmpeg binaries, and
  cached OmniVoice/Whisper assets.
- This repository does not redistribute upstream model licenses; check each
  source project before redistributing.
- If you update the model, UI, or runtime stack, add the new upstream project
  here as well.
