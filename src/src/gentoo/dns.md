## Configuring DNS
- Change live system's DNS:
```bash
printf "%s\n" "nameserver 8.8.8.8 # Google" > /etc/resolv.conf
printf "%s\n" "nameserver 1.1.1.1 # Cloudflare" >> /etc/resolv.conf
```