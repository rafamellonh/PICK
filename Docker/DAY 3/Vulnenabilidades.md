##### Vulnerabilidades

Utilizamos vários aplicativos para testar nossas imagens, um exemplo é o [Trivy](https://trivy.dev/)

Para instalar no Ubuntu siga os passos abaixo :

[Fonte](https://aquasecurity.github.io/trivy/v0.56/getting-started/installation/)


```
sudo apt-get install wget apt-transport-https gnupg
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb generic main" | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy
```

Para verificar uma imagem : <br>
``` trivy image NOME-DA-IMAGEM ```


##### Docker Scout

[Fonte](https://docs.docker.com/scout/quickstart/)