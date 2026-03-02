# Nothing Phone 2 Kernel Builder

Builds a custom kernel for **Nothing Phone 2 (Pong)** with [Wild_KSU](https://github.com/WildKernels/Wild_KSU) and [SUSFS](https://gitlab.com/simonpunk/susfs4ksu) via GitHub Actions.

Uses [kernel_nothing_sm8475_cleaned](https://github.com/MiguVT/kernel_nothing_sm8475_cleaned) as the default kernel source.

## Quick Start

1. Fork this repo
2. Go to **Actions** → **Build NP2 Kernel** → **Run workflow**
3. Download the AnyKernel3 zip from the completed run
4. Flash via recovery (TWRP / OrangeFox) or extract `Image` for fastboot

## Workflow Inputs

| Input | Default | Description |
|-------|---------|-------------|
| `kernel_repo` | `MiguVT/kernel_nothing_sm8475_cleaned` | Kernel source repo URL |
| `kernel_branch` | `clean` | Branch to build |
| `kernel_defconfig` | `vendor/meteoric_defconfig` | Defconfig path |
| `enable_susfs` | `true` | Enable SUSFS root hiding |

The workflow builds two variants automatically via matrix:
- **WKSU-SUSFS** — Wild_KSU + SUSFS
- **WKSU** — Wild_KSU only

## Flashing

### AnyKernel3 (recommended)
Boot into recovery → flash the zip → reboot.

### Fastboot
```bash
adb reboot bootloader
fastboot flash boot boot.img
fastboot reboot
```

After flashing, install the [KernelSU Manager](https://github.com/tiann/KernelSU/releases) app.

## Credits

- [WildKernels](https://github.com/WildKernels/Wild_KSU) — Wild_KSU
- [simonpunk](https://gitlab.com/simonpunk/susfs4ksu) — SUSFS
- [osm0sis](https://github.com/osm0sis/AnyKernel3) — AnyKernel3

## Disclaimer

Unlocking your bootloader voids your warranty. Flashing custom kernels can brick your device. Use at your own risk — always keep a stock boot image backup.
