[English](README.md)|[简体中文](自述文件.md)|[繁體中文](繁體中文.md)
--|--|--

# Yours-LegacyBIOS
Your own usual rEFInd's sign for LegacyBIOS.

Your device should meet the requirements,
- NOT supporting 64bit UEFI,
- - 32bit UEFI supported;
- - Only Legacy BIOS without UEFI supported;
- GPU/vBIOS UEFI not supported; (See the picture)

![image](https://user-images.githubusercontent.com/69227436/213923710-120c5a02-30ea-4005-b2fe-c8e9adc7b6d7.png)

## 💻️Preview👀

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

<img src="README/about.duet.png">
</details>

## 🧭Guide⬇️

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

### Cover Boot Record

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

It need use [DiskGenius](https://www.diskgenius.com/) and Bootice.
#### Backup EFI files
- Open DiskGenius;
- Copy all files from ESP to somewhere else you would like;
#### Format ESP as FAT32
- Open DiskGenius;
- Format ESP as FAT32(Basic data partition);
#### Cover MBR and PBR
- Open Bootice;
- `\Boot_Record\MBR.bin` covers MBR;
- `\Boot_Record\PBR.bin` covers PBR;
#### Turn FAT32 into ESP
- Open DiskGenius;
- Change partition parameters, set the FAT32 as
</details>

 
### Manage ESP

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

</details>

</details>

## ⭐Star🌟
If you like it and are looking forward to the coming update, you can star it.💫

## 🎉Credit🎊
- 
