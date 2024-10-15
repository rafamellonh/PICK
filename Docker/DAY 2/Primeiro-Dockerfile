#Imagem que sera usada no container
FROM ubuntu:18.04

# RUN executa um comando quando a imagem de container esta sendo criada, da RUN executado eh uma camada
RUN apt update && apt install nginx -y 

# A Porta do container que estara aberta
EXPOSE 80

# Executa um comando quando o container estiver pronto
CMD [ "nginx","-g","daemon off;" ]


