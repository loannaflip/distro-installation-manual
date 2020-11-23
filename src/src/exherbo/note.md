# Note
This guide uses Heavily Optimized <a href=https://paludis.exherbo.org/>Paludis</a> Config, thus some **packages May Break**.

## This guide uses
* Latest x86_64 Exherbo Stage
* Linux Kernel (ck)
* GNU userland
* Systemd (init system)
* Grub2 & EFISTUB (Booting Methods)
* Glibc (C standard library)
* Openssl (cryptography library)
* pulseaudio (sound server)
* Aggressive `-Ofast` GCC optimization
* LOCALE: `en_US.utf8`
* BTRFS filesystem for Root partition (no separate home partition)
* EFI (vfat/fat32) for Boot partition
* Disabled Tests & debugging