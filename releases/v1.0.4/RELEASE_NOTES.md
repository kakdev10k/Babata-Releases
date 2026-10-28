Babata OCR v1.0.4 consolidates new NVIDIA GPU downloads onto runtime v3 and reduces backend download-cache storage.

### Changes

- New optional GPU installations and repairs use the reviewed CUDA 12.9 v3 runtime for compatible NVIDIA architectures, including the reviewed RTX 20/30/40/50 targets. Compatible already installed v2 runtimes remain usable; updating the application alone does not force a replacement download.
- After a CPU runtime, language pack, or GPU runtime passes installation and recognition validation, Babata removes its cached archives, runtime parts, assembly copies, and downloader metadata.
- On startup, Babata also cleans eligible cached downloads belonging to verified installed components. Resumable partial transfers, files held by ongoing setup, and unknown cache files remain available for retry. Cleanup does not remove installed runtimes, models, preferences, or component receipts.
- Cleanup uses bounded file deletion. If Windows or antivirus prevents removing a cache file, installed OCR remains ready and cleanup can retry on a later launch. No security protection is disabled.

The GPU v3 cache can otherwise contain approximately **6.20 GiB** of ZIP plus transfer parts, separate from its installed runtime. Actual space recovered depends on which cached files exist and whether disk data is shared.

### Installation and runtime hosting

Download **Babata-Setup-1.0.4-x64.exe**, quit Babata from the tray, and install manually. The installer is unsigned and includes neither OCR runtimes nor model weights. Keep normal Windows security protections enabled.

The CPU runtime remains required and hosted. Existing compatible models are reused; new language models still download directly from reviewed official Paddle sources. The v3 GPU runtime is about **3.10 GiB** and still requires compatible hardware/drivers and successful actual inference validation. AMD/Intel adapters use CPU OCR with this backend.

Older app versions retain their own bundled runtime selection. Before downloading or repairing GPU acceleration after any future v2 hosting retirement, update those applications to v1.0.4 or later. Already installed compatible v2 files can continue working locally.

### Verification limits

Automated native execution used the local RTX 4050. The unchanged v3 runtime previously passed user-confirmed RTX 5070 Ti setup and accurate OCR; this release is not physical certification of every adapter or driver. Installer execution, a real installed-version upgrade, and clean-VM certification are not claimed. Existing floating animations, sounds, OCR, automatic copying, shortcuts, and app update checks are preserved.
