## Install Docker

``` ~$ curl -fsSl https://get.docker.com | bash   ```

To run Docker as a non-privileged user, consider setting up the  <br>
Docker daemon in rootless mode for your user:  <br>

```  apt-get install -y uidmap ``` 

Adiciona o usuario no grupo do Docker

``` ~$ dockerd-rootless-setuptool.sh install ``` 

