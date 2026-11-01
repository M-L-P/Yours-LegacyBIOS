亲爱的朋友们：<br/>
    我生病了。病去如抽丝，掉了几层皮。<br/>
	暂停更新，等我好转一些。<br/>
<br/>
<br/>
<br/>
[icons](https://github.com/M-L-P/icons)|[rEFInd-theme-Yours](https://github.com/M-L-P/rEFInd-theme-Yours)|[Yours-LegacyBIOS](https://github.com/M-L-P/Yours-LegacyBIOS)|[Yours-UEFI](https://github.com/M-L-P/Yours-UEFI)
-|-|-|-

<div align="center">

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/M-L-P/Yours-LegacyBIOS)](https://github.com/M-L-P/Yours-LegacyBIOS/releases/latest)
[![GitHub all releases](https://img.shields.io/github/downloads/M-L-P/Yours-LegacyBIOS/total)](https://github.com/M-L-P/Yours-LegacyBIOS/releases)
[![GitHub Workflow Status (with event)](https://img.shields.io/github/actions/workflow/status/M-L-P/Yours-LegacyBIOS/%E6%89%93%E5%8C%85.yml)](https://github.com/M-L-P/Yours-LegacyBIOS/actions)
[![GitHub Discussions](https://img.shields.io/github/discussions/M-L-P/Yours-LegacyBIOS)](https://github.com/M-L-P/Yours-LegacyBIOS/discussions)
[![GitHub Repo stars](https://img.shields.io/github/stars/M-L-P/Yours-LegacyBIOS?style=social)](https://github.com/M-L-P/Yours-LegacyBIOS/stargazers)

</div>

[English](README.md)|[简体中文](README-自述文件.md)|[繁體中文](README-繁體中文.md)|...
--|--|--|--

<h1 align="center">Yours-LegacyBIOS</h1>

[Y-o-u-r-s](https://github.com/M-L-P/rEFInd-theme-Yours),<br/>
Your own usual rEFInd's sign for LegacyBIOS.<br/>
依赖于 [CloverBootloader](https://github.com/CloverHackyColor/CloverBootloader) 或 [OpenCore](https://github.com/acidanthera/OpenCorePkg) 的 DUET，Legacy BIOS 能够运行 rEFInd。<br/>
它能够拯救你的旧电脑，使其支持 64位 的 UEFI，化腐朽为神奇。
#### 你的设备满足以下情况中的一种，
- 不支持 64bit UEFI，
- - 支持 32bit UEFI；
- - 仅支持 Legacy BIOS，不支持 UEFI；
- GPU/vBIOS 不支持 UEFI；(如下图)<br/>
![image](https://user-images.githubusercontent.com/69227436/213923710-120c5a02-30ea-4005-b2fe-c8e9adc7b6d7.png)
#### 特色
- 支持 GPT 磁盘；
- 支持内置 SATA 硬盘；
- NVMe 固态 需要 使用 ~~`boot7`~~`boot0` 或 `boot1`；
- 旧电脑一般使用 `boot0` 作为默认的 `boot`，
- - 新电脑附带的 USB 3.0 接口 使用`boot1`作为默认的 `boot`，因为 USB 3.0 接口无法被 EhciDxe 驱动，但可以被 Block I/O 驱动；
#### 工作原理
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot`]=>[`Yours_x64.efi`]=>[Yours]<br/>
~~[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot6`]=>[`Yours_x64.efi`]=>[Yours]~~<br/>
~~[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot7`]=>[`Yours_x64.efi`]=>[Yours]~~<br/>
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot5`]=>[`Yours_x64.efi`]=>[Yours]<br/>
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot0`]=>[`Yours_x64.efi`]=>[Yours]<br/>
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot1`]=>[`Yours_x64.efi`]=>[Yours]<br/>
- 默认情况， `boot`；
- ~~按下 6， 是 Clover 的 `boot6`；~~
- ~~按下 7， 是 Clover 的 `boot7`；~~
- 按下 5， 是 Clover 的 `boot5`；
- 按下 0， `boot0`，OpenCore 的 `bootx64`（添加了键鼠驱动和NVMe驱动后重新编译）；
- 按下 1， `boot1`，OpenCore 的 `bootx64-blockio`（添加了键鼠驱动和NVMe驱动后重新编译）；
#### 文件结构树状图
<img src="https://github.moeyy.xyz/https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/Yours-LegacyBIOS/Yours-LegacyBIOS.png">

-----------------------------------------------------------------------------------------------------------------------------------
## 💻️预览👀

<details>
<summary>🖱️点击展开查看🖱️</summary>

<img src="https://github.moeyy.xyz/https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/Yours-LegacyBIOS/about.duet.png">
<img src="https://github.moeyy.xyz/https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/Yours/M.big.png">
</details>

## 🧭指南⬇️

需要使用 [DiskGenius](https://www.diskgenius.com/) 和 BOOTICE。
### 转化 MBR 为 GPT
__注意__: 所有文件是为 GPT 分区表准备的，因为我不使用 MBR 分区表。<br/>
如果你的硬盘已经是 GPT 的，你要 __跳过__ 这个步骤。
<details>
<summary>🖱️点击展开查看🖱️</summary>
https://www.diskgenius.com/manual/convert-partition-table-style.php

![image](https://github.com/M-L-P/Yours-LegacyBIOS/assets/69227436/93246cd8-f616-43c7-a5ac-8ca224ef8fb0)
</details>

### 覆盖引导记录

<details>
<summary>🖱️点击展开查看🖱️</summary>

#### 备份 EFI 文件
- 打开 DiskGenius；
- 把 ESP分区 中的所有的文件 复制到其他你想要的位置；
#### 格式化 ESP 成 FAT32
- 打开 DiskGenius；
- 格式化 ESP 成 FAT32(Basic data partition)；
- - 或者 在第一个分区前面 创建一个 FAT32 分区。
#### 覆盖 MBR 和 PBR
- 打开 BOOTICE；
- `zip: Boot_Record\mbr(boot0af)` 用来覆盖内置 SATA 硬盘的 MBR；<br/>
  ![mbr](https://github.com/M-L-P/Yours-LegacyBIOS/assets/69227436/af8d8cb4-3e10-48a8-ab06-71a8e69ed3ba)

- `zip: Boot_Record\pbr(boot1f32alt)` 用来覆盖 FAT32 的 PBR；<br/>
  ![pbr](https://github.com/M-L-P/Yours-LegacyBIOS/assets/69227436/a2a6f8f1-6b28-48a3-90fc-b7ed140adc86)

#### 把 FAT32 变成 ESP
- 打开 DiskGenius；
- [编辑分区参数](https://www.diskgenius.com/manual/modify-partition-para.php), set the FAT32 as ESP；
- 命名为 `EFI system partition`(如下图)<br/>
[<img src="https://github.com/M-L-P/Yours-LegacyBIOS/assets/69227436/2fb6df69-e8be-4b67-b00f-ebde03fa0538">](https://www.diskgenius.com/manual/modify-partition-para.php)
</details>

### 调整 ESP 分区

<details>
<summary>🖱️点击展开查看🖱️</summary>

#### 恢复 EFI 文件
- 从你的备份中把 EFI 文件恢复进 ESP 分区。

#### 复制 Yours 到 ESP 分区
- 复制文件 `zip: ESP\boot` 到 `ESP: \`；
- 复制文件 `zip: ESP\boot5` 到 `ESP: \`；
- ~~复制文件 `zip: ESP\boot6` 到 `ESP: \`~~；
- ~~复制文件 `zip: ESP\boot7` 到 `ESP: \`~~；
- 复制文件 `zip: ESP\boot0` 到 `ESP: \`；
- 复制文件 `zip: ESP\boot1` 到 `ESP: \`；
- 复制文件夹 `zip: ESP\EFI\Yours` 到 `ESP: \EFI`；

#### 若有 黑苹果
为了让图形界面衔接得更加紧密，中途没有代码界面，同时支持安全启动<br/>
<details>
<summary>🖱️点击展开查看🖱️</summary>

文件名|所在目录|文件原理|文件功能
-|-|-|-
`GRUB_PreLoader_CLOVER.efi`|`EFI\Yours\efi\Hackintosh`|链接到 `EFI\CLOVER\CLOVERX64.efi`|预启动 CloverBootloader
`GRUB_PreLoader_CLOVER.png`|`EFI\Yours\efi\Hackintosh`|同名显示图标|用于显示 Clover 的启动图标
`GRUB_PreLoader_OC.efi`|`EFI\Yours\efi\Hackintosh`|链接到 `EFI\OC\OpenCore.efi`|预启动 OpenCore
`GRUB_PreLoader_OC.png`|`EFI\Yours\efi\Hackintosh`|同名显示图标|用于显示 OC 的启动图标

#### 若是 OpenCore
- 你应该编辑 `config.plist` 设置 `LauncherOption=System` ；

#### 若不用黑果
- 你可以选定 Clover 或 OC 的启动图标，按下【Delete】，隐藏对应的入口。
</details>

</details>

## 📝FAQ❓️
### USB 可移动硬盘 或 NVMe 固态
- 用键盘按下数字键`7`，当黑色屏幕的左上角出现白色的 `_` 的时候；

## ⭐收藏🌟
如果你喜欢并且期待未来的更新，你可以点亮星星。💫

## 🎉来源🎊
- *Roderick W. Smith* 的 [rEFInd Boot Manager](http://www.rodsbooks.com/refind/)；
- [a1ive](https://github.com/a1ive) 的 [grub2-filemanager](https://github.com/a1ive/grub2-filemanager)；
- [CloverBootloader](https://github.com/CloverHackyColor/CloverBootloader) 的 DUET；
- [OpenCore](https://github.com/acidanthera/OpenCorePkg) 的 DUET；
- moeyy 的 github 加速器，用于显示图片，https://github.moeyy.xyz/ ；

## [🧁请我吃块巧克力🍫](https://github.com/M-L-P/.github/blob/main/profile/chocolate/README.md)