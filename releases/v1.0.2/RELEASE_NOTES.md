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
