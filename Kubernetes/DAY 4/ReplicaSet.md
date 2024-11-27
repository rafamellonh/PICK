##  O que é ReplicaSet

* ReplicaSet é um objeto usado para garantir que un número especifico de um pod esteja rodando em um determinado momento.
* Ele é responsável por mandar a quantidade desejada de replicas do pod em execução, independente de falhas ou alterações no cluster.
* Principais características.
    * Escalabilidade
    * Autocorreção
    * Seletores de rótulos
    * Integração com Deployments

* Quando usar Replicaset?
    * Embora o replicaSet possa ser usado diretamente, é mais comum usa-lo indiretamente por meio de um deployment, pois o deployment fornece mais recursos, como atualizações e rollbacks automáticos.

* Commandos :
```
kubectl scale deployment my-deployment --replicas 3
```