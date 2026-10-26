# Release history

## 1.0.0 — 2026-10-27

First Windows x64 release.

- Lightweight installer; CPU/GPU runtimes and OCR model weights are not bundled.
- First-launch setup downloads the CPU runtime from Cloudflare R2 and required models directly from official Paddle endpoints, with integrity checks, progress, retry and resume.
- Chinese and English OCR, including Simplified and Traditional Chinese; Japanese uses the shared recognizer. Korean and Thai are optional downloads.
- Optional NVIDIA GPU runtime, Automatic/CPU-only selection and reported CPU fallback.
- Floating capture button, global shortcut, editable results and automatic copying.
- Google Translate handoff for explicitly selected result text.
- Local preferences, themes, startup settings and tray controls.

The installer is unsigned. Clean Windows VM, physical multi-monitor and mixed-DPI coverage remains incomplete. Google Lens is unavailable. The current runtime host uses a rate-limited r2.dev endpoint.
