# Indica Anime Us — Project Design Draft

This is a planning note for the separate `indica-anime-us` project. It is not a product feature of Open-GenAi-Repo and should be copied into that repository only if explicitly requested. The planned app converts user-owned comic page batches into an editable anime video workflow: panel segmentation → OCR/dialogue extraction → character/scene continuity → storyboards → shot animation → Hindi/English voices and subtitles → final FFmpeg assembly.

## Inspirations
- `https://github.com/geeklee/srt-whiteboard-animation`: adopt the concept of timeline/SRT-driven rendering and editable timing. Do not copy implementation without reviewing its license.
- `https://github.com/Sharmapank-j/Open-GenAi-Repo`: adopt the idea of modular media-provider adapters, explicit local inference engines, model capability metadata, submit/poll/error normalization, durable generation history, and settings-based provider configuration.

## Offline-first target
Local mode must not call hosted APIs. CPU-capable operations: import files, order pages, detect/crop panels using OpenCV, OCR through Tesseract/PaddleOCR if installed, dialogue editing, basic multilingual subtitles, pan/zoom motion-comic rendering, FFmpeg export, SRT/VTT export. Optional local visual reasoning, image generation and TTS need separately installed models and hardware; report capability state honestly. Hosted anime video generation is opt-in, metered and isolated behind adapters.

## MVP acceptance
1. Import multiple JPG/PNG/PDF pages, reorder pages, and create a project.
2. Detect panels; manually split/merge, correct order and reading direction.
3. OCR Hindi/English text when the selected OCR engine supports the script; preserve original text and editable translation.
4. Edit dialogue, speaker, timing and language; export/import SRT/VTT.
5. Generate a local motion-comic MP4 using transitions, pans/zooms, subtitles, optional locally available TTS and music.
6. Project assets and cache remain on disk; no network use in strict offline mode.
7. Optional provider adapters normalize job submission, polling, cancellation, retry, cost/availability, asset inputs and output URLs.
8. Unit/integration tests, Windows PowerShell bootstrap, Docker optional, documented setup and data/privacy controls.

This note is intentionally a draft. The final product repo should own its docs and license after repository creation.