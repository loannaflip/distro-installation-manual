## Update fstab
* Edit by executing `nano /etc/fstab` and add the following:
```bash
# System #
/dev/sdx2   /boot  vfat    defaults,noatime  0 0
/dev/sdx1   /      btrfs   noatime           0 0

# TMPFS #
tmpfs /tmp     tmpfs nodev,nosuid,noatime,nodev 0 0
shm   /dev/shm tmpfs nodev,nosuid,noexec 0 0
tmpfs /var/tmp tmpfs rw,nosuid,noatime,nodev,mode=1777 0 0
tmpfs /var/tmp/portage tmpfs rw,nosuid,noatime,nodev,mode=775,uid=portage,gid=portage,x-mount.mkdir=775 0 0
```