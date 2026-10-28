# Babata

Offline screen OCR for Windows x64. Capture text, edit the result, and copy it automatically. Optional NVIDIA GPU acceleration is available as a separate download.

**[Download the latest Babata installer](https://github.com/kakdev10k/Babata-Releases/releases/latest)**

This public repository contains installers, checksums and release notes. Application source code is maintained privately.

## Install

1. Download `Babata-Setup-1.0.4-x64.exe` from the release assets and run it manually. Quit any running Babata instance first.
2. Launch Babata and complete Offline OCR setup. An internet connection is required for this initial setup.
3. Babata downloads its CPU runtime from Cloudflare R2 and the required OCR models directly from official Paddle sources. The installer includes neither runtime nor model weights. You do not need to install Python.
4. After verification and a recognition test, capture text with **Ctrl + Alt + O** or the floating button. OCR then works offline.

Chinese and English are the default configuration, including Simplified and Traditional Chinese. Japanese shares the same model pack. Korean and Thai recognition packs are optional downloads. Recognition can make mistakes; review important text.

## Application updates

Version 1.0.4 removes verified backend download archives after successful installation and recognition validation, and cleans eligible installed-component caches at startup. New GPU downloads and repairs use runtime v3; compatible installed runtimes are reused. Partial transfers and installed runtimes/models are preserved. Check **Settings -> General -> App Updates** to download the update, then quit Babata and install manually. The original v1.0.0 requires a manual update to gain update checking. Animations, notification sounds, OCR warm-up and saved preferences are preserved.

## Optional GPU acceleration

**GPU runtime v1 has been retired from hosting.** Users of Babata v1.0.0 or v1.0.1 must update to v1.0.2 or later before downloading or repairing GPU acceleration. Already installed local runtimes continue to work. The shared CPU runtime remains hosted and is still required by current releases.

Open **Settings -> Advanced -> OCR backend** after base setup. In v1.0.4, new NVIDIA GPU installations and repairs use CUDA 12.9 runtime v3 (about **3.10 GiB**), covering reviewed native targets 7.5, 8.0, 8.6, 8.9 and 12.0, followed by actual inference validation. Compatible installed v2/v3 runtimes remain reusable. Unreviewed architectures retain CPU OCR. A compatible NVIDIA driver is required; installing the CUDA Toolkit is unnecessary. CPU runtime and model sources are unchanged. GPU v2 hosting has not been retired by this publication.

Babata checks actual worker build targets, runs a CUDA kernel, validates both OCR predictors, and verifies recognition before showing **GPU Inference Active**. Local automated tests used an RTX 4050 laptop; an RTX 5070 Ti user separately confirmed successful setup and accurate normal OCR. Every GPU/driver combination is not certified.

Leave the processing device on **Automatic** to use verified acceleration, or select **CPU only**. GPU failures can fall back to CPU and retain diagnostic details. AMD and Intel adapters use CPU OCR with this backend. GPU and CPU share the same OCR models.

## Privacy and local data

Screenshots are processed locally. Babata does not keep screenshot history or send screenshots to an online OCR service. Clicking the Google Translate button explicitly opens the recognized text in your browser and shares that text with Google.

Runtimes, models and download caches are stored under `%LOCALAPPDATA%\Babata\`, outside the application directory. They are retained across application updates and uninstall for reuse. Preferences are stored under `%APPDATA%\Babata\`.

## Release information

The installer is unsigned. Validation was performed on the development Windows host; clean Windows VM certification is not claimed. Runtime downloads currently use Cloudflare's rate-limited r2.dev development endpoint; if a download fails, retry setup. A production runtime custom domain remains planned.

Each release includes an installer SHA-256 checksum and a small release manifest. Dependency notices are included with the application and runtime packages. [View the release history](CHANGELOG.md).
