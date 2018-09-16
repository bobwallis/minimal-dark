minimal-dark
============
Minimal, dark, Arch Linux themes for rEFInd, Plymouth and SLiM.

rEFInd
-------------------------
Loosely based on EvanPurkhiser's [rEFInd-minimal-theme](https://github.com/EvanPurkhiser/rEFInd-minimal-theme), but with white logos on a black background.

To use, copy the refind folder nto `minimal-dark` into your rEFInd EFI folder (usually `/boot/EFI/refind/`), then add the line `include minimal-dark/theme.conf` to the end of your `refind.conf`.

You might want to add some more icons into the `icons` folder if you use different OSs to me.

If you want to use the `use_graphics_for` option then the flash through grey is less than ideal. To fix:

1. Download the PKGBUILD and other files from `https://projects.archlinux.org/svntogit/packages.git/tree/trunk?h=packages/refind-efi`.
2. Run `makepkg -o` to download and extract the source files.
3. Open `src/refind-0.7.4/refind/screen.c`
4. Replace: `EG_PIXEL StdBackgroundPixel  = { 0xbf, 0xbf, 0xbf, 0 };` on line 69 with `EG_PIXEL StdBackgroundPixel  = { 0x0, 0x0, 0x0, 0 };`.
5. Run `makepkg -esi` to build and install.
6. Run `sudo refind-install` to copy the new rEFInd binaries to `/boot/efi/EFI/refind`.


Plymouth
-------------------------
Made by modifying the [Arch Logo](http://karlinux.deviantart.com/art/Arch-Logo-Plymouth-Theme-209553250) theme, which in turn is based on debian-logo.

Copy into `/usr/share/plymouth/themes/minimal-dark` and set the `minimal-dark` as the theme in
`/etc/plymouth/plymouthd.conf`.

SLiM
-------------------------
I don't use this one so it might not work any more.

If you're vertical screen resolution isn't 768px then the `session_y` and `msg_y` config options
will need adjusting.

Copy into `/usr/share/slim/themes/minimal-dark` and set `minimal-dark` as the theme in `/etc/slim.conf`.

GDM
-------------------------
Build, then copy the resulting `gnome-shell-theme.gresource` to `/usr/share/gnome-shell` and restart GDM.
