[English](README.md)|[简体中文](自述文件.md)|[繁體中文](繁體中文.md)
--|--|--
# Yours-LegacyBIOS
Your own usual rEFInd's sign for LegacyBIOS.<br/>
Relying on DUET of [CloverBootloader](https://github.com/CloverHackyColor/CloverBootloader), rEFInd can run on Legacy BIOS.<br/>
It can save your old PC and make it support 64bit UEFI.
#### Your device should meet the requirements,
- NOT supporting 64bit UEFI,
- - 32bit UEFI supported;
- - Only Legacy BIOS without UEFI supported;
- GPU/vBIOS UEFI not supported; (See the picture)<br/>
![image](https://user-images.githubusercontent.com/69227436/213923710-120c5a02-30ea-4005-b2fe-c8e9adc7b6d7.png)
- GPT disk;
- Internal SATA disk, NOT NVMe or USB Storage;
- - It seems that DUET of CloverBootloader supports only SATA, NOT NVMe or USB;
#### Working Principle
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot`]=>[`CLOVERX64.EFI`(`refind_x64.efi` renamed)]=>[Yours]
#### File Tree
<img src="README/Yours-LegacyBIOS.png">

## 💻️Preview👀

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

<img src="README/about.duet.png">
</details>

## 🧭Guide⬇️

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

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
![屏幕截图 2023-05-10 204425](https://github.com/M-L-P/Yours-LegacyBIOS/assets/69227436/2fb6df69-e8be-4b67-b00f-ebde03fa0538)
</details>

### Manage ESP

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

#### Restore EFI files
- Restore EFI files from your backup into ESP.

#### Copy Yours in ESP
- Copy the file `zip: boot` into `ESP: \`
- Copy the folder `zip: EFI\CLOVER` into `ESP: \EFI`
- Copy the folder `zip: EFI\Yours` into `ESP: \EFI`

#### For Hackintosh
If you want,
- graphical interface is going to be not interrupted by codes;
- CloverBootloader does not conflict with Yours;

You need to perform the following steps.
<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

#### For OpenCore
- Set `LauncherOption=System` by editing `config.plist`;
- Cut your EFI files into `ESP: \EFI\Yours\efi\OC`;
- Edit `refind.conf` to enable `include /EFI/Yours/Settings/menuentry/examples/OpenCore.conf` with `#` deleted;

#### For CloverBootloader
- Cut your EFI files into `ESP: \EFI\Yours\efi\CLOVER`;
- Edit `refind.conf` to enable `include /EFI/Yours/Settings/menuentry/examples/CLOVER.conf` with `#` deleted;

</details>

</details>

</details>

## ⭐Star🌟
If you like it and are looking forward to the coming update, you can star it.💫

## 🎉Credit🎊
- [rEFInd Boot Manager](http://www.rodsbooks.com/refind/) of *Roderick W. Smith*;
- [grub2-filemanager
](https://github.com/a1ive/grub2-filemanager) of [a1ive](https://github.com/a1ive);
- DUET of [CloverBootloader](https://github.com/CloverHackyColor/CloverBootloader);
