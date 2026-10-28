# Babata

Offline screen OCR for Windows x64. Capture text, edit the result, and copy it automatically. Optional NVIDIA GPU acceleration is available as a separate download.

**[Download the latest Babata installer](https://github.com/kakdev10k/Babata-Releases/releases/latest)**

This public repository contains installers, checksums and release notes. Application source code is maintained privately.

## Install

1. Download `Babata-Setup-1.0.3-x64.exe` from the release assets and run it manually. Quit any running Babata instance first.
2. Launch Babata and complete Offline OCR setup. An internet connection is required for this initial setup.
3. Babata downloads its CPU runtime from Cloudflare R2 and the required OCR models directly from official Paddle sources. The installer includes neither runtime nor model weights. You do not need to install Python.
4. After verification and a recognition test, capture text with **Ctrl + Alt + O** or the floating button. OCR then works offline.

Chinese and English are the default configuration, including Simplified and Traditional Chinese. Japanese shares the same model pack. Korean and Thai recognition packs are optional downloads. Recognition can make mistakes; review important text.

## Application updates

Version 1.0.3 adds architecture-aware NVIDIA runtime selection, including CUDA 12.9 v3 for the tested RTX 5070 Ti. Compatible installed runtimes are reused. Background OCR warm-up, the live backend dashboard, animations, both sounds, and saved preferences are preserved. Stable releases can be detected and downloaded through **Settings -> General -> App Updates**; installation remains manual. The original v1.0.0 has no updater, so install the latest version manually once to get update checking. Reduced motion or missing/broken animation files use PNG safely.

## Optional GPU acceleration

**GPU runtime v1 has been retired from hosting.** Users of Babata v1.0.0 or v1.0.1 must update to v1.0.2 or later before downloading or repairing GPU acceleration. Already installed local runtimes continue to work. The shared CPU runtime remains hosted and is still required by current releases.

Open **Settings -> Advanced -> OCR backend** after base setup. Babata selects a reviewed NVIDIA runtime by compute capability: CUDA 12.6 v2 (about **2.45 GiB**) for reviewed older architectures, or CUDA 12.9 v3 (about **3.10 GiB**) for Blackwell capability 12.0. The catalog covers native targets 7.5, 8.0, 8.6, 8.9, and 12.0, with compatible same-major higher-minor targets followed by real validation. Unreviewed architectures keep CPU OCR available. Installing the CUDA Toolkit is not required; a compatible NVIDIA driver is required.

Existing compatible v2 or v3 installations are reused. RTX 50-series users should update to **v1.0.3**, then download the offered GPU runtime and wait for validation. CPU runtime and existing compatible model downloads are unchanged. Previous runtime files remain until a replacement passes verification.

Babata checks actual worker build targets, runs a CUDA kernel, validates both OCR predictors, and verifies recognition before showing **GPU Inference Active**. Local automated tests used an RTX 4050 laptop; an RTX 5070 Ti user separately confirmed successful setup and accurate normal OCR. Every GPU/driver combination is not certified.

Leave the processing device on **Automatic** to use verified acceleration, or select **CPU only**. GPU failures can fall back to CPU and retain diagnostic details. AMD and Intel adapters use CPU OCR with this backend. GPU and CPU share the same OCR models.

## Privacy and local data

Screenshots are processed locally. Babata does not keep screenshot history or send screenshots to an online OCR service. Clicking the Google Translate button explicitly opens the recognized text in your browser and shares that text with Google.

Runtimes, models and download caches are stored under `%LOCALAPPDATA%\Babata\`, outside the application directory. They are retained across application updates and uninstall for reuse. Preferences are stored under `%APPDATA%\Babata\`.

## Release information

The installer is unsigned. Validation was performed on the development Windows host; clean Windows VM certification is not claimed. Runtime downloads currently use Cloudflare's rate-limited r2.dev development endpoint; if a download fails, retry setup. A production runtime custom domain remains planned.

Each release includes an installer SHA-256 checksum and a small release manifest. Dependency notices are included with the application and runtime packages. [View the release history](CHANGELOG.md).
