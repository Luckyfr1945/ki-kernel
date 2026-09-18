# Ki-kernel - POCO F4 (munch)

Custom kernel for **POCO F4 / Redmi K40S (munch)** with KernelSU-Next, SuSFS, performance tuning, memory optimizations and additional kernel features.

Base: `kernel_xiaomi_sm8250_mod`, `munch_defconfig`, proton-clang toolchain.

## Specs & Features

- Linux 4.19.325
- KernelSU-Next with UAPI v4
- SuSFS v1.5.7 (Non-GKI)
- Metamodule / OverlayFS support
- EROFS support
- F2FS realtime discard (TRIM) for UFS 3.1 storage
- ZRAM with LZ4, LZ4KD, LZ4HC and ZSTD
- Google BBRv3 backport (FQ scheduler, Westwood+ fallback)
- WALT & schedutil tuning (per-cluster rate limits)
- MGLRU memory management
- Ki-Profile CPU profiles
- Ki-Thermal runtime thermal control
- Hardware Bypass Charging (Qualcomm PM8150B)
- Sound Control support
- Smart FPS for 60 / 90 / 120Hz
- Built-in WireGuard support
- Battery SOH & cycle count interface
- Charging current control
- Qualcomm Bluetooth & USB audio optimizations
- Android 15 / 16 compatibility improvements

## CPU Profiles

Ki-Profile provides switchable CPU profiles:

- **Battery** - lower power consumption
- **Balanced** - default profile for daily use
- **Performance** - higher performance
- **Gaming** - performance-focused tuning

Profile interface:

```text
/sys/kernel/ki_profile/mode
```

## Thermal Control

Ki-Thermal provides runtime thermal throttle control:

```text
/sys/kernel/ki_profile/thermal_throttle
```

Critical thermal protection and emergency shutdown mechanisms remain enabled regardless of profile.

## Bypass Charging

Hardware bypass charging routes current directly to the load instead of the battery cell, keeping the battery near 0mA charge current during sustained load (e.g. gaming).

```text
/sys/class/power_supply/battery/bypass_charging
```

A standard `charging_enabled` node is also exposed for compatibility with ACC / Kernel Manager-style modules. Bypass charging must be toggled manually; it does not disable itself at 100%.

## Builds

### AOSP

For AOSP-based ROMs.

### MIUI / HyperOS

For MIUI 13/14 and HyperOS stock-based ROMs.

## Flashing

Flash the appropriate ZIP using **TWRP, OrangeFox, Kernel Flasher**, or another compatible kernel flashing method.

```text
AOSP  : Ki-kernel-AOSP_*.zip
MIUI  : Ki-kernel-MIUI_*.zip
```

Make sure to use the correct build for your ROM.

## Notes

- Target device: POCO F4 / Redmi K40S (`munch`)
- AOSP and MIUI / HyperOS builds are produced from a single dual-target build, packaged separately via AnyKernel3
- KernelSU-Next and SuSFS are integrated at the kernel level, not as a flashable add-on
- Additional tunables are exposed through sysfs interfaces under `ki_profile` and standard power_supply nodes

## Credits

- [LineageOS SM8250](https://github.com/LineageOS/android_kernel_xiaomi_sm8250)
- [KernelSU-Next](https://github.com/KernelSU-Next/KernelSU-Next)
- [SuSFS](https://gitlab.com/simonpunk/susfs4kernel) by simonpunk
- [AnyKernel3](https://github.com/osm0sis/AnyKernel3) by osm0sis
- [liyafe1997](https://github.com/liyafe1997/kernel_xiaomi_sm8250_mod)
- [UtsavBalar1231](https://github.com/UtsavBalar1231/kernel_xiaomi_sm8250)
- testers
