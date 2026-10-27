# Release history

## 1.0.1 ? 2026-10-28

Babata OCR v1.0.1 improves the floating capture icon and adds notification sounds and application update checks.

### What's new

- **Animated floating icon:** transparent WebM idle, hover, click, processing and success states. **Settings -> General -> Floating Icon Animation** switches instantly between animation and the original PNG, and remembers your choice. Missing/broken media and reduced motion use PNG safely.
- **More reliable floating icon:** restores its visibility and on-top preference after relevant window/display/power events, preserves dragging, and fixes a case where saving settings during OCR left it hidden.
- **Notification sounds:** capture and successful OCR sounds, controlled by **General -> Notification Sounds**. Errors, cancellation and empty OCR do not play success audio.
- **App updates:** automatic stable-release checks, manual checking, an update notification deferred until OCR is idle, download progress, integrity checking and retry/resume. Installation is manual; Babata does not execute an installer or restart automatically.
- **Windows startup retention:** restores a saved startup opt-in when the replacement packaged app launches.

### Install or update

Download **Babata-Setup-1.0.1-x64.exe**. Quit Babata from the tray, run the installer manually and choose the existing installation location when updating. Settings and downloaded OCR components are stored outside the application installation.

**The original v1.0.0 app does not include this updater. Install v1.0.1 manually once to receive the new update-checking functionality.**

The installer contains no OCR runtime or model weights. Existing compatible components are reused. On a new PC, setup downloads the runtime separately from Babata's runtime host and the required models directly from official Paddle sources. Optional GPU acceleration remains a separate download.

### Known limitations

- The Windows installer is unsigned; normal Windows security prompts may appear. Do not disable Windows security protections.
- Automatic installer execution and real installed-version-to-new-version upgrade testing are deferred for this release. The supported update workflow is detect, notify, download and install manually.
- Google Lens remains unavailable; offline PaddleOCR and explicit Google Translate handoff remain available.
- Physical multi-monitor/mixed-DPI, real sleep/resume and clean-VM coverage remains incomplete. Secure desktop/UAC and exclusive fullscreen are not bypassed.
- Reduced-motion settings intentionally show PNG. The click animation is a brief cue before the icon hides for screenshot selection.
- The existing runtime host still uses its rate-limited r2.dev endpoint; runtime/model distribution versions and locations are unchanged.

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
