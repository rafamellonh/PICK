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
