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
