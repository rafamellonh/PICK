##### Criando volumes

* Agora vamos criar os volumes da maneira mais elegante e atual. Hoje temos a possibilidade de realizar o gerenciamento de volumes de maneira muito simples e inteligente.

Sempre que criamos um volume, ele cria um diretório com o mesmo nome dentro de ``` /var/lib/docker/volumes```.

No exemplo a seguir, o volume ``` giropops ``` seria então criado em ```/var/lib/docker/volumes/giropops``` , com isso, todos os arquivos disponíveis nesse diretório também estariam no local indicado no container. Vamos aos exemplos : 

* É possível fazer a criação de volumes e toda a sua administração através do comando : 

```
# docker volume create giropops

```

* É possível remove-lo através do comando : 

```
# docker volume rm giropops

```

* Para verificar detalhes sobre esse volume

```
# docker volume inspect giropops

```

* Para remover os volumes que nao estão sendo utilizados (use com extrema moderação)

```
# docker volume prune

```

* Para que voce possa montar o volume criado em algum container/service, baste executar o seguinte comando :

```

# docker container run -d --mount type=volume,source=giropops,destination=/var/opa/= nginx

```

* Onde : 
    * ``` --mount ``` : Comando utilizado para montar volumes
    * ``` type=volume ```: Indica que o tipo é ```volume```. Ainda existe o tipo ```bind```, onde, em vez de indicar um volume, voce indicaria um diretório como source.
    * ```source=giropops``` : Qual o volume que pretendo montar
    * ```destination=/var/opa ``` : Onde no container montarei esse volume.


##### Localizando volumes

* Caso você queira obter a localização do seu volume, é simples. Mas para isso você precisa conhecer o comando ``` docker volume inspect ```.

Com o ```docker volume inspect ``` voce consegue obter detalhes do seu container, como, por exemplo : detalhes do volume.

A Saida do comando ``` docker volume inspect ``` retorna mais informações do que somente o path do diretório no host. Vamos user a opção ``` --format ``` ou ```-f``` para filtrar a Saida do  ```inspect```.

```
docker volume inspect --format '{{ .Mountpoint }}' giropops
/var/lib/docker/volumes/giropopos/_data

```
