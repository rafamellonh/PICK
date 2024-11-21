## Networks no Docker :

[Docker Docs](https://docs.docker.com/engine/network/drivers/)


* docker network --help

```  
docker network create -d macvlan giropops  
docker container run -d --network giropops-senhas -p 6379:6379 --name redis-local redis 
docker container run -d --network giropops-senhas -p 5000:5000 --name giropops giropops-senhas:1.0
docker container run -d --network giropops-senhas -p 5000:5000 --env REDIS_HOST=redis-local --name giropops giropops-senhas:1.0
``` 