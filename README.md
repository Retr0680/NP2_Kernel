# Nothing Phone 2 Kernel Builder

Builds a custom kernel for **Nothing Phone 2 (Pong)** with [KWKSU](https://github.com/WildKernels/Wild_KSU/) and optional [SUSFS](https://gitlab.com/simonpunk/susfs4ksu) via GitHub Actions.

Based on the [LineageOS android_kernel_nothing_sm8475](https://github.com/LineageOS/android_kernel_nothing_sm8475.git) kernel source (android13-5.10-waipio, sublevel 246).

## Quick Start

1. Fork this repo
2. Go to **Actions** → **Build NP2 Kernel** → **Run workflow**
3. Download the AnyKernel3 zip from the completed run
4. Flash via recovery (TWRP / OrangeFox) or extract `Image` for fastboot

## Workflow Inputs

| Input | Default | Description |
|-------|---------|-------------|
| `kernel_repo` | `LineageOS/android_kernel_nothing_sm8475` | Kernel source repo URL |
| `kernel_branch` | `lineage-23.2` | Branch to build |
| `kernel_defconfig` | `gki_defconfig` | Defconfig path (relative to `arch/arm64/configs/`) |
| `extra_configs` | `vendor/waipio_GKI.config vendor/nothing/waipio_GKI.config` | Extra config fragments to merge |

The workflow builds two variants automatically via matrix:
- **WKSU-SUSFS** — WKSU + SUSFS
- **WKSU** — WKSU only

## Flashing

### AnyKernel3
Boot into recovery → flash the zip → reboot.

After flashing, install the [KernelSU Manager](https://github.com/KernelSU-Next/KernelSU-Next/releases) app or the [Wild KSU](https://github.com/WildKernels/Wild_KSU) app to manage root access and modules.

## Credits

- [WildKernels](https://github.com/WildKernels/Wild_KSU) - WKSU
- [KernelSU-Next](https://github.com/KernelSU-Next/KernelSU-Next) — KSU-Next
- [simonpunk](https://gitlab.com/simonpunk/susfs4ksu) — SUSFS
- [osm0sis](https://github.com/osm0sis/AnyKernel3) — AnyKernel3
- [LineageOS](https://github.com/LineageOS) — Kernel source

## Disclaimer

Unlocking your bootloader voids your warranty. Flashing custom kernels can brick your device. Use at your own risk — always keep a stock boot image backup.
