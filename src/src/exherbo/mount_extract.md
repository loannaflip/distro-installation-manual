## Mounting & Extracting Exherbo Tarball Stage
- Create a mount directory for mounting root partition: `<superuser> mkdir /mnt/exherbo`.
- Mount root directory in `/mnt/exherbo`: `<superuser> mount /dev/sdx1 /mnt/exherbo`.
- Change into the mounted directory: `cd /mnt/exherbo`.
- Download the latest Exherbo Tarball Stage: `<superuser> wget https://dev.exherbo.org/stages/exherbo-x86_64-pc-linux-gnu-current.tar.xz`.
- Extract the tarball: `<superuser> tar xJpf exherbo-x86_64-pc-linux-gnu-current.tar.xz`.
