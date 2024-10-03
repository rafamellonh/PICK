## Install Docker

``` ~$ curl -fsSl https://get.docker.com | bash   ```

To run Docker as a non-privileged user, consider setting up the 
Docker daemon in rootless mode for your user:
``` ~$ dockerd-rootless-setuptool.sh install ``` 