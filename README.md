# Babata

Offline screen OCR for Windows x64. Capture text, edit the result, and copy it automatically. Optional NVIDIA GPU acceleration is available as a separate download.

**[Download the latest Babata installer](https://github.com/kakdev10k/Babata-Releases/releases/latest)**

This public repository contains installers, checksums and release notes. Application source code is maintained privately.

## Install

1. Download `Babata-Setup-1.0.2-x64.exe` from the release assets and run it manually. Quit any running Babata instance first.
2. Launch Babata and complete Offline OCR setup. An internet connection is required for this initial setup.
3. Babata downloads its CPU runtime from Cloudflare R2 and the required OCR models directly from official Paddle sources. The installer includes neither runtime nor model weights. You do not need to install Python.
4. After verification and a recognition test, capture text with **Ctrl + Alt + O** or the floating button. OCR then works offline.

Chinese and English are the default configuration, including Simplified and Traditional Chinese. Japanese shares the same model pack. Korean and Thai recognition packs are optional downloads. Recognition can make mistakes; review important text.

## Application updates

Version 1.0.2 adds reviewed GPU runtime v2, background OCR model loading/warm-up, and a live backend dashboard. Animated icons, both notification sounds and their saved preferences are preserved. Stable releases can be detected and downloaded through **Settings -> General -> App Updates**; installation remains manual. The original v1.0.0 has no updater, so install the latest version manually once to get update checking. Reduced motion or missing/broken animation files use PNG safely.

## Optional GPU acceleration

Open **Settings → Advanced → OCR backend** after completing the base setup. Supported NVIDIA GPUs can download the optional **2.45 GiB** v2 runtime. It includes cuDNN 9.9.0.52 matching Paddle's binary build target. This backend requires compute capability 7.5 or newer and a compatible NVIDIA driver; actual native and recognition tests determine readiness. Installing the CUDA Toolkit is not required. Physical GPU tests used an RTX 4050 laptop, not every GPU/driver combination.

**Updating from an earlier GPU runtime:** click **Download GPU acceleration** to install v2. Previous runtime files are kept, existing models are reused, and CPU OCR stays available while GPU setup is pending. CPU-only users do not need a new runtime or model pack for this update.

Leave the processing device on **Automatic** to use the verified GPU runtime. **CPU only** is also available. GPU execution failures retry recognition on CPU and report the fallback. AMD and Intel GPU acceleration are not included in this release. The same OCR models are reused.

## Privacy and local data

Screenshots are processed locally. Babata does not keep screenshot history or send screenshots to an online OCR service. Clicking the Google Translate button explicitly opens the recognized text in your browser and shares that text with Google.

Runtimes, models and download caches are stored under `%LOCALAPPDATA%\Babata\`, outside the application directory. They are retained across application updates and uninstall for reuse. Preferences are stored under `%APPDATA%\Babata\`.

## Release information

The installer is unsigned. Validation was performed on the development Windows host; clean Windows VM certification is not claimed. Runtime downloads currently use Cloudflare's rate-limited r2.dev development endpoint; if a download fails, retry setup. A production runtime custom domain remains planned.

Each release includes an installer SHA-256 checksum and a small release manifest. Dependency notices are included with the application and runtime packages. [View the release history](CHANGELOG.md).
