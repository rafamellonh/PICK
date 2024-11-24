## Criando um deployment

* Criar arquivo deployment.yml :
``` 
vi deployment.yml
``` 

* Criar deployment :
``` 
kubectl apply -f deployment.yml
``` 

* Verificar deployments :
``` 
kubectl get deployments
kubectl get deployments.NOME-DEPLOYMENT -o yaml
``` 

* Atualizar um deployment :
``` 
kubectl set image deployment/minha-aplicacao meu-container=nginx:1.2
``` 
* Escalar um deployment :
``` 
kubectl scale deployment/minha-aplicacao --replicas=5
``` 

* Reverter um deployment :
``` 
kubectl rollout undo deployment/minha-aplicacao
``` 

* Comandos
``` 
kubectl describe deployments.apps nginx 

``` 