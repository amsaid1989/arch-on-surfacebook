# Installing Arch on Surface Book with Secure Boot

## Quick summary of the steps required

1) Download Arch installation ISO and create bootable USB
2) Disable secure boot and boot into Arch installation ISO
3) Follow the [Arch Installation Guide](https://wiki.archlinux.org/title/Installation_guide)
4) For the initial installation, use [GRUB Bootloader](https://wiki.archlinux.org/title/GRUB#Installation)
5) Once Arch boots, install the `shim-signed` from AUR
6) Install the [rEFInd Bootloader](https://wiki.archlinux.org/title/REFInd) since it makes managing booting with Secure Boot simpler, presents a nicer boot UI and does a better job on auto-detecting available EFI binaries
7) Remove `GRUB` and clean any existing boot options using `efibootmgr`
8) Follow this [guide](https://wiki.archlinux.org/title/REFInd#Using_shim) to setup the bootloader with Secure Boot support
9) Reboot and enable secure boot to confirm everything is working properly so far
10) Follow the [installation guide](https://github.com/linux-surface/linux-surface/wiki/Installation-and-Setup#Arch) for the `linux-surface` kernel except for the `GRUB` config at the end
11) Find the `refind.conf` file (usually `{EFI/SYSTEM/PARTITION}/EFI/refind/refind.conf`) and change the following line
```
# extra_kernel_version_strings linux-lts,linux
```
to
```
extra_kernel_version_strings linux-lts,linux,linux-surface
```
