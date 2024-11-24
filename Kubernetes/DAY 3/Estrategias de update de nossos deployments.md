## Estrategias de update de nossos deployments


1. RollingUpdate (padrao)

* Descrição: Atualiza os pods gradualmente, substituindo-os um por um ou em lotes
* Uso principal: Para manter alta disponibilidade durante a atualização, garantindo que sempre haja instancias funcionais do aplicativo
* Configurações adicionais:
    * maxSurge: numero ou percentual de pods adicionais que pode ser criados temporariamente além do numero desejado de replicas durante a atualização
    * maxUnavailable: numero ou percentual de pods desejados que podem estar indisponível durante a atualização

```
strategy:
  type: RollingUpdate
    maxSurge: 1  # adiciona 1 pod extra durante a atualização
    MaxUnavailable: 1  # permite que 1 pod esteja indisponível

```