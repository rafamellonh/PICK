## Control plante

* É a parte que gerencia o cluster e toma decisões sobre a execução de containers. Ele é responsável pela cordeação e gerenciamento do estado 
desejado do cluster. Principais funções : 
    * API Server
    * Scheduler
    * Controller manager
    * Etcd


## Worker nodes 

* Sao os nodes onde as cargas de trabalho, ou containers (pods), realmente rodam. Cada worker node contem os componentes necessarios para executar os pods :
    * Kubelet
    * Container runtime
    * Kube proxy
