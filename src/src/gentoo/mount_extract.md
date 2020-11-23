## Mounting & Extracting Gentoo Tarball Stage
- Create a mount directory for mounting root partition: `<superuser> mkdir /mnt/gentoo`.
- Mount root directory in `/mnt/gentoo`: `<superuser> mount /dev/sdx1 /mnt/gentoo`.
- Change into the mounted directory: `cd /mnt/gentoo`.
- Get the latest stage3 tarball download link from <a href=https://www.gentoo.org/downloads/>gentoo.org/downloads</a>
- Download the latest Gentoo Stage 3 tarball: `wget https://www.direct-download-link...`.
- Extract the tarball: `<superuser> tar xpvf stage3-*.tar.xz --xattrs-include='*.*' --numeric-owner`.