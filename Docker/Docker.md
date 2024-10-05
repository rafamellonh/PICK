## Install Docker

``` ~$ curl -fsSl https://get.docker.com | bash   ```

To run Docker as a non-privileged user, consider setting up the  <br>
Docker daemon in rootless mode for your user:  <br>

Adiciona o usuario no grupo do Docker

```  apt-get install -y uidmap ``` <br>
``` ~$ dockerd-rootless-setuptool.sh install ``` 

