#### For OpenCore
- Set `LauncherOption=System` by editing `config.plist`;
- Cut your EFI files into `EFI\Yours\efi\OC`;
- Edit `refind.conf` to enable `include /EFI/Yours/Settings/menuentry/examples/OpenCore.conf` with `#` deleted;