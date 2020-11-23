## Configuring DNS
- Change live system's DNS: `<superuser> nano /etc/resolv.conf` and add the following:
```bash
nameserver 8.8.8.8 # Google
nameserver 1.1.1.1 # Cloudflare
```