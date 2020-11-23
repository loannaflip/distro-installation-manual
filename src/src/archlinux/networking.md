## Install Networking
```bash
pacman -S networkmanager --noconfirm
```

## Enable Networking at boot
```bash
systemctl enable NetworkManager.service
```