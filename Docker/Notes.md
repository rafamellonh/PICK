* Fazer login no Docker Hub

``` docker login -u USER```

* Fazer o upload(push) da imagem

``` docker push rafamellonh/my-nginx:1.0  ``` 


* FROM : Especifica a imagem básica para construir un novo container<br>
* RUN : Executa comandos em uma nova camada e cria uma nova imagem<br>
* CMD : Define o comando padrão e paramentos que sera executados no container.<br>
* ENTRYPOINT : Configura um comando para ser executado como um executável<br>
* EXPOSE : Informa ao Docker que o container ira escutar em portas especificas em tempo de execução <br>
* ENV : Define uma variável de ambiente persistente para ser usada no container.<br>
* ADD : Copia arquivos e diretórios para o sistema de arquivos do container e pode descompactar arquivos locais.<br>
* COPY : Copia arquivos ou diretórios locais para o sistema de arquivos do container.<br>
* WORKDIR : Define o diretório de trabalho para as instruções RUN, CMD, ENTRYPOINT, COPY e ADD.<br>
* VOLUME : Cria um ponto de montagem de volume no container. <br>
* LABEL : Adiciona metadados a imagem, como autor , versão, ou descrição. <br>
* ARG : Define uma variável para ser usada durante a fase de construção da imagem.<br>
* USER : Define o nome do usuário ou UID para executar as instruções subsequentes.<br>
* STOPSIGNAL : Define o sinal de sistema para encerrar o container. <br>
* HEALTHCHECK : Verifica a saúde do container usando um comando especifico.<br>
* ONBUILD : Adiciona uma instrução que sera executada quando a imagem for usada como base para outra.<br>
* SHELL : Substitui o shell padrão usado nas instruções RUN, CMD e ENTRYPOINT. <br>
* MAINTAINER : (Depreciado ) Nome ou e-mail do autor da imagem.<br>
* DEPRECATED : Indica que uma instrução ou recurso é obsoleto e pode ser removido em versões futuras.<br>
* MULTISTAGE : Técnica para usar múltiplos estágios de construção para otimizar imagens.<br>
