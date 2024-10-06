## Dockerfile

Sempre o nome do arquivo deve ser ```Dockerfile``` 

# Exemplo01 de ```Dockerfile``` 

``` 
FROM debian:10

RUN apt-get update && apt-get install -y apache2 && apt-get clean

ENV APACHE_LOCK_DIR="/var/lock"

ENV APACHE_PID_FILE="/var/run/apache2.pid"

ENV APACHE_RUN_USER="www-data"

ENV APACHE_RUN_GROUP="www-data"

ENV APACHE_LOG_DIR="/var/log/apache2"

LABEL description="Webserver"

VOLUME /var/www/html/

EXPOSE 80

``` 

# Detalhes

FROM :  indica a imagem a servir como base <br>
RUN : Lista de comandos que deseja executar na criação da image <br>
ENV : Define variáveis de ambiente <br>
LABEL : Adiciona metadata a imagem, como descrição, versão e etc,<br>
VOLUME :  Define um volume a ser montado no container 

# Buildar a imagem

``` docker image build -t nome-da-image . ```


# Exemplo01 de ```Dockerfile``` 

```
FROM debian:10

RUN apt-get update && apt-get install -y apache2 && apt-get clean

ENV APACHE_LOCK_DIR="/var/lock"

ENV APACHE_PID_FILE="/var/run/apache2/apache2.pid"

ENV APACHE_RUN_USER="www-data"

ENV APACHE_RUN_DIR="/var/run/apache2"

ENV APACHE_RUN_GROUP="www-data"

ENV APACHE_LOG_DIR="/var/log/apache2"

LABEL description="Webserver"

VOLUME /var/www/html/

EXPOSE 80

ENTRYPOINT ["/usr/sbin/apachectl"]

CMD ["-D", "FOREGROUND"]


```

# Detalhes

ADD : Copia novos arquivos, diretórios, arquivos TAR ou arquivos remotos e os adiciona ao filesystem do container<br>
CMD : Executa um comando. Diferentemente do RUN, que executa o comando no momento em que esta "buildando" a image <br>
o CMD ira fazer-lo somente quando o container é iniciado.<br>
LABEL : Adiciona metadados a imagem, como versão, descrição e fabricante. <br>
COPY : Copia novos arquivos e diretórios e os adiciona ao filesystem do container.<br>
ENTRYPOINT : Permite que voce configure um container para rodar um executável. Quando esse executável for finalizado<br>
o container também sera.<br>
ENV : Informa variáveis de ambiente ao container.<br>
EXPOSE : Informa qual porta o container estará ouvindo. <br>
FROM : Indica qual imagem sera utilizada como base. Eal precisa ser a primeira linha do dockerfile. <br>
MAINTEINAR : Autor da imagem.<br>
RUN : Executa qualquer comando em uma nova camada no topo da imagem e "commita" as alterações. Essas alterações voce poderá <br>
utilizar nas próximas instruções de seu dockerfile.<br>
USER : Determina qual usuário sera utilizado na imagem. Por default é o root.<br>
VOLUME : Permite a criação de um ponto de montagem no container. <br>
WORKDIR : Responsável por mudar do diretório / para o especificado nele.

Um detalhe importante é que quando utilizamos o ENTRYPOINT e o CMD dentro do mesmo dockerfile, o CMD somente aceita paramentos <br>
do ENTRYPOINT.

```

ENTRYPOINT ["/usr/sbin/apachectl"]

CMD ["-D", "FOREGROUND"]


```

* "/usr/sbin/apachectl" -- Esse é o comando.

* "-D", "FOREGROUND" -- Esse é o argumento, o parâmetro.