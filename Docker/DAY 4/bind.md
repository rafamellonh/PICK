Diretorio padrao

``` /var/lib/docker/volumes/ ```  

* Exemplo simples : 

```

docker run -d \
  --name devtest \
  --mount source=myvol2,target=/app \
  nginx:latest

```

``` docker run -it --name test-volumes --mount type=bind,source=/home/rafael,target=/teste-volumes debian ```

* Alterando as permissões para somente leitura :

``` docker run -it --name test-volumes --mount type=bind,source=/home/rafael,target=/teste-volumes,ro debian ```    

##### Versão antiga mas ainda funcional

Essa maneira é muito utilizada quando se quer montar um diretório especifico do host dentro do container. Isso é ruim quando estamos trabalhando com cluster, uma vez que teríamos que garantir esse diretório criado em todos os hosts do cluster.

Porem, podemos aprender como funciona e utilizar em algum momento, caso se faca necessário. Para evitar erros, primeiro crie o diretório ```/volume ``` na sua maquina.

``` # mkdir /volume ``` <br>
``` docker container run -it --mount type=bind,src=/volume,dst=volume ubuntu ``` <br>

``` 
root@7db02e999bf2:/# ls
bin boot dev etc home lib lib64 media mnt opt proc root run sbin srv sys tmp usr var volume 

```

* No exemplo anterior, conhecemos um novo paramentro do conmando ``` docker container run ``` ,  o ``` --mount```

* O parâmetro ```--mount``` é o responsável por indicar o volume, que nosso exemplo é o ``` /volume ```, e onde ele sera montando no container. Perceba que, quando passamos o parâmetro ```--mount type=bind,src=/volume,dst=/volume```  , o Docker montou esse diretório no container, proem se nenhum conteúdo.

* Podemos também montar um volume no container linkando-o com um diretório do host ja com algum conteúdo. Para exemplificar, vamos compartilhar o diretório ```/root/primeiro_container ``` , que utilizamos para guardar o nosso primeiro dockerfile, e monta-lo no container em um volume chamado ``` /volume ``` da seguinte forma : 

``` # docker container run -ti --mount type=bind,src=/root/primeiro_container,dst=/volume ubuntu ```

```

root@3d372a410ea2:/# df -h
Filesystem                   Size Used Avail  Use%  Mounted on
none                          13G 6.8G  5.3G   57%  /
tmpfs                        999M    0  999M    0%  /dev
tmpfs                        999M    0  999M    0%  /sys/fs/cgroup
/dev/mapper/ubuntu--vg-root   13G 6.8G  5.3G   57%  /volume
shm                           64M    0   64M    0%  /dev/shm

root@3d372a410ea2:/#

```

