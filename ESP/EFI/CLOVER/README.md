## ESP: /EFI/CLOVER
- `CLOVERX64.efi` is linked to `Yours_x64.efi`;
 
### Working Principle
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot`]=>[`CLOVERX64.efi`(Linked to `Yours_x64.efi`)]=>[Yours]
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot7`]=>[`CLOVERX64.efi`(Linked to `Yours_x64.efi`)]=>[Yours]
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot5`]=>[`CLOVERX64.efi`(Linked to `Yours_x64.efi`)]=>[Yours]
[Power On]=>[Legacy BIOS]=>[MBR]=>[PBR]=>[`boot0`]=>[`OpenCore.efi`(Linked to `Yours_x64.efi`)]=>[Yours]