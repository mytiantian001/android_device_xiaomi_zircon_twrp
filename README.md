### TWRP device tree for Redmi Note 13 Pro+ (zircon)
=========================================

[简体中文](README_CN.md)

The Redmi Note 13 Pro+ (codenamed _"zircon"_) is a high-end, mid-range smartphone from Xiaomi.

It was released in May 2023.

## Device specifications

Basic   |    Spec Sheet
-------:|:-------------------------
CPU    |  Octa-core (2x2.8 GHz Cortex-A715 & 6x2.0 GHz Cortex-A510)	
Chipset |  Mediatek Dimensity 7200-Ultra
GPU    |  Mali-G610 MC4	
Memory |	8GB/12GB/16GB RAM (LPDDR5)	
Shipped Android Version | Android 13, up to HyperOS	
Storage |	256GB/512GB (UFS 3.1)	
Battery |	Non-removable Li-Po 5000 mAh battery	
Display |	1220 x 2712 pixels, 6.67 inches, 120 Hz, AMOLED

![Redmi Note 13 Pro+](https://cdn.cnbj1.fds.api.mi-img.com/nr-pub/202309200033_a224298dc1a71d496778218f50ab427b.png)

## Features

Works:

- [X] ADB
- [X] Decryption (Android 15)
- [X] Display
- [X] Fasbootd
- [X] Flashing
- [X] MTP
- [X] Sideload
- [X] USB OTG
- [  ] Vibrator
- [X] Touch

## Compile

First checkout minimal twrp with aosp tree:

```
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
repo sync -j$(nproc --all)
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/xiaomi/zircon" name="mytiantian001/android_device_xiaomi_zircon_twrp" remote="github" revision="a15" />
```

Finally execute these:

```
source build/envsetup.sh
repopick <needed patch>
lunch twrp_zircon-eng
mka vendorbootimage -j$(nproc --all)
```
## To use it:

```
fastboot flash vendor_boot out/target/product/zircon/vendor_boot.img
```
