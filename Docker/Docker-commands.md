## Docker commands

```  ``` 

``` 
    docker ps 
    docker container run
    docker container ls 
    docker container ls -a
    docker container run -it ubuntu         (para sair sem matar o container user : ctrl pq)
    docker container run --name meu-container -it -d ubuntu  
    docker container stop meu-container
    docker container start meu-container
    docker container pause meu-container
    docker container rm meu-container
    docker container attach 24c8c9316a18    (conecta no container em execução)
    docker container stats
    docker container top meu-container
    docker container pause meu-container
    docker container pause meu-container
    docker container prune                  ( remove os containers que nao estão sendo executados)
    docker container rm -f test01
    docker image ls
    docker image rm hello-world
    docker container inspect test01



    docker stop $(docker ps -q)
    docker rm $(docker ps -aq)
``` 


