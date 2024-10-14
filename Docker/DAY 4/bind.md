Diretorio padrao

``` /var/lib/docker/volumes/ ```  

```

docker run -d \
  --name devtest \
  --mount source=myvol2,target=/app \
  nginx:latest

```

``` docker run -it --name test-volumes --mount type=bind,source=/home/rafael,target=/teste-volumes debian ```

* Alterando as permissões para somente leitura :

``` docker run -it --name test-volumes --mount type=bind,source=/home/rafael,target=/teste-volumes,ro debian ```    

##### Versao antiga mas ainda funcional

Essa maneira é muito utilizada quando se quer montar um diretório especifico do host dentro do container. Isso é ruim quando estamos trabalhando com cluster, uma vez que teríamos que garantir esse diretório criado em todos os hosts do cluster.

Porem, podemos aprender como funciona e utilizar em algum momento, caso se faca necessário. Para evitar erros, primeiro crie o diretório ```/volume ``` na sua maquina.

``` # mkdir /volume ``` <br>
``` docker container run -it --mount type=bind,src=/volume,dst=volume ubuntu ``` <br>
``` root@7db02e999bf2:/# ls
bin boot dev etc home lib lib64 media mnt opt proc root run sbin srv sys tmp usr var volume ```