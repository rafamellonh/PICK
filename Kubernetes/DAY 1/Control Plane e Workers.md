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


## Fluxograma :

* Control plane 
    * API Server : Recebe todas as requisições de usuários como comandos do kubectl ou de outros componentes e os encaminha para os módulos apropriados.
    * Controller manager : Garante que o estado desejado do cluster seja manindo, por exemplo, ajustando o numero de replicas dos pods.
    * Scheduler : Escolhe o nó (worker node) onde os pods devem ser executados, com base em recursos disponíveis e requisitos do pod.
    * etcd : Armazena todos os dados do cluster, incluindo configurações e informações sobre o estado dos objetos do Kubernetes, como pods, services e deployments.

* Worker node 
    * Kubelet : Um agente que roda em cada worker node. Ele se comunica com o control plane e garante que os containers do pod sejam executados conforme desejado.
    * kube-proxy : Mantém a rede entre os pods e garante a conectividade entre os serviços no cluster.
    * Container runtime : O software que executa os containers. Ex Docker ou Containerd

* Fluxo de dados
    * O usuario envia um comando para o API Server (Control plane)
    * O scheduler decide em qual worker node o pod sera executado
    * O kubelet no worker node recebe a tarefa e garante que o container esteja rodando.
    * O controller manager no control plane mantém o estado desejado dos pods em todo o cluster.
    * O kube-proxy gerencia o trafego de rede e a comunicação entre os serviços e pods.