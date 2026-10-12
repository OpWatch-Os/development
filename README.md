# OpWatch-Os development

Research and development for a **Wear OS 7 port to the OnePlus Watch 3 43 mm (OPWE242)**.

**Status: preparation and static analysis. There is no compiled, boot-tested, or installable ROM.** This repository contains original project documentation and a plan for the device port. Hardware support, bootloader unlocking, and recovery remain unverified.

## Current baseline

| Component | Verified baseline | Limitation |
| --- | --- | --- |
| Target device | OPWE242 / XK935 / project 24968; stock A.165, Android 14 / API 34 | Complete A.165 boot and partition images are unavailable |
| Running kernel | Linux 5.15.185-android14-11; ARM64, ARM32 compatibility, 4 KiB pages | No rebuilt kernel or module compatibility test |
| Official 43 mm source | A.123, Linux 5.15.167 | Older than the running A.165 kernel |
| Vendor sample | All 98 acquired ELF files are ARM32 | ARM64 processes cannot load the sampled ARM32 graphics drivers directly |
| Target reference | Google Wear OS 7 ARM64 emulator image, Android 17 / API 37 | Emulator binaries are not an OPWE242 hardware ROM; no ARM32 runtime in this image |
| Stock OTA reference | Original OPWE242 A.128 package acquired for offline analysis | Older build; acceptance by the current A.165 device is unverified |

The immediate work is to obtain matching A.165 stock inputs, establish a recoverable device test path, and resolve the vendor ABI and platform integration requirements. [Device status](docs/STATUS.md) separates observations from untested assumptions.

## Repositories

| Repository | Purpose |
| --- | --- |
| [manifests](https://github.com/OpWatch-Os/manifests) | Pinned source manifests and upstream provenance |
| [android_kernel_oneplus_sw5100](https://github.com/OpWatch-Os/android_kernel_oneplus_sw5100) | Official OnePlus kernel fork, 43 mm branch |
| [android_kernel_modules_and_devicetree_oneplus_sw5100](https://github.com/OpWatch-Os/android_kernel_modules_and_devicetree_oneplus_sw5100) | Matching official modules and device tree fork |
| [android_kernel_google_msm-extra](https://github.com/OpWatch-Os/android_kernel_google_msm-extra) | Selected Google SW5100 Android 15 QPR2 branch mirror, experimental reference |
| [android_device_oneplus_OPWE242](https://github.com/OpWatch-Os/android_device_oneplus_OPWE242) | Original device facts and architecture fragments |
| [android_vendor_oneplus_OPWE242](https://github.com/OpWatch-Os/android_vendor_oneplus_OPWE242) | Public vendor requirements descriptor; no proprietary files |

## Documentation

- [Roadmap](docs/ROADMAP.md): milestones and the evidence needed to complete each one.
- [Provenance](docs/PROVENANCE.md): upstream source revisions, archive hashes, and licensing boundaries.
- [Contributing](CONTRIBUTING.md): useful contributions and publication rules.

Kernel source and modules belong in separate upstream-preserving repositories. This repository does not bundle firmware, proprietary binaries, emulator images, device logs, or private capture data. It does not provide a build or flashing command yet.

Original project files are licensed under [Apache-2.0](LICENSE). Upstream kernel sources and third-party material retain their own licenses. OpWatch-Os is a community project and is not affiliated with OnePlus or Google.
