## Update fstab
* Edit by executing `nano /etc/fstab` and add the following:
```bash
# System #
/dev/sdx2   /boot  vfat    defaults,noatime  0 0
/dev/sdx1   /      btrfs   noatime           0 0