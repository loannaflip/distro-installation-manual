## `TMPFS`
`N` to be replaced with the amount of max ram tmpfs can access, i.e `8`.
```bash
tmpfs /var/tmp         tmpfs rw,nosuid,noatime,nodev,size=NG,mode=1777 0 0
tmpfs /var/tmp/portage tmpfs rw,nosuid,noatime,nodev,size=NG,mode=775,uid=portage,gid=portage,x-mount.mkdir=775 0 0
```