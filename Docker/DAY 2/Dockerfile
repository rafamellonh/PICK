#Imagem que sera usada no container
FROM ubuntu:18.04

# Informa alguma info 
LABEL maintainer="Rafael Mello"

# RUN executa um comando quando a imagem de container esta sendo criada, da RUN executado eh uma camada
# RUN apt update && apt install nginx -y && rm -rf /var/lib/apt/lists/*
RUN apt update && apt install nginx curl -y 

# SHELL : Define o shell padrao
SHELL [ "/bin/bash" ]

# A Porta do container que estara aberta
EXPOSE 80

# Com o ADD podemos pegar arquivos da internet, fazer download, pegar um arquivo compactado (somente se for da maquina local, da internet so faz o download)
ADD consul_exporter-0.12.1.darwin-amd64.tar.gz /root/node-exporter

# Copia um arquivo para dentro do container
COPY index.html /var/www/html/

# Local padrao que voce ira cair apos entrar no container
WORKDIR /var/www/html

# variaveis de ambiente no container
ENV APP_VERSION 1.0.0

# define uma variavel que é usada apenas durante a construcao da imagem
ARG APP_PORT=8080

#Principal processo, se ele parar o container tambem para, executa um comando de inicializacao do container 
# pode user um scrip para executar varios acoes
ENTRYPOINT [ "nginx" ]

# Executa um comando quando o container estiver pronto
CMD [ "-g","daemon off;" ]

# Criar o usuario que sera usado na opcao USER
RUN useradd rafaelmello

# Usuario que sera utilisado para executar os processos dentro do container.
USER rafaelmello

# Volume
VOLUME [ "/dados" ]

# Valida se o container esta saldavel
HEALTHCHECK --interval=10s --timeout=3s --start-period=5s --retries=3 CMD curl -f http://localhost || exit


