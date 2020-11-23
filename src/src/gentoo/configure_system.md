## Configuring the system
- Set root password: `passwd`.
- Add the language environment `en_US.UTF-8`: `echo "en_US.UTF-8 UTF-8" > /etc/locale.gen`.
- Generate locales specified in `/etc/locale.gen`: `locale-gen`.
- Set the locale: `eselect locale set en_US.utf8`.
- Reload the environment: `env-update ; source /etc/profile`.
- Set system timezone: `ln -s /usr/share/zoneinfo/Asia/Dhaka /etc/localtime`.
- Reconfigure the `timezone-data` package: `emerge --config sys-libs/timezone-data`.
- Install `mlocate` (provides faster file location capabilities): `emerge -q sys-apps/mlocate`.