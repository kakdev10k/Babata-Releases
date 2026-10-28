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
