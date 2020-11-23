## Creating a User
```bash
- Administrative Groups:
  + adm   used for system monitoring tasks (e.g. journalctl)
  + users traditional group for identifying user accounts (versus system/daemon accounts)
  + wheel used to indicate permission to perform certain restricted operations (e.g.  su)

- Device Access Groups:
  + disk  allows access to various disk device nodes
  + usb   allows access to usb device nodes
  + audio allows access to audio device nodes
  + video allows access to video device nodes (for accelerated video)
```
* Create a user with all the permissions: `useradd -m -G adm,disk,wheel,cdrom,audio,video,usb,users username`.
* add a password for the user: `passwd username`.