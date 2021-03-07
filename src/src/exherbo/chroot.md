## Chrooting into Exherbo
- Mount everything for chroot by invoking the following commands:
    - `<superuser> mount -o rbind /dev /mnt/exherbo/dev/`.
    - `<superuser> mount -o rbind /sys /mnt/exherbo/sys/`.
    - `<superuser> mount -t proc none /mnt/exherbo/proc/`.

- Boot partition: `<superuser> mount /dev/sdx2 /mnt/exherbo/boot/`.

* Chroot into Exherbo: `<superuser> chroot /mnt/exherbo /bin/bash`.
* Reload the settings of `/etc/profile` in memory: `source /etc/profile`.