## Limita o uso de memoria e cpu para os containers :


```
docker container run -d -p 8080:8080 --name my-nginx --cpus=1 nginx

docker container inspect my-nginx | grep -i cpus

docker container run -d -p 8080:8080 --name my-nginx --memory 64m nginx

docker container inspect my-nginx | grep -i memory
```