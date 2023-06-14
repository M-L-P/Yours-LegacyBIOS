[![GitHub release (latest by date)](https://img.shields.io/github/v/release/M-L-P/Yours)](https://github.com/M-L-P/Yours/releases/latest)
[![GitHub all releases](https://img.shields.io/github/downloads/M-L-P/Yours/total)](https://github.com/M-L-P/Yours/releases)
[![GitHub Discussions](https://img.shields.io/github/discussions/M-L-P/Yours)](https://github.com/M-L-P/Yours/discussions)
[![GitHub Repo stars](https://img.shields.io/github/stars/M-L-P/Yours?style=social)](https://github.com/M-L-P/Yours/stargazers)

[English](README.md)|[简体中文](自述文件.md)|[繁體中文](繁體中文.md)|...
--|--|--|--

# Yours
Y-o-u-r-s,<br/>
Your own usual rEFInd's sign.
- You can
- - ✏️set ___your profile___;
- - ✏️set ___device___;
- - ✏️set ___your name___.

- It is based on [rEFInd Boot Manager](http://www.rodsbooks.com/refind/) of *Roderick W. Smith*, with [grub2-filemanager](https://github.com/a1ive/grub2-filemanager) built-in.

- - So you can boot .iso files from internal SSD by using [grub2-filemanager](https://github.com/a1ive/grub2-filemanager) of [a1ive](https://github.com/a1ive).

- Here are [icons](https://github.com/M-L-P/icons) for You.

## 💻️Preview👀
Press the key `F10` or `\` to take a screenshot, by using your keyboard.<br/>
Screenshots are folded.
<details>
<summary>🖱️Click to Unfold to see🖱️</summary>
<img src="README/B.big.png">
<img src="README/B.small.png">
<img src="README/M.big.png">
<img src="README/M.small.png">
<img src="README/1080p.B.big.png">
<img src="README/1080p.B.small.png">
<img src="README/1080p.M.big.png">
<img src="README/1080p.M.small.png">

</details>


## 🧭Guide⬇️

### Where to Download
<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

#### For UEFI Firmware
If your device meets the requirements,
- 64bit UEFI supported;
- GPU/vBIOS UEFI supported;

You should use [Yours-UEFI](https://github.com/M-L-P/Yours-UEFI).

#### For Legacy BIOS
Else,
- NOT supporting 64bit UEFI,
- - 32bit UEFI supported;
- - Only Legacy BIOS without UEFI supported;
- GPU/vBIOS UEFI not supported; (See the picture)

![image](https://user-images.githubusercontent.com/69227436/213923710-120c5a02-30ea-4005-b2fe-c8e9adc7b6d7.png)

You should use [Yours-LegacyBIOS](https://github.com/M-L-P/Yours-LegacyBIOS).

#### For Hyper-V
Download .vhdx from [Releases](https://github.com/M-L-P/Yours/releases).
</details>

### Edit Your Banner

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

- For 1K screen, open `EFI\Yours\Settings\display\1K\BannerEditor.pptx` by using Microsoft PowerPoint 2021+;
- For 2K screen, open `EFI\Yours\Settings\display\2K\BannerEditor.pptx` by using Microsoft PowerPoint 2021+;
- Edit to set your profile, device and your name;
- Save as a PNG;
- Edit `EFI\Yours\Settings\display\display.conf` to set the new made as the banner.

<img src="Settings/display/1K/M.L.P.png"><br/>
<img src="Settings/display/1K/BannerEditor.png">
</details>

## 📝FAQ❓️
Frequently asked question

### Resize Icons
<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

- edit `EFI\Yours\Settings\display\display.conf`

Icon Size|Token|Screen Resolutions|Examples
--|--|--|--
Original Size|`small_icon_size 48` `big_icon_size 128`|Resolutions < `1024x768`|`800x600` and so on
Double Size|`small_icon_size 96` `big_icon_size 256`|`1024x768` ≤ Resolutions < `1920x1080`|`1024x768`,`1366x768`,`1440x900` and so on
Treble Size|`small_icon_size 144` `big_icon_size 384`|Resolutions ≥ `1920x1080`|`1080P`,`2K`,`4K` and so on

</details>

### The Icon of Windows
<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

No matter which version of Windows you are using,<br/>
you should copy its icon,<br/>
from `EFI\Yours\Settings\icon\Windows` to `EFI\Yours\Settings\icon\showing`,<br/>
and rename it `os_win8.png`.<br/>
It is because rEFInd is taking `os_win8.png` as the icon of `Windows Boot Manager`.<br/>
</details>

### The Icon of Hackintosh
<details>
<summary>🖱️Click to Unfold to see🖱️</summary>
In order to ensure that the graphical interface is going to be not interrupted by codes,<br/>
You need to perform the following steps.

#### For OpenCore
- Set `LauncherOption=System` by editing `config.plist`;
- Cut your EFI files into `EFI\Yours\efi\OC`;
- Edit `refind.conf` to enable `include /EFI/Yours/Settings/menuentry/examples/OpenCore.conf` with `#` deleted;

#### For CloverBootloader
- Cut your EFI files into `EFI\Yours\efi\CLOVER`;
- Edit `refind.conf` to enable `include /EFI/Yours/Settings/menuentry/examples/CLOVER.conf` with `#` deleted;

</details>

### The Icon of Linux Distros
Here are [icons](https://github.com/M-L-P/icons/tree/main/PNGs/Linux) for You.

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

- find and download which icons you need from [here](https://github.com/M-L-P/icons/tree/main/PNGs/Linux);
- Rename the PNG files,
- - `os_$NAME.png` is the icon of `ESP: \EFI\$NAME\grubx64.efi`;
- Copy into `ESP: \EFI\Yours\Settings\icon\showing`;
</details>

## ⭐Star🌟
If you like it and are looking forward to the coming update, you can star it.💫

## 🎉Credit🎊
- [rEFInd Boot Manager](http://www.rodsbooks.com/refind/) of *Roderick W. Smith*;
- [grub2-filemanager](https://github.com/a1ive/grub2-filemanager) of [a1ive](https://github.com/a1ive);
- More modern icons,
- - Some coming from [Iconfont](https://www.iconfont.cn/),
- - Some coming from [Iconfinder](https://www.iconfinder.com/),
- - Some coming from macOS and [OC](https://github.com/acidanthera/OpenCorePkg),
- - Others coming from Unknown;

## 🧁Buy me a piece of chocolate🍫
<details>
<summary>🖱️Click to Unfold to see🖱️</summary>
I have no father; No man celebrates my birthday; No man buys me a cake🎂.<br/>
If you are willing, please treat me to a piece of chocolate🍫.<br/>
I need chocolate🍫 to help me release endorphins and dopamine to get rid of pain.<br/>
I would be very grateful to you, fairy lady🧚 or handsome knight🦸‍♂️.<br/>
<img src="https://github.com/M-L-P/Yours/assets/69227436/f094f056-9420-4dd5-beec-4ccecff20a1e" width="300px"><br/>
<img src="https://github.com/M-L-P/Yours/assets/69227436/8608e193-3c4d-4926-8171-7944e881d95f" width="300px">

[The List of Fairy Lady🧚 or Handsome kKnight🦸‍♂️](https://github.com/M-L-P/.github/blob/main/list/README.md)
</details>