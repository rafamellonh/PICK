## Dockerfile

Sempre o nome do arquivo deve ser ```Dockerfile``` 

Exemplo de ```Dockerfile``` 

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