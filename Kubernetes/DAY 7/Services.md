## Services

* Service é um recurso que fornece uma maneira de expor um conjunto de Pods como um único endpoint de rede. Ele abstrai e gerencia o acesso aos pods, garantindo que as aplicações possam se comunicar de forma confiável, mesmo que os pods subjacentes sejam recriados, escalados ou migrados para outros nós.

## Tipos de services

* ClusterIP : Expõe o serviço apenas dentro do cluster, tornando-o acessível por outros recursos internos.
* NodePort : Expõe o serviço em uma porta especifica em todos os nos do cluster, permitindo acesso externo.
* LoadBalancer : Usa um balanceador de carga externo (geralmente no provedor de nuvem) para expor o serviço ao mundo exterior.
* ExternalName : mapeia um nome DNS externo para um service dentro do Cluster.
* Ingress (complementar) : Embora tecnicamente nao seja um service, é usado para gerenciar a entrada de trafego HTTP/HTTPS com regras mais complexas.


## Exemplos

```
kubectl create deployment nginx --image nginx --port 80
kubectl expose deployment nginx
kubectl expose deployment nginx --type NodePort
kubectl expose deployment nginx --type LoadBalancer
kubectl create service externalname mello-db --external-name db.mello.com.br

```