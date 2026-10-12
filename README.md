 <div align="center">

<img src="banner.png" alt="Ki-Kernel POCO F4 (munch)" width="100%" />

# ⚡ Ki-Kernel

**POCO F4 (munch) / Redmi K40S**

*Custom Linux kernel with performance tuning, power management and additional kernel features.*

[![Kernel](https://img.shields.io/badge/Linux-4.19.325-blue.svg)](https://kernel.org)
[![Android](https://img.shields.io/badge/Android-13--17-green.svg)](#rom-support)
[![Root](https://img.shields.io/badge/Root-BakaSU%20%2F%20ReSukiSU-red.svg)](https://github.com/Baka-SU/BakaSU)
[![SuSFS](https://img.shields.io/badge/SuSFS-v2.3.0-orange.svg)](https://gitlab.com/simonpunk/susfs4kernel)
[![Device](https://img.shields.io/badge/Device-munch-purple.svg)](#device-support)

</div>

---

## Overview

Ki-Kernel is a custom kernel for the **POCO F4 (munch)**, based on the Xiaomi SM8250 kernel tree. It focuses on gaming performance, daily-use responsiveness, battery management and compatibility with AOSP and MIUI / HyperOS ROMs.

## Features

### Core & Compatibility

- Linux 4.19.325
- ZyCromerZ Clang 16.0.6
- Android 13–17 compatibility work
- eBPF backports for newer Android userspace
- PID, USER and network namespaces
- Docker, LXC and container support

### CPU & Gaming

- Tuned schedutil and WALT
- Ki-Profile CPU profiles
- CPUSET and core migration tuning
- RTG and SchedTune support
- Performance-oriented CPU frequency scaling
- C-state and idle power tuning
- Adreno 650 GPU frequency tuning, undervolting and overclocking
- GPU boost and idle power management
- Focaltech touchscreen latency tuning

### Display & Audio

- Hardware DC Dimming for supported panels
- Smart FPS and dynamic refresh-rate fixes
- KCAL hardware color calibration
- WCD938x Hi-Fi audio tuning
- UHQA headphone audio support
- Sound Control
- USB Audio and external DAC support
- Headset impedance detection
- AW86927 haptic tuning

### Battery & Charging

- Hardware bypass charging
- Force Fast Charge
- Screen-On Fast Charge
- Charging current controls
- Battery health and cycle count interfaces
- Ki-Thermal controls
- Screen-off power optimizations
- Deep Sleep and suspend tuning

Actual charging speed depends on the charger, cable, battery temperature, battery state and ROM configuration.

### Memory & Storage

- ZRAM with LZ4, LZ4KD, LZ4HC and ZSTD
- Configurable ZRAM size through `reki-zram`
- Dynamic Fsync
- MGLRU and memory reclaim tuning
- `kswapd` CPU affinity tuning
- F2FS background garbage collection tuning
- Maple, Kyber, Deadline and other supported I/O schedulers
- UFS 3.1 read-ahead tuning
- USB Attached SCSI (UAS)
- NTFS filesystem support

### Networking

- Google BBRv3
- TCP Westwood-sub
- TCP Fast Open
- TCP ECN support
- PLB support
- Built-in WireGuard
- IPv4 / IPv6 tethering support

### Root & Security

- BakaSU / ReSukiSU integration
- SuSFS v2.3.0
- Inline hook support
- Baseband-Guard
- KernelSU-compatible manager support, depending on the build
- SELinux and kernel security configuration updates

---

## Kernel Controls

Some builds expose the following interfaces for runtime control. Availability depends on the selected build.

### Ki-Profile

Path:

```bash
/proc/ki_profile
```

Available profiles:

```bash
# Battery Saver
echo 0 > /proc/ki_profile

# Balanced
echo 1 > /proc/ki_profile

# Performance
echo 2 > /proc/ki_profile

# Check active profile
cat /proc/ki_profile
```

### Bypass Charging

Path:

```bash
/proc/bypass_charging
```

```bash
# Enable bypass charging
echo 1 > /proc/bypass_charging

# Disable bypass charging
echo 0 > /proc/bypass_charging

# Check status
cat /proc/bypass_charging
```

### Force Fast Charge

Path:

```bash
/proc/fast_charge
```

```bash
# Enable
echo 1 > /proc/fast_charge

# Disable
echo 0 > /proc/fast_charge

# Check status
cat /proc/fast_charge
```

Check the interfaces provided by your build before using these commands.

---

## ROM Support

| Build | Target |
|---|---|
| AOSP | AOSP-based custom ROMs |
| MIUI / HyperOS | Stock-based Xiaomi ROMs |

Android version compatibility varies by ROM and build. Use the release notes for the exact supported configurations.

## Download Variants

| Package | Contents |
|---|---|
| `KSU+SUSFS.zip` | BakaSU with SuSFS integration |
| `KSU.zip` | BakaSU without SuSFS |
| `NOKSU.zip` | Kernel without an integrated root subsystem |

Root-related features depend on the selected package. A build without an integrated root subsystem does not automatically guarantee Play Integrity certification.

## Installation

1. Download the correct ZIP for your device and ROM.
2. Reboot into TWRP / OrangeFox or use a compatible kernel flasher.
3. Flash the ZIP.
4. Reboot to system.
5. Verify that the device boots and the expected kernel version is active.

**Before flashing:**
- Confirm that the device is `munch`.
- Use the package intended for your ROM.
- Keep a backup of your current boot image.
- Do not mix AOSP and MIUI / HyperOS builds unless the release explicitly supports it.

## Credits

- [Linux Kernel](https://kernel.org)
- [LineageOS SM8250](https://github.com/LineageOS/android_kernel_xiaomi_sm8250)
- [BakaSU](https://github.com/Baka-SU/BakaSU)
- [SuSFS](https://gitlab.com/simonpunk/susfs4kernel) by simonpunk
- [Baseband-Guard](https://github.com/vc-teahouse/Baseband-guard) by vc-teahouse
- [AnyKernel3](https://github.com/osm0sis/AnyKernel3) by osm0sis
- [liyafe1997](https://github.com/liyafe1997/kernel_xiaomi_sm8250_mod)
- [UtsavBalar1231](https://github.com/UtsavBalar1231/kernel_xiaomi_sm8250)
- All contributors, testers and the POCO F4 community

---

## Links

- **GitHub:** [Luckyfr1945/ki-kernel](https://github.com/Luckyfr1945/ki-kernel)
- **Telegram:** [Ki Community](https://t.me/kikernel)

