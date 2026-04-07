```bash
$fat.py rootfs.squashfs
```
Once emulation is done, create a port forward on your machine using SSH as follows:
```shell
$ssh -N user@ip -L 8081:192.168.0.100:port
```
