# Note
- `/dev/sdx` | `x` is your preferred disk. Check by executing the command: `df -h` or `lsblk`.
- Examples: `/dev/sda1` for root & `/dev/sda2` for boot partition respectively.

## Do the proper Partitioning in `cfdisk`
- 1 partition for `root` of any reasonable size (i.e `20GB`) [`/dev/sdx1`].
- 1 partition for `boot` of any reasonable size (i.e `100MB`) [`/dev/sdx2`].
```bash
cfdisk /dev/sdx
```

## Format the Partitions
```bash
mkfs.btrfs /dev/sdx1
mkfs.fat -F 32 /dev/sdx2
```
