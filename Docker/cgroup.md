apt install cgroup-tools

cgcreate --help

cgcreate -g cpu,memory,blkio,devices,freezer:mello
ls /sys/fs/cgroup/cpu


Caso nao funcione, verificar a versao do cgroup que esta usando e altere para versao 1

sudo nano /etc/default/grub

GRUB_CMDLINE_LINUX="systemd.unified_cgroup_hierarchy=0"

sudo update-grub

sudo reboot

cgclassify -g cpu,memory,blkio,devices,freezer:mello 1157

sudo cat /sys/fs/cgroup/cpu/mello/cgroup.procs

cgset -r cpu.cfs_quota_us=1000 mello

cgset -r memory.limit_in_bytes=48m mello

cgget -r memory.limit_in_bytes mello

dd if=/dev/zero of=catota.img bs=8k count=256k