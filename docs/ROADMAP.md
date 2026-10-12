# Roadmap

This is an evidence-driven plan, not a delivery schedule. A milestone is complete only when its listed result can be reviewed and reproduced.

## 1. Establish the stock baseline

- Obtain original stock material matching OPWE242 A.165 through an authorized source or a verified readback method.
- Record build metadata, sizes, hashes, boot headers, ramdisks, partition geometry, and AVB relationships without mixing A.123, A.128, and A.165 inputs.
- Complete the vendor/HAL/module inventory and distinguish Android application-processor firmware from MCU firmware.

**Completion evidence:** a versioned local stock inventory and repeatable validation, with a public summary that excludes proprietary payloads and private device data.

## 2. Establish a recoverable test path

- Verify the actual bootloader unlock conditions for OPWE242 and document the resulting device state.
- Obtain and validate the stock restoration inputs required for the same device and version.
- Define one narrowly scoped hardware test and its recovery procedure before writing modified images.

**Completion evidence:** a demonstrated OPWE242 restoration path and documented prerequisites. Root authorization, a detected fastboot interface, or emergency-download mode alone is insufficient.

## 3. Prepare and reproduce the kernel build

- Keep the official A.123 source history in separate kernel and modules/device-tree forks.
- Reproduce the source layout on a case-sensitive Linux filesystem; preserve symlinks and permissions.
- Supply the required Clang r487747c toolchain, device-tree compiler, and compatible build tools.
- Compare the resulting kernel configuration and module ABI with stock before proposing an A.165 test image.

**Completion evidence:** a reproducible kernel build, exact source/toolchain revisions, and an explicit record of remaining differences from A.165. Compiling the older sources does not establish current-stock compatibility.

## 4. Resolve the platform and vendor ABI

- Design a coherent ARM64/ARM32 platform configuration against the Android 17 reference.
- Establish a supported graphics strategy: compatible ARM64 implementations or a validated ARM32 consumer stack with all required dependencies.
- Inventory the Wear components needed for a hardware product and establish their availability and permitted distribution.
- Adapt OEM MCU, sensor, display, time synchronization, and vibration contracts instead of replacing platform JARs with incompatible stock versions.

**Completion evidence:** reviewed device/product configuration, dependency inventories, passing ABI/linker checks, and a feasible Wear integration plan. An emulator image alone does not complete this milestone.

## 5. Validate integration and packaging

- Run actual VINTF checks against the intended system/vendor pair.
- Validate SELinux policy, init services, filesystem ownership/context requirements, and linker namespaces.
- Verify boot-image headers, partition constraints, AVB relationships, and rollback requirements against the matching stock baseline.
- Produce build artifacts with repeatable manifests and hashes.

**Completion evidence:** successful builds and offline integration checks. Label artifacts as experimental until hardware validation is complete.

## 6. Test on OPWE242 and qualify a release

Begin hardware tests only after the stock baseline and recovery milestone are complete. Validate boot, suspend/resume, charging, connectivity, graphics, sensors, MCU coordination, haptics, and update behavior in a documented sequence.

Evaluate pairing, health services, and application compatibility separately. Payment and integrity-dependent services require their own evidence and are not implied by successful boot.

**Completion evidence:** test results for the exact source/build/device combination, known limitations, a verified restoration procedure, and a release package containing only material that may be redistributed.
