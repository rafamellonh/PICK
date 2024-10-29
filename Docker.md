##### Install Docker

``` ~$ curl -fsSl https://get.docker.com | bash   ```

To run Docker as a non-privileged user, consider setting up the  <br>
Docker daemon in rootless mode for your user:  <br>

Adiciona o usuário no grupo do Docker

```  apt-get install -y uidmap ``` <br>
``` ~$ dockerd-rootless-setuptool.sh install ``` 

##### Dockerfile

Dockerfile é um script de texto que contém uma serie de instruções usadas pelo docker para criar uma image de container. <br>
Essas instruções definem o ambiente, as configurações e os comandos necessários para criar um container que possa ser executado <br>
em qualquer sistema que suporte docker

##### EntryPoint

É o principal processo dentro do container

##### Distroless 

É a ideia de nao ter uma imagem base. https://images.chainguard.dev/

##### Vulnerabilidades 

- [Documentação para Vulnerabilidades ](https://github.com/rafamellonh/PICK/blob/main/Docker/DAY%203/Vulnenabilidades.md)


Utilizamos vários aplicativos para testar nossas imagens, um exemplo é o Trivy e o Docker Scout

##### Assinar as images

Por questões de segurança, podemos assinar nossas imagens com o Cosign.
