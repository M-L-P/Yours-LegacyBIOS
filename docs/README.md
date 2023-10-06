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
Relying on DUET of [CloverBootloader](https://github.com/CloverHackyColor/CloverBootloader) or [OpenCore](https://github.com/acidanthera/OpenCorePkg), rEFInd can run on Legacy BIOS.<br/>
It can save your old PC and make it support 64bit UEFI.
#### Your device should meet the requirements,
- NOT supporting 64bit UEFI,
- - 32bit UEFI supported;
- - Only Legacy BIOS without UEFI supported;
- GPU/vBIOS UEFI not supported; (See the picture)<br/>
![image](https://user-images.githubusercontent.com/69227436/213923710-120c5a02-30ea-4005-b2fe-c8e9adc7b6d7.png)
- GPT disk;
- Internal SATA disk;
- NVMe SSD should be with `boot7`;
#### Working Principle
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot`]=>[`Yours_x64.efi`]=>[Yours]<br/>
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot6`]=>[`Yours_x64.efi`]=>[Yours]<br/>
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot7`]=>[`Yours_x64.efi`]=>[Yours]<br/>
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot5`]=>[`Yours_x64.efi`]=>[Yours]<br/>
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot0`]=>[`Yours_x64.efi`]=>[Yours]<br/>
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot1`]=>[`Yours_x64.efi`]=>[Yours]<br/>
- By default, `boot`;
- Pressing 6, `boot6` of Clover;
- Pressing 7, `boot7` of Clover;
- Pressing 5, `boot5` of Clover;
- Pressing 0, `boot0`, `bootx64` of OpenCore;
- Pressing 1, `boot1`, `bootX64-blockio` of OpenCore;
#### File Tree
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/Yours-LegacyBIOS/Yours-LegacyBIOS.png">

-----------------------------------------------------------------------------------------------------------------------------------
## 💻️Preview👀

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/Yours-LegacyBIOS/about.duet.png">
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/Yours/M.big.png">
</details>

## 🧭Guide⬇️

It need use [DiskGenius](https://www.diskgenius.com/) and BOOTICE.
### Convert MBR to GPT
__Note__: All I have prepared is for GPT partition table, because I do NOT use MBR partition table.<br/>
If your disk has been already GPT, You shall __SKIP__ this step.
<details>
<summary>🖱️Click to Unfold to see🖱️</summary>
https://www.diskgenius.com/manual/convert-partition-table-style.php

![image](https://github.com/M-L-P/Yours-LegacyBIOS/assets/69227436/93246cd8-f616-43c7-a5ac-8ca224ef8fb0)
</details>

### Cover Boot Record

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

#### Backup EFI files
- Open DiskGenius;
- Copy all files from ESP to somewhere else you would like;
#### Format ESP as FAT32
- Open DiskGenius;
- Format ESP as FAT32(Basic data partition);
- - Or create a FAT32 before the first partition;
#### Cover MBR and PBR
- Open BOOTICE;
- `zip: Boot_Record\MBR.bin` covers MBR of Internal SATA disk;<br/>
  ![mbr](https://github.com/M-L-P/Yours-LegacyBIOS/assets/69227436/af8d8cb4-3e10-48a8-ab06-71a8e69ed3ba)

- `zip: Boot_Record\PBR.bin` covers PBR of that FAT32;<br/>
  ![pbr](https://github.com/M-L-P/Yours-LegacyBIOS/assets/69227436/a2a6f8f1-6b28-48a3-90fc-b7ed140adc86)

#### Turn FAT32 into ESP
- Open DiskGenius;
- [Modify partition parameters](https://www.diskgenius.com/manual/modify-partition-para.php), set the FAT32 as ESP;
- Name it `EFI system partition`(See the picture)<br/>
[<img src="https://github.com/M-L-P/Yours-LegacyBIOS/assets/69227436/2fb6df69-e8be-4b67-b00f-ebde03fa0538">](https://www.diskgenius.com/manual/modify-partition-para.php)
</details>

### Manage ESP

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

#### Restore EFI files
- Restore EFI files from your backup into ESP.

#### Copy Yours in ESP
- Copy the file `zip: ESP\boot` into `ESP: \`;
- Copy the file `zip: ESP\boot5` into `ESP: \`;
- Copy the file `zip: ESP\boot6` into `ESP: \`;
- Copy the file `zip: ESP\boot7` into `ESP: \`;
- Copy the file `zip: ESP\boot0` into `ESP: \`;
- Copy the file `zip: ESP\boot1` into `ESP: \`;
- Copy the folder `zip: ESP\EFI\Yours` into `ESP: \EFI`;

#### For Hackintosh
In order to ensure that the graphical interface is NOT going to be interrupted by codes, and that it will support Secure Boot<br/>
<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

File Name|Directory|Principle|Function
-|-|-|-
`GRUB_PreLoader_CLOVER.efi`|`EFI\Yours\efi\Hackintosh`|Linked to `EFI\CLOVER\CLOVERX64.efi`|PreLoader CloverBootloader
`GRUB_PreLoader_CLOVER.png`|`EFI\Yours\efi\Hackintosh`|To display icon with the same name|Used to display icon of Clover
`GRUB_PreLoader_OC.efi`|`EFI\Yours\efi\Hackintosh`|Linked to `EFI\OC\OpenCore.efi`|PreLoader OpenCore
`GRUB_PreLoader_OC.png`|`EFI\Yours\efi\Hackintosh`|To display icon with the same name|Used to display icon of OC

#### For OpenCore
- Set `LauncherOption=System` by editing `config.plist`;

#### Without Hackintosh
- You can select the icon of Clover or OC, press [Delete], and hide the corresponding entry.
</details>

</details>

## 📝FAQ❓️
### USB disks or NVMe SSDs
- Press the key `7` by using the keyboard when the black is showing a white `_` at the top left;

## ⭐Star🌟
If you like it and are looking forward to the coming update, you can star it.💫

## 🎉Credit🎊
- [rEFInd Boot Manager](http://www.rodsbooks.com/refind/) of *Roderick W. Smith*;
- [grub2-filemanager](https://github.com/a1ive/grub2-filemanager) of [a1ive](https://github.com/a1ive);
- DUET of [CloverBootloader](https://github.com/CloverHackyColor/CloverBootloader);
- DUET of [OpenCore](https://github.com/acidanthera/OpenCorePkg);

## [🧁Buy me a piece of chocolate🍫](https://github.com/M-L-P/.github/blob/main/profile/chocolate/README.md)