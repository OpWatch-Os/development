# Device and port status

Snapshot: 12 October 2026. These are observations from the research workspace, not a compatibility guarantee or a release announcement.

## Device observations

| Property | Observed value |
| --- | --- |
| Device | OnePlus Watch 3 43 mm |
| Model / hardware / project | OPWE242 / XK935 / 24968 |
| Installed build | OPWE242_11_A.165 |
| Android / API | 14 / 34 |
| Kernel | 5.15.185-android14-11 |
| Kernel architecture | ARM64 |
| Compatibility configuration | CONFIG_COMPAT and CONFIG_COMPAT_BINFMT_ELF enabled |
| Kernel page size | 4 KiB |
| Advertised application ABI | armeabi-v7a, armeabi; no ARM64 application ABI advertised |
| Acquired vendor ELF sample | 98 files, all ELF32 / EM_ARM |
| Bootloader / verified boot | Locked / green in the observed stock state |

The kernel configuration was read from the running device. The architecture findings apply to the acquired sample; they do not prove that every component in the complete firmware has been inventoried.

## Material available for analysis

- Original files readable from the installed stock software, including configuration, framework, application, and selected vendor components. This is an incomplete file extraction, not a flashable partition backup.
- Official OnePlusOSS kernel and modules/device-tree sources for the 43 mm branch, published for A.123. Archive integrity has been checked.
- The original OPWE242 A.128 full OTA, with all 48 ZIP members passing CRC checks. Its boot-related images and six logical partition images were extracted or reconstructed for offline analysis. No complete `super` image was reconstructed.
- The official Wear OS 7 ARM64 emulator reference, identified as Android 17 / API 37. Static inspection established that the sampled image does not provide an ARM32 runtime.

The A.128 package has a mathematically valid embedded signature, but verification against the trust material acquired from A.165 does not pass. Authenticity for the current device, installation eligibility, downgrade support, and restoration capability have not been established. A.128 images must not be treated as matching A.165 inputs.

## Remaining blockers

1. **Matching stock inputs:** complete OPWE242 A.165 boot images, partition geometry, AVB metadata, and protected HAL/module components are missing. Shell access cannot read the protected partitions examined. Root access has not been obtained.
2. **Device test and restoration:** an OPWE242 bootloader unlock procedure and a working stock restoration path have not been demonstrated. A visit to a bootloader or emergency-download mode does not establish write or recovery access.
3. **Vendor ABI:** the sampled EGL, Vulkan, and mapper implementations are ARM32. A future ARM64 graphics process cannot load them directly. A multilib runtime alone does not resolve these consumers and their dependencies.
4. **Kernel match:** available A.123 sources use 5.15.167, while the running A.165 kernel is 5.15.185. Matching module ABI/KMI, configuration, packaging, and source changes have not been verified.
5. **Platform integration:** a complete Android device/product configuration, VINTF validation, SELinux policy integration, linker namespaces, and OEM display, vibration, sensor, and MCU framework adaptation remain to be developed.
6. **Wear platform availability:** an emulator reference and Android platform source do not supply a complete, redistributable Wear OS hardware product. Availability and permitted use of each required component must be established separately.
7. **Build environment:** a case-sensitive Linux/POSIX workspace, compatible kernel toolchain and dependencies, and a complete platform build have not been validated.

The public kernel tree contains 13 pairs of paths that collide on a case-insensitive filesystem. Preserve source paths, symlinks, and POSIX permissions when preparing a build workspace.

## Validation completed and not completed

Archive hashes, source revisions, selected file metadata, kernel configuration, sampled ELF architectures, and OTA ZIP integrity have been checked. Framework and vendor comparisons are static analysis; they are not `checkvintf`, boot tests, hardware tests, or a successful ROM build.

No custom kernel or ROM has been compiled, booted, or flashed. No verified root method or custom-ROM recovery process has been produced. The latest available official OTA is still unknown: server metadata and bounded device observations did not establish a newer downloadable package. Lack of a captured OTA URL does not demonstrate that an update does not exist.

The 47 mm OPWWE251 dump is a separate model reference. Its binaries, partition images, and device-tree overlays have no established compatibility with OPWE242.
