###### Volumes

Volumes sao diretorios externos ao container, que sao montados diretamente nele, e dessa form bypassam seu filesystem, ou seja, nao seguem aquele padrao de camadas.

A principal funcao do volume é persistir os dados. diferentemente do filesystem do container, que é volatil e toda informacao escrita nele é perdida quando o container morre.

* Volume é inicializado quando o container é criado
* Caso ocorra de ja haver dados no diretorio em que voce esta montando como volume, ou seja, se o diretorio ja existe e esta populado na imagem base, aqueles dados sera copiados para o volume.
* Um volume pode ser reusado e compartilhado entre containers
* Alteracoes em um volume sao feitas diretamente no volume
* Volumes continuam a existir mesmo se voce deletar o container.