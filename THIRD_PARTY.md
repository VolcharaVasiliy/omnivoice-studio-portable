# Third-Party Credits

This portable build is assembled from the OmniVoice source tree plus the runtime and UI stack listed below.

## Core Project

| Project | Link | Use |
| --- | --- | --- |
| OmniVoice | https://github.com/k2-fsa/OmniVoice | Core TTS model, CLI tools, docs, and source code. |
| OmniVoice model | https://huggingface.co/k2-fsa/OmniVoice | Pretrained weights used by the portable build. |
| OmniVoice Studio frontend | https://github.com/debpalash/OmniVoice-Studio | Ready-made frontend source used as the bundled portable UI. |

## Runtime and UI Stack

| Project | Link | Use |
| --- | --- | --- |
| Python | https://www.python.org/ | Bundled runtime in `runtime\python311`. |
| PyTorch | https://pytorch.org/ | Main inference runtime. |
| torchaudio | https://github.com/pytorch/audio | Audio I/O and signal utilities. |
| Transformers | https://huggingface.co/docs/transformers | Model loading and generation helpers. |
| Accelerate | https://huggingface.co/docs/accelerate | Device and runtime orchestration. |
| Gradio | https://www.gradio.app/ | Studio UI layer. |
| FastAPI | https://fastapi.tiangolo.com/ | Backend HTTP API. |
| psutil | https://github.com/giampaolo/psutil | Process and system checks. |

## Audio and Data Helpers

| Project | Link | Use |
| --- | --- | --- |
| FFmpeg | https://ffmpeg.org/ | Bundled audio conversion runtime. |
| pydub | https://github.com/jiaaro/pydub | Audio manipulation helpers. |
| soundfile | https://python-soundfile.readthedocs.io/ | WAV and audio file handling. |
| NumPy | https://numpy.org/ | Numerical operations. |
| tensorboardX | https://github.com/lanpa/tensorboardX | Training and logging utilities. |
| WebDataset | https://github.com/webdataset/webdataset | Dataset pipeline support. |

## Optional Evaluation Stack in the Source Tree

These packages are referenced by the OmniVoice source tree for evaluation or extended workflows and are not required for the basic portable UI path.

| Project | Link | Use |
| --- | --- | --- |
| jiwer | https://github.com/jitsi/jiwer | WER evaluation. |
| librosa | https://librosa.org/ | Audio processing. |
| s3prl | https://github.com/s3prl/s3prl | Speech representation models. |
| FunASR | https://github.com/modelscope/FunASR | ASR support for evaluation workflows. |
| zhconv | https://github.com/gumblex/zhconv | Chinese character normalization. |
| zhon | https://github.com/tsroten/zhon | Chinese punctuation helpers. |
| Unidecode | https://github.com/avian2/unidecode | Unicode normalization helpers. |

## Packaging and Portability

| Project | Link | Use |
| --- | --- | --- |
| uv | https://docs.astral.sh/uv/ | Dependency and lockfile workflow in the source tree. |
| hatchling | https://hatch.pypa.io/ | Build backend declared in `pyproject.toml`. |
