##### Volumes

[Docs - Docker](https://docs.docker.com/engine/storage/)

Volumes são diretórios externos ao container, que sao montados diretamente nele, e dessa form bypassam seu filesystem, ou seja, nao seguem aquele padrão de camadas.

A principal função do volume é persistir os dados. diferentemente do filesystem do container, que é volátil e toda informação escrita nele é perdida quando o container morre.

* Volume é inicializado quando o container é criado
* Caso ocorra de ja haver dados no diretório em que voce esta montando como volume, ou seja, se o diretório ja existe e esta populado na imagem base, aqueles dados sera copiados para o volume.
* Um volume pode ser reusado e compartilhado entre containers
* Alterações em um volume sao feitas diretamente no volume
* Volumes continuam a existir mesmo se voce deletar o container.




##### Tipos de volumes :

* [Bind](https://github.com/rafamellonh/PICK/blob/main/Docker/DAY%204/bind.md)

* [Volume](https://github.com/rafamellonh/PICK/blob/main/Docker/DAY%204/volume.md)

* Tmps