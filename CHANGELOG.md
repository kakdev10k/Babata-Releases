# Release history

## 1.0.4 - 2026-10-29

Verified backend download-cache cleanup after installation and at engine readiness. New GPU downloads/repairs use runtime v3; compatible installed runtimes, CPU OCR and models remain available. Resumable partial transfers are preserved.

[Release notes and installer](https://github.com/kakdev10k/Babata-Releases/releases/tag/v1.0.4)

## 1.0.3 - 2026-10-28

Babata OCR v1.0.3 improves NVIDIA GPU compatibility, including the tested RTX 5070 Ti.

### What's changed

- Select a reviewed GPU runtime by actual compute capability. RTX 50-series capability 12.0 uses CUDA 12.9 runtime v3 with native Blackwell support and cuDNN 9.9.0.52.
- Keep compatible installed CUDA 12.6 v2 or CUDA 12.9 v3 runtimes. RTX 20/30/40 users with a working runtime do not need to replace it for this update.
- Check the worker's actual GPU capability and compiled targets before executing CUDA kernels. Unsupported architectures keep CPU OCR available.
- Retain precise, bounded GPU failure stages and error codes after CPU fallback. Initialization with empty or incorrect warm-up recognition cannot mark the GPU ready.

### Install or update

Download **Babata-Setup-1.0.3-x64.exe**, quit Babata from the tray, and run the installer manually. Choose the existing installation folder when updating.

The installer includes neither OCR runtimes nor model weights. Existing compatible CPU runtimes and models are reused. No new model download is required by this update.

**RTX 50-series users:** open **Settings → Advanced**, download the optional **3.10 GiB** GPU runtime, and wait for validation. Confirm **GPU Inference Active**, CUDA **12.9**, and loaded cuDNN **9.9.0** in Advanced Details. A compatible NVIDIA driver is required; the CUDA Toolkit is not required separately.

Existing compatible RTX 20/30/40 installations continue using their verified runtime. CPU OCR stays available if optional GPU installation or validation fails. Previous components are kept until a replacement passes validation.

### Verification and limitations

- Local automated native and OCR testing used an RTX 4050 laptop GPU. The affected RTX 5070 Ti passed the portable test kit on the user's other PC, and the user confirmed accurate normal OCR results. This is not certification of every GPU or driver.
- AMD and Intel adapters use CPU OCR with the current backend. Other unreviewed NVIDIA architectures are not promised GPU support.
- CPU runtime, model catalogs, official upstream model downloads, startup warming, floating animations, both sounds, automatic copying, shortcuts, and Google Translate handoff are preserved.
- R2 hosts runtime packages and runtime metadata only. Model weights download directly from the reviewed official Paddle sources.
- The Windows installer is unsigned. Keep normal Windows security protections enabled. Installer execution and installation remain manual; clean-VM and installed-version upgrade execution are not claimed.

## 1.0.2 - 2026-10-28

Babata OCR v1.0.2 improves GPU runtime compatibility, OCR startup, and backend status reporting.

### What's changed

- **GPU runtime v2:** the optional NVIDIA runtime includes cuDNN 9.9.0.52, matching Paddle's reported 9.9.0 build target. Babata checks the actual loaded library, runs CUDA validation, and verifies both OCR predictors before showing GPU inference as active.
- **Faster captures after startup:** OCR models load and warm up in the background. Captures made during initialization wait for the same engine; later captures reuse the ready worker.
- **Clearer GPU diagnostics:** compatible NVIDIA devices are evaluated by capability and actual inference tests. A detection or runtime error is not automatically described as an outdated driver. CPU fallback remains available.
- **Compact backend dashboard:** Settings → Advanced now shows live readiness dots for the device, engine, runtime, models, and GPU inference. Technical information is under Advanced Details. Installation percentages reflect the actual download, extraction, or verification stage.
- **Current verification messages:** successful recognition replaces pending-verification text. Genuine compatibility warnings remain visible.

### Install or update

Download **Babata-Setup-1.0.2-x64.exe**. Quit Babata from the tray and run the installer manually, choosing the existing installation location when updating. Settings and OCR components remain outside the application installation.

**Existing CPU users:** the compatible CPU runtime and OCR models are reused; no new model pack is required for this update.

**Existing GPU users:** open **Settings → Advanced → OCR backend**, then **Download GPU acceleration** to obtain the reviewed v2 runtime, approximately **2.45 GiB**. The previous GPU runtime files are retained. CPU OCR stays available while GPU setup is pending. After installation and verification, use Automatic mode and confirm **GPU Inference Active** and **cuDNN loaded: 9.9.0** in Advanced Details.

The installer bundles neither OCR runtimes nor model weights. Cloudflare R2 hosts runtime packages and metadata only. OCR models continue downloading directly from the reviewed official Paddle sources and are reused when compatible. Optional Korean/Thai language packs remain separate downloads.

### Compatibility and limitations

- NVIDIA CUDA acceleration requires compatible hardware, compute capability 7.5 or newer, and a compatible NVIDIA driver. The CUDA Toolkit does not need to be installed separately. Detection alone does not establish compatibility; Babata validates actual inference. Physical testing for this release used an RTX 4050 laptop GPU, not every supported GPU/driver combination.
- AMD and Intel graphics use CPU OCR with this backend. GPU initialization failures can fall back to CPU.
- The Windows installer is unsigned. Keep normal Windows security protections enabled. Update detection and verified downloads are supported; installer execution remains manual.
- Installed-version upgrade execution and clean-VM testing are not claimed. Multi-monitor/DPI and real sleep/lock coverage remain limited.
- Google Lens remains unavailable. Floating animations, both notification sounds, automatic copying, shortcuts, and explicit Google Translate handoff are preserved.
- The runtime host remains the existing r2.dev endpoint, which has service rate limits.

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
