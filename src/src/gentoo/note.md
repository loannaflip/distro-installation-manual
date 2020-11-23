# Note
This guide uses Heavily Optimized <a href=https://wiki.gentoo.org/wiki/Portage>Portage</a> Config, thus some **packages May Break** (unlikely). User can change the config or borrow/cherry-pick information(s) from this guide to fit their personal needs. The portage configuration is based of my own personal system's portage config. 


## This guide uses
* Gentoo Stage 3
* Linux Kernel (pf & ck)
* GNU userland
* Openrc/sysinit (init system)
* Sysklogd (system logger)
* Grub2 & EFISTUB (Booting Methods)
* Glibc (C standard library)
* Openssl (cryptography library)
* pulseaudio (sound server)
* `-03` GCC optimization
* LOCALE: `en_US.utf8`
* xinerama (multi-monitor support)
* tcmalloc (Fast, multi-threaded `malloc` implementation)
* AMD64 Desktop Profile (17.1) with other use-flags
* BTRFS filesystem for Root partition (no separate home partition)
* EFI (vfat/fat32) for Boot partition
* Global optimization use flags enabled: `graphite`, `lto` & `pgo`
* True 64 Bit applications (no multilib support)
* TMPFS
* Disabled Tests & debugging
* Performance focused (Non-hardened system)
* Disabled Wireless and additional devices functionality (i.e bluetooth, printing, WIFI, joystick)