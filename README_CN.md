### TWRP 设备树 for Redmi Note 13 Pro+ (zircon)
=========================================

[English](README.md)

Redmi Note 13 Pro+ (代号 _"zircon"_) 是一款小米出品的智能手机。

它于 2023 年 5 月发布。

## 设备规格

| 基本项 | 规格说明 |
|--------|----------|
| CPU | 八核 (2x2.8 GHz Cortex-A715 & 6x2.0 GHz Cortex-A510) |
| 芯片组 | 联发科 天玑 7200-Ultra |
| GPU | Mali-G610 MC4 |
| 内存 | 8GB/12GB/16GB RAM (LPDDR5) |
| 出厂安卓版本 | Android 13, 可升级至 HyperOS |
| 存储 | 256GB/512GB (UFS 3.1) |
| 电池 | 不可拆卸 Li-Po 5000 mAh 电池 |
| 显示屏 | 1220 x 2712 像素, 6.67 英寸, 120 Hz, AMOLED |

![Redmi Note 13 Pro+](https://cdn.cnbj1.fds.api.mi-img.com/nr-pub/202309200033_a224298dc1a71d496778218f50ab427b.png)

## 功能状态

**正常工作的功能:**

- [X] ADB
- [X] 解密 (Android 15)
- [X] 显示
- [X] Fasbootd
- [X] 刷机
- [X] MTP
- [X] Sideload
- [X] USB OTG
- [ ] 振动器
- [X] 触摸

## 我该如何编译它？

首先使用以下命令同步最小版本的TWRP

```
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
repo sync -j$(nproc --all)
```

然后将这些项目添加到.repo/manifest.xml：

```xml
<project path="device/xiaomi/zircon" name="mytiantian001/android_device_xiaomi_zircon_twrp" remote="github" revision="a15" />
```

最后执行以下命令

```
source build/envsetup.sh
repopick <needed patch>
lunch twrp_zircon-eng
mka vendorbootimage -j$(nproc --all)
```
## 我该如何刷入？

使用以下命令刷入编译好的rec
```
fastboot flash vendor_boot out/target/product/zircon/vendor_boot.img
```
