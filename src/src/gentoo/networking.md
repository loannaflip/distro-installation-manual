## Configuring the network
If the system has several/Different network interface check invoking `ifconfig` and set the proper network interface. Example: `eth0`, `enp2s0`, `enp3s0`.
- Edit by executing `nano /etc/conf.d/net` and add: `config_enp2s0="dhcp"`.
- Automatically start networking at boot: `cd /etc/init.d ; ln -s net.lo net.enp2s0 ; rc-update add net.enp2s0 default`