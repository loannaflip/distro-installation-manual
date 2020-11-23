## Setup Bootloader (`GRUB`)
```bash
pacman -S grub efibootmgr --noconfirm
mkdir /boot/efi
mount /dev/sdx2 /boot/efi
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=GRUB
grub-mkconfig -o /boot/grub/grub.cfg
```