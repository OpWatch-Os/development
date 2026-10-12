# OpWatch-Os development

Research and development for a **Wear OS 7 port to the OnePlus Watch 3 43 mm (OPWE242)**.

**Status: source organization, preparation and static analysis. There is no compiled, boot-tested, or installable ROM.** This repository contains original project documentation and a plan for the device port. Hardware support, bootloader unlocking, and recovery remain unverified.

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

The organization contains **27 repositories: 21 native GitHub forks, two
selected upstream Git mirrors and four original project repositories**. The
[complete repository index](docs/REPOSITORIES.md) lists each purpose, branch,
source revision and canonical upstream. Twenty Android platform components
have editable `opwatchos-17.0` branches based on the recorded Google Android
17 r1 commits; the rest of AOSP is acquired from upstream through the manifest.

| Repository | Purpose |
| --- | --- |
| [manifests](https://github.com/OpWatch-Os/manifests) | Pinned source manifests and upstream provenance |
| [android_kernel_oneplus_sw5100](https://github.com/OpWatch-Os/android_kernel_oneplus_sw5100) | Official OnePlus kernel fork, 43 mm branch |
| [android_kernel_modules_and_devicetree_oneplus_sw5100](https://github.com/OpWatch-Os/android_kernel_modules_and_devicetree_oneplus_sw5100) | Matching official modules and device tree fork |
| [android_kernel_google_msm-extra](https://github.com/OpWatch-Os/android_kernel_google_msm-extra) | Selected Google SW5100 Android 15 QPR2 branch mirror, experimental reference |
| [android_device_oneplus_OPWE242](https://github.com/OpWatch-Os/android_device_oneplus_OPWE242) | Original device facts and architecture fragments |
| [android_vendor_oneplus_OPWE242](https://github.com/OpWatch-Os/android_vendor_oneplus_OPWE242) | Public vendor requirements descriptor; no proprietary files |

## Acquire the Android source workspace

The AOSP `android-17.0.0_r1` manifest contains **1,087 projects**. The integrated
OpWatch manifest contains **1,089**: it substitutes twenty platform projects
without changing their paths and adds the device/vendor scaffolds. These are
source checkout manifests, not a complete OPWE242 build product.

With Git, Python 3 and the Android `repo` launcher installed, use a new Linux
directory on a filesystem that supports case-sensitive names and symlinks:

```sh
mkdir opwatch-aosp
cd opwatch-aosp
repo init -u https://github.com/OpWatch-Os/manifests -b main -m opwatch.xml
repo sync -c -j4
```

For the recorded twenty-component Google baseline, select the pinned overlay
instead of `opwatch.xml` in the initialization command:

```sh
repo init -u https://github.com/OpWatch-Os/manifests -b main -m opwatch-pinned.xml
```

The pinned overlay locks the twenty selected platform components and both
device/vendor scaffolds to recorded commits. Other AOSP projects retain the
official release tag; this is not an immutable lock of every build input. The default groups
omit three `notdefault` AOSP projects; use `-g all` with `repo init` to acquire
every project. After a successful sync, `repo manifest -r` can record the
resolved checkout. Linux sync and compilation remain to be performed.

After sync, create a topic branch for a selected project, for example:

```sh
repo start wifi-policy frameworks/base
cd frameworks/base
git remote get-url --push opwatch
```

For this example the push destination must be
`https://github.com/OpWatch-Os/android_platform_frameworks_base`. Verify it
before publishing, then review and commit the intended changes. To update the
editable organization branch, push the committed topic explicitly:

```sh
git push opwatch HEAD:refs/heads/opwatchos-17.0
```

This command targets `opwatchos-17.0`, rather than creating a remote branch
named after the local topic. It uses no force push. Other platform components
use their own project paths and repository URLs from the index.

Keep the [kernel source workspace](https://github.com/OpWatch-Os/manifests#acquisire-i-sorgenti-kernel)
separate from this Android workspace. The published OnePlus kernel and module
layout, toolchain and incomplete external inputs are documented by the
[manifests repository](https://github.com/OpWatch-Os/manifests).

## Documentation

- [Roadmap](docs/ROADMAP.md): milestones and the evidence needed to complete each one.
- [Provenance](docs/PROVENANCE.md): upstream source revisions, archive hashes, and licensing boundaries.
- [Repository index](docs/REPOSITORIES.md): all 27 repositories and twenty canonical Android platform baseline revisions.
- [Contributing](CONTRIBUTING.md): useful contributions and publication rules.

Kernel source and modules belong in separate upstream-preserving repositories. This repository does not bundle firmware, proprietary binaries, emulator images, device logs, or private capture data. The commands above acquire source; no complete device build or flashing command is provided.

Original project files are licensed under [Apache-2.0](LICENSE). Upstream kernel sources and third-party material retain their own licenses. OpWatch-Os is a community project and is not affiliated with OnePlus or Google.
