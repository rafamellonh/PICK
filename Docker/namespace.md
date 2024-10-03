apt install debootstrap
# cria um sistema de arquivos do debian

debootstrap stable /debian http://deb.debian.org/debian

cd /debian

#unshare é o comando que tenhamos o namespace 
unshare --help


unshare --help
unshare --mount --uts --ipc --net --map-root-user --user --pid --fork chroot /debian bash
mount -t proc none /proc
mount -t sysfs none /sys
mount -t tmpfs none /tmp

##Namespaces

Eles permitem o isolamento de processos quando estamos utilizando o Docker.

##PID namespace

O PID namespace permite que cada container tenha seus proprios identificadores de processos.

##NET namespace

O Net Namespace permite que cada container possua sua interface de rede e portas.

## Mnet namespace

Eh a evolucao do chroot. Com o Mnt namespace cada container pode ser dono de seu ponto de montagem.

## IPC namespace

Ele prove um systemV IPC isolado, alem de um fila de mensagens posix propria

## UTS namespace

Responsavel por prover o isolamento de hostname, nome de dominio, versao do SO e etc

## User namespace

Responsavel por manter o mapa de identificacao de usuarios em cada container