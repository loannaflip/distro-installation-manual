## Updating the system
* Add some necessary repositories before syncing/updating: `cave resolve -x repository/{perl,python,gnome,x11,hardware}`.
* Sync all the trees by invoking: `cave sync`.
* Upgrade/Update necessary packages by executing: `cave resolve world -x`.