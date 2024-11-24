## Fazendo Rollback e conhecendo o comando Rollout

* Rollback é o processo de desfazer uma mudança ou atualização para restaurar um sistema, aplicativo ou infraestrutura para um estado anterior.

* O comando Rollout é utilizado para gerenciar e controlar o processo de implantação de versões de aplicações ou atualizações em um sistema, como no 
kubernetes ou Docker Compose. O rollout pode ser usado para inciar, verificar o status ou reverter implantações.
* No kubernetes, o comando kubectl rollout é comumente usado para gerenciar o ciclo de vida de atualizações de deployments, como a implantação de novos
pods ou containers. Alguns dos comandos mais utilizados : 

```
# Exibe o status de uma implantação para garantir que a nova versão da aplicação foi aplicada
kubectl rollout status deployment/nome-do-deployment 

# Reverte a implantação para a versão anterior, essencialmente realizando um rollback
kubectl rollout undo deployment/nome-do-deployment
```


```
kubectl rollout history deployment nginx-deployment --revision 2


deployment.apps/nginx with revision #3
Pod Template:
  Labels:       app=nginx-deployment
        pod-template-hash=86cf486457
  Containers:
   nginx:
    Image:      nginx:1.15.0
    Port:       <none>
    Host Port:  <none>
    Limits:
      cpu:      500m
      memory:   256Mi
    Requests:
      cpu:      300m
      memory:   64Mi
    Environment:        <none>
    Mounts:     <none>
  Volumes:      <none>
  Node-Selectors:       <none>
  Tolerations:  <none>

  
```
