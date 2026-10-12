# Repository index

Recorded organization layout: **27 repositories**, comprising **21 native
GitHub forks**, **one selected upstream Git mirror**, **one complete source
snapshot** and **four original project repositories**. The native forks are
the two OnePlus sources and nineteen Android platform components. Google
msm-extra is a selected Git mirror. Connectivity preserves the complete
canonical source tree in a new import commit, without Google commit history
on GitHub.

This index describes source organization for OPWE242 development. No complete
ROM, successful Linux source sync, compilation, hardware boot or installation
is claimed. Wear OS 7 / Android 17 / API 37 remains the target reference.

## Project and kernel repositories: seven

| Repository | Kind | Branch or baseline | Role |
|---|---|---|---|
| [development](https://github.com/OpWatch-Os/development) | Original project | `main` | Project status, roadmap, source provenance and this index. |
| [manifests](https://github.com/OpWatch-Os/manifests) | Original project | `main` | Complete AOSP source manifest, editable and pinned platform overlays, separate kernel workspace. |
| [android_device_oneplus_OPWE242](https://github.com/OpWatch-Os/android_device_oneplus_OPWE242) | Original project | `main` | Device architecture fragments and integration checklist; no complete lunch product. |
| [android_vendor_oneplus_OPWE242](https://github.com/OpWatch-Os/android_vendor_oneplus_OPWE242) | Original project | `main` | Public 84-path requirements descriptor and offline ELF/hash inventory tool; no proprietary files. |
| [android_kernel_oneplus_sw5100](https://github.com/OpWatch-Os/android_kernel_oneplus_sw5100) | Native GitHub fork of OnePlusOSS | `sw5100_wear_os_5.0_oneplus_watch_3_43mm`; `824c7022b19eabb6c0831924da134725e6068e40` | Published A.123 kernel 5.15.167 for the correct 43 mm variant. |
| [android_kernel_modules_and_devicetree_oneplus_sw5100](https://github.com/OpWatch-Os/android_kernel_modules_and_devicetree_oneplus_sw5100) | Native GitHub fork of OnePlusOSS | `sw5100_wear_os_5.0_oneplus_watch_3_43mm`; `024d4ff6705d3d00256a3af32b25cc22ccde0782` | Matching published modules, DTS and kernel build infrastructure. |
| [android_kernel_google_msm-extra](https://github.com/OpWatch-Os/android_kernel_google_msm-extra) | Selected Google Git mirror | `android-msm-sw5100-5.15-android15-qpr2`; `a4327f95421b0070c11fe9c70d0fd05466bf642c` | Optional SW5100 audio-module reference; compatibility with OnePlus stock is unverified. |

The Google msm-extra [canonical upstream](https://android.googlesource.com/kernel/msm-extra/+/refs/heads/android-msm-sw5100-5.15-android15-qpr2)
is separate from the OnePlus source publications. A branch name mentioning
Android 15 does not establish a complete Android 15 or Wear OS system.

## Editable Android platform components: twenty

Every selected platform repository has an editable **`opwatchos-17.0`** branch.
The table records its canonical Google **Android 17 r1 baseline commit**. The
branch may evolve during development; these hashes identify the canonical
source baseline, not a promise that mutable branch heads remain unchanged.
The pinned overlay uses the canonical commit for nineteen components and the
separate, tree-identical source import commit for Connectivity.

GitHub native fork parents can be public mirrors such as `aosp-mirror` or
`aosp-mirror-neo`. Those parent repositories are not presented as official
Google repositories; the canonical source is linked in each row.

| OpWatch-Os repository | Android source path | Kind | Canonical Google baseline SHA |
|---|---|---|---|
| [android_platform_frameworks_base](https://github.com/OpWatch-Os/android_platform_frameworks_base) | `frameworks/base` | Native GitHub fork | [`94b4c163b7dfe5ce3607f7bb8456f9573f7de57d`](https://android.googlesource.com/platform/frameworks/base/+/94b4c163b7dfe5ce3607f7bb8456f9573f7de57d) |
| [android_platform_system_core](https://github.com/OpWatch-Os/android_platform_system_core) | `system/core` | Native GitHub fork | [`545d2487e38192a2ce25040897ced877cf6b4f53`](https://android.googlesource.com/platform/system/core/+/545d2487e38192a2ce25040897ced877cf6b4f53) |
| [android_platform_build](https://github.com/OpWatch-Os/android_platform_build) | `build/make` | Native GitHub fork | [`5ce6f787337d0223710bf7d4a16dbe6d2a35f777`](https://android.googlesource.com/platform/build/+/5ce6f787337d0223710bf7d4a16dbe6d2a35f777) |
| [android_platform_bionic](https://github.com/OpWatch-Os/android_platform_bionic) | `bionic` | Native GitHub fork | [`06356e41c5ed7b12220b24c05ba4fdb873b126a7`](https://android.googlesource.com/platform/bionic/+/06356e41c5ed7b12220b24c05ba4fdb873b126a7) |
| [android_platform_art](https://github.com/OpWatch-Os/android_platform_art) | `art` | Native GitHub fork | [`b753cf97923c3695338d21466fa14c57b480a59a`](https://android.googlesource.com/platform/art/+/b753cf97923c3695338d21466fa14c57b480a59a) |
| [android_platform_build_soong](https://github.com/OpWatch-Os/android_platform_build_soong) | `build/soong` | Native GitHub fork | [`6722dd8833db7482df1a2543ca3fcf67ddf0f7b1`](https://android.googlesource.com/platform/build/soong/+/6722dd8833db7482df1a2543ca3fcf67ddf0f7b1) |
| [android_platform_frameworks_native](https://github.com/OpWatch-Os/android_platform_frameworks_native) | `frameworks/native` | Native GitHub fork | [`ae266dcb706d083868578cfedce381ef44488a07`](https://android.googlesource.com/platform/frameworks/native/+/ae266dcb706d083868578cfedce381ef44488a07) |
| [android_platform_frameworks_av](https://github.com/OpWatch-Os/android_platform_frameworks_av) | `frameworks/av` | Native GitHub fork | [`475269ec44acec82792be6b01fb8e16357d4d2c8`](https://android.googlesource.com/platform/frameworks/av/+/475269ec44acec82792be6b01fb8e16357d4d2c8) |
| [android_platform_system_sepolicy](https://github.com/OpWatch-Os/android_platform_system_sepolicy) | `system/sepolicy` | Native GitHub fork | [`e066568e98d86db31a9346d30977f3632fa7073c`](https://android.googlesource.com/platform/system/sepolicy/+/e066568e98d86db31a9346d30977f3632fa7073c) |
| [android_platform_system_libvintf](https://github.com/OpWatch-Os/android_platform_system_libvintf) | `system/libvintf` | Native GitHub fork | [`df89ad736e14ac375f61d50fa543ae7cd746a140`](https://android.googlesource.com/platform/system/libvintf/+/df89ad736e14ac375f61d50fa543ae7cd746a140) |
| [android_platform_hardware_interfaces](https://github.com/OpWatch-Os/android_platform_hardware_interfaces) | `hardware/interfaces` | Native GitHub fork | [`0162af698935100a590b7359581ac8b1b80693e5`](https://android.googlesource.com/platform/hardware/interfaces/+/0162af698935100a590b7359581ac8b1b80693e5) |
| [android_platform_hardware_libhardware](https://github.com/OpWatch-Os/android_platform_hardware_libhardware) | `hardware/libhardware` | Native GitHub fork | [`97ee3e33ec5ba48c0eca8341ed377ac4497a0678`](https://android.googlesource.com/platform/hardware/libhardware/+/97ee3e33ec5ba48c0eca8341ed377ac4497a0678) |
| [android_platform_packages_apps_Settings](https://github.com/OpWatch-Os/android_platform_packages_apps_Settings) | `packages/apps/Settings` | Native GitHub fork | [`213829fb67f5e070029e0513a088f31bc8f5c1ed`](https://android.googlesource.com/platform/packages/apps/Settings/+/213829fb67f5e070029e0513a088f31bc8f5c1ed) |
| [android_platform_packages_modules_Permission](https://github.com/OpWatch-Os/android_platform_packages_modules_Permission) | `packages/modules/Permission` | Native GitHub fork | [`1093eca7407576c72e51b1a88550ee0667a6e5dc`](https://android.googlesource.com/platform/packages/modules/Permission/+/1093eca7407576c72e51b1a88550ee0667a6e5dc) |
| [android_platform_packages_modules_Connectivity](https://github.com/OpWatch-Os/android_platform_packages_modules_Connectivity) | `packages/modules/Connectivity` | Complete source snapshot | [`347fbd34b368d19f0d87e908ea101eed3601a731`](https://android.googlesource.com/platform/packages/modules/Connectivity/+/347fbd34b368d19f0d87e908ea101eed3601a731) |
| [android_platform_packages_modules_Bluetooth](https://github.com/OpWatch-Os/android_platform_packages_modules_Bluetooth) | `packages/modules/Bluetooth` | Native GitHub fork | [`c77db469de80f86660bc053bec4dee0c5d4b947c`](https://android.googlesource.com/platform/packages/modules/Bluetooth/+/c77db469de80f86660bc053bec4dee0c5d4b947c) |
| [android_platform_system_libhidl](https://github.com/OpWatch-Os/android_platform_system_libhidl) | `system/libhidl` | Native GitHub fork | [`061055fc4dad78e5d25a77d9217001794656f16b`](https://android.googlesource.com/platform/system/libhidl/+/061055fc4dad78e5d25a77d9217001794656f16b) |
| [android_platform_system_hwservicemanager](https://github.com/OpWatch-Os/android_platform_system_hwservicemanager) | `system/hwservicemanager` | Native GitHub fork | [`60271965cf6b055ed82b2e1ae0bf74b2c34a6af2`](https://android.googlesource.com/platform/system/hwservicemanager/+/60271965cf6b055ed82b2e1ae0bf74b2c34a6af2) |
| [android_platform_build_blueprint](https://github.com/OpWatch-Os/android_platform_build_blueprint) | `build/blueprint` | Native GitHub fork | [`7f2058de8155b05ea3c3f8317d33bfe732cacf8b`](https://android.googlesource.com/platform/build/blueprint/+/7f2058de8155b05ea3c3f8317d33bfe732cacf8b) |
| [android_platform_system_tools_mkbootimg](https://github.com/OpWatch-Os/android_platform_system_tools_mkbootimg) | `system/tools/mkbootimg` | Native GitHub fork | [`4a27dd13adf9846e12d585d6fe99a375ebb58396`](https://android.googlesource.com/platform/system/tools/mkbootimg/+/4a27dd13adf9846e12d585d6fe99a375ebb58396) |

Connectivity's organization import commit is
[`f5311234fcf561df1c20d468a5072c103cc55ba0`](https://github.com/OpWatch-Os/android_platform_packages_modules_Connectivity/commit/f5311234fcf561df1c20d468a5072c103cc55ba0).
Its tree is **`3a9df5486bd2b0d48cf22a4df8b8e097d36da07d`**, identical to
the canonical Google commit above: all **3,017 files**, modes, licenses and
notices are retained. This is a full selected source snapshot, not a source
subset. Google commit history is not preserved on GitHub because historical
JSON blobs larger than GitHub's 100 MB file limit prevented that history from
being published. History remains available from the canonical upstream; the
project also retains it locally. The pinned overlay uses the import commit,
so it does not request a canonical commit absent from the snapshot repository.

## Source workspace manifests

The public AOSP manifest at `android-17.0.0_r1`, revision
`5bc9a7ce1cd78dd53613bbfd0ebf506e1e4adb0f`, contains **1,087 projects**.
`opwatch.xml` preserves that source set, substitutes the twenty components
above at the original Android paths and adds the two device/vendor scaffolds:
**1,089 projects**. The default groups omit three AOSP `notdefault` projects;
`repo init -g all` includes all groups.

On Linux with Git, Python 3 and the Android Repo launcher installed, start in
a new directory:

```sh
mkdir opwatch-aosp
cd opwatch-aosp
repo init -u https://github.com/OpWatch-Os/manifests -b main -m opwatch.xml
repo sync -c -j4
```

To initialize with the recorded selected platform baseline instead, use:

```sh
repo init -u https://github.com/OpWatch-Os/manifests -b main -m opwatch-pinned.xml
repo sync -c -j4
```

Choose one overlay when initializing a workspace. `opwatch-pinned.xml` fixes
the twenty platform components (nineteen canonical commits and Connectivity's
source import commit) and the two device/vendor scaffolds, while
other AOSP projects retain the release tag. A fully resolved immutable checkout must
be exported after a successful sync with `repo manifest -r`, alongside a lock
of external toolchains and build inputs. The manifests do not define a complete
OPWE242 product or provide proprietary Wear OS components.

After sync, start a local topic branch in the project you intend to modify:

```sh
repo start wifi-policy frameworks/base
cd frameworks/base
git remote get-url --push opwatch
```

Verify that this example's destination is
`https://github.com/OpWatch-Os/android_platform_frameworks_base`, then review
and commit the selected changes. Publish the committed topic to the editable
platform branch explicitly:

```sh
git push opwatch HEAD:refs/heads/opwatchos-17.0
```

The local topic name is `wifi-policy`; the destination branch is
`opwatchos-17.0`. No force push is used. For another platform component,
substitute its Android project path and verify its own organization remote
before pushing. Device/vendor branches follow their separate `main` workflow.

Use a **separate kernel workspace** for `kernel.xml`:

```sh
mkdir opwatch-kernel
cd opwatch-kernel
repo init -u https://github.com/OpWatch-Os/manifests -b main -m kernel.xml
repo sync -c -j2
```

This preserves the OnePlus modules repository at `src/oneplus-sw5100` and the
kernel at `src/oneplus-sw5100/kernel_platform/msm-kernel`. Case-sensitive
filenames, POSIX permissions and symlinks are required. Toolchain and external
kernel dependencies remain to be completed and verified. The optional Google
msm-extra reference uses `upstream-msm-extra.xml` in another separate directory;
it is not automatically integrated into the OnePlus kernel workspace.

All repositories retain upstream copyright notices and per-file licensing.
Apache-2.0 on original project documentation does not replace kernel/module or
platform licenses and grants no rights to distribute external vendor/SDK
binaries. Public descriptors and documentation contain no raw device logs,
credentials, unique device identifiers, private paths or firmware binaries.
