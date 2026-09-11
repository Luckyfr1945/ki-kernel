# CS Kernel - POCO F4 (munch)

Custom kernel for POCO F4 / Redmi K40S (munch / sm8250) based on LineageOS 4.19 with KernelSU-Next and SuSFS.

## Specs & Features
- Linux 4.19.325
- KernelSU-Next v3.3.0 (Driver UAPI v2)
- SuSFS v1.5.7 (15/15 features enabled)
- Metamodul / OverlayFS support (fixed error 17)
- Realtime discard (TRIM) for EROFS & F2FS
- ZRAM: LZ4, LZ4HC, ZSTD

## Builds
- **AOSP**: For AOSP based ROMs (tested on Android 16 / AxionOS 2.8 Beta)
- **MIUI**: For MIUI / HyperOS stock based ROMs

## Changelog
- Bump KernelSU-Next to v3.3.0 with Driver UAPI v2
- Enable all 15 SuSFS configs (TRY_UMOUNT, SUS_OVERLAYFS, SUS_MAPS, etc)
- Fix undefined reference to `susfs_try_umount_all` in `fs/namespace.c`
- Fix `add_try_umount` return code (fixes OverlayFS mount error 17)
- Fix use-after-free kernel panic on `__sys_setresuid`
- Fix string buffer panic on `CMD_SUSFS_SHOW_ENABLED_FEATURES`
- Update build script to output both AOSP and MIUI flashable zips

## Flashing
Flash the zip via Custom Recovery (TWRP / OrangeFox) or Kernel Flasher:
- AOSP: `Kernel_AOSP_munch_*.zip`
- MIUI: `Kernel_MIUI_munch_*.zip`

## Notes
Root hiding di kernel level (SuSFS) udah aktif semua. Untuk bypass app banking / DANA, pastikan setup userspace juga bener:
- Play Integrity lolos device integrity (PlayIntegrityFix)
- Sembunyikan app root (MT Manager, KSU, LSPosed, Termux) pake Hide My Applist
- Hide Zygisk pake Shamiko / Zygisk Assistant

## Credits
- [LineageOS SM8250](https://github.com/LineageOS/android_kernel_xiaomi_sm8250)
- [KernelSU-Next](https://github.com/KernelSU-Next/KernelSU-Next)
- [SuSFS](https://gitlab.com/simonpunk/susfs4kernel) by simonpunk
- [AnyKernel3](https://github.com/osm0sis/AnyKernel3) by osm0sis
- [liyafe1997](https://github.com/liyafe1997/kernel_xiaomi_sm8250_mod)
- [UtsavBalar1231](https://github.com/UtsavBalar1231/kernel_xiaomi_sm8250)
