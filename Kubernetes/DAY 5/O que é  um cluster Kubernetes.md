## O que é um cluster Kubernetes

* Um cluster Kubernetes é um conjunto de maquinas (nós) configuradas para trabalhar juntas para executar e gerenciar aplicativos em containers.
* Componentes de um Cluster Kubernetes :
    * Master Node ( nó mestre )
        * Responsável por gerenciar e controlar o cluster
        * Principais componentes : 
            * API Server 
            * Controller Manager
            * Scheduler
            * ETCD
    * Worker Nodes (nós de trabalho) :
        * Executam os containers das aplicações
        * Principais componentes
            * Nubele
            * Kube-proxy
            * Container Runtime
    * Pods :
        * Menor unidade de execução no Kubernetes
        * Contem um ou mais containers que compartilham recursos como rede e armazenamento
    * Services :
        * Abstração que expõem os Pods e permitem comunicação interna e externa ao cluster


* Benefícios de usar um Cluster Kubernetes
    * Escalabilidade automática
    * Tolerância a falhas
    * Gerenciamento simplificado
    * Portabilidade