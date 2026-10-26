# Babata

Offline screen OCR for Windows x64. Capture text, edit the result, and copy it automatically. Optional NVIDIA GPU acceleration is available as a separate download.

**[Download the latest Babata installer](https://github.com/kakdev10k/Babata-Releases/releases/latest)**

This public repository contains installers, checksums and release notes. Application source code is maintained privately.

## Install

1. Download `Babata-Setup-1.0.0-x64.exe` from the release assets and run it.
2. Launch Babata and complete Offline OCR setup. An internet connection is required for this initial setup.
3. Babata downloads its CPU runtime from Cloudflare R2 and the required OCR models directly from official Paddle sources. The installer includes neither runtime nor model weights. You do not need to install Python.
4. After verification and a recognition test, capture text with **Ctrl + Alt + O** or the floating button. OCR then works offline.

Chinese and English are the default configuration, including Simplified and Traditional Chinese. Japanese shares the same model pack. Korean and Thai recognition packs are optional downloads. Recognition can make mistakes; review important text.

## Optional GPU acceleration

Open **Settings → Advanced → GPU acceleration** after completing the base setup. Supported NVIDIA GPUs can download the optional **2.26 GiB** runtime. This build requires compute capability 7.5 or newer and Windows driver 561 or newer. A compatible NVIDIA driver is required; installing the CUDA Toolkit is not required.

Leave the processing device on **Automatic** to use the verified GPU runtime. **CPU only** is also available. GPU execution failures retry recognition on CPU and report the fallback. AMD and Intel GPU acceleration are not included in this release. The same OCR models are reused.

## Privacy and local data

Screenshots are processed locally. Babata does not keep screenshot history or send screenshots to an online OCR service. Clicking the Google Translate button explicitly opens the recognized text in your browser and shares that text with Google.

Runtimes, models and download caches are stored under `%LOCALAPPDATA%\Babata\`, outside the application directory. They are retained across application updates and uninstall for reuse. Preferences are stored under `%APPDATA%\Babata\`.

## Release information

The installer is unsigned. Validation was performed on the development Windows host; clean Windows VM certification is not claimed. Runtime downloads currently use Cloudflare's rate-limited r2.dev development endpoint; if a download fails, retry setup. A production runtime custom domain remains planned.

Each release includes an installer SHA-256 checksum and a small release manifest. Dependency notices are included with the application and runtime packages. [View the release history](CHANGELOG.md).
