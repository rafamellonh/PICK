#Imagem que sera usada no container
FROM ubuntu:18.04

# RUN executa um comando quando a imagem de container esta sendo criada, da RUN executado eh uma camada
# RUN apt update && apt install nginx -y && rm -rf /var/lib/apt/lists/*
RUN apt update && apt install nginx -y 

# A Porta do container que estara aberta
EXPOSE 80

# Copia um arquivo para dentro do container
COPY index.html /var/www/html/

# Executa um comando quando o container estiver pronto
CMD [ "nginx","-g","daemon off;" ]

# Local padrao que voce ira cair apos entrar no container
WORKDIR /var/www/html

# variaveis de ambiente no container
ENV APP_VERSION 1.0.0



