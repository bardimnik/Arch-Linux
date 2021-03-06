# Recommended supplements for new installations
This page describes some supplementary but strongly recommended packages and their configuration for [new installations](../README.md).
It is assumed that all of the [necessary essential configuration](essentials-installation.md) has been done.
> To reduce dependencies, the main recommended packages on this page are all part of the [`core`](https://www.archlinux.org/packages/?repo=Core) repository. In some cases additional notes have been added which refer to possibly useful packages in either the [`extra`](https://www.archlinux.org/packages/?repo=Extra) or the [`community`](https://www.archlinux.org/packages/?repo=Community) repository.

## Command line editor
[Install](../using-pacman.md#install-a-package) package [`vi`](https://www.archlinux.org/packages/core/x86_64/vi/).

> Additionally, to have a more intuitive kind of editor, you could [install](../using-pacman.md#install-a-package) package [`nano`](https://www.archlinux.org/packages/core/x86_64/nano/).

> For an extended vi editor, you could [install](../using-pacman.md#install-a-package) package [`gvim`](https://www.archlinux.org/packages/extra/x86_64/gvim/) or [`vim`](https://www.archlinux.org/packages/extra/x86_64/vim/) (see https://wiki.archlinux.org/index.php/Vim).

## Add an administrative user
### Install prerequisites
As user `root`:
* [Install](../using-pacman.md#install-a-package) package [`sudo`](https://www.archlinux.org/packages/core/x86_64/sudo/)
* Call `visudo` and remove the `# ` of rule `# %wheel ALL=(ALL) ALL`.
  > Package [`vi`](https://www.archlinux.org/packages/core/x86_64/vi/) is required for this to work (see the previous [Command line editor](#command-line-editor) section)

### Add the user
```bash
useradd -m -G wheel <username>
passwd <username>
```

## Utilities for monitoring your system
[Install](../using-pacman.md#install-a-package) package [`procps-ng`](https://www.archlinux.org/packages/core/x86_64/procps-ng/) which includes `ps`, `top` and `uptime`.

> For extended system and performance monitoring, you could [install](../using-pacman.md#install-a-package) package [`htop`](https://www.archlinux.org/packages/extra/x86_64/htop/) and/or [`sysstat`](https://www.archlinux.org/packages/community/x86_64/sysstat/).

## Additional network tools
[Install](../using-pacman.md#install-a-package) package [`iputils`](https://www.archlinux.org/packages/core/x86_64/iputils/) which includes i.e. `ping`.

## Reading manual pages
[Install](../using-pacman.md#install-a-package) packages [`man-db`](https://www.archlinux.org/packages/core/x86_64/man-db/) and [`man-pages`](https://www.archlinux.org/packages/core/x86_64/man-pages/).

## Additional archivers
[Install](../using-pacman.md#install-a-package) package [`tar`](https://www.archlinux.org/packages/core/x86_64/tar/).
> For much higher compression and decompression speed for tar (at the cost of some compression ratio), you could [install](../using-pacman.md#install-a-package) package [`lzop`](https://www.archlinux.org/packages/extra/x86_64/lzop/).

> [`gzip`](https://www.archlinux.org/packages/core/x86_64/gzip/), [`bzip2`](https://www.archlinux.org/packages/core/x86_64/bzip2/), [`xz`](https://www.archlinux.org/packages/core/x86_64/xz/) and [`lz4`](https://www.archlinux.org/packages/core/x86_64/lz4/) are already installed as dependencies of either [`linux`](https://www.archlinux.org/packages/core/x86_64/linux/) or [`pacman`](https://www.archlinux.org/packages/core/x86_64/pacman/).

## Adding AUR package management with yaourt
### Prepare
```
sudo pacman -S --needed base-devel git
```
### Install package-query
```
git clone https://aur.archlinux.org/package-query.git
cd package-query
makepkg -sri
cd ..
```
### Install yaourt
```
git clone https://aur.archlinux.org/yaourt.git
cd yaourt
makepkg -sri
cd ..
```
Now you can use `yaourt` to update your system, install some packages etc.

### Cleanup
```
rm -rf package-query yaourt
```

Please also check [some more optimizations for a new installation](optimizations.md)
