## Componentes dos Workers

* Kubelet ele é o agente do kubernetes dentro do nó (worker node), temos um em cada um dos nodes.
    * Aplica o estado desejado, recebe as instruções do kube-apiserver sobre quais pods devem ser executados no nó.
    * Gerencia containers
    * Relata o estado do nó.
    * Le especificações de pod.
    * Valida a saúde e monitora para garantir que os pods e containers estejam funcionando

* Kube-proxy é quem vai fazer a comunicação dos pods com tudo, todo worker node tem um
