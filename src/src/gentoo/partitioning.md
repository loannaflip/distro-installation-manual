## Prepare the storage drives
Create a boot and root partition of any size. Recommended at-least `300MB` for boot & `40GB` for root partition.
- NOTE: `<superuser>` -> `sudo`/`doas` or `X`.
* Prepare them: `<superuser> cfdisk /dev/sdx` (`x` is your preferred storage. Check by executing the command: `df -h` or `lsblk`).
* Format the filesystems for each partition:
    - root partition: `<superuser> mkfs.btrfs /dev/sdx1`.
    - boot partition: `<superuser> mkfs.vfat -F32 /dev/sdx2`.
