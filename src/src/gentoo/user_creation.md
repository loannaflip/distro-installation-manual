## Creating a User
```
audio 	 Be able to access the audio devices.
cdrom 	 Be able to directly access optical devices.
floppy 	 Be able to directly access floppy devices.
games 	 Be able to play games.
portage  Be able to access portage restricted resources.
usb      Be able to access USB devices.
video 	 Be able to access video capturing hardware and doing hardware acceleration.
wheel 	 Be able to use su.
```
* Create a user with all the permissions: `useradd -m -G users,wheel,audio,video,usb -s /bin/bash username`.
* add a password for the user: `passwd username`.