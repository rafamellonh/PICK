## Componentes do Control Plane

* etcd : Ele é um banco de dados que guarda todo o estado, todas as informações do cluster. Ele so se comunica com </br>
o Kube APIServer

* Kube APIServer : Ele é responsável por intermediar a comunicação entre os usuários, ferramentas externas e outros componentes</br>
internos do cluster. Ele é cérebro, sem ele o kubernetes nao pode funcionar.
    * Todas as solicitações para criar, atualizar, excluir ou consultar objetos do kubernetes, como pods, services ou deployments </br>
    passam por ele. 
    * Expõe uma API RESTful que pode ser acessada usando comandos como kubectl, bibliotecas client do kubernetes ou chamadas diretas via </br>
    HTTP/HTTPS.
    * Verifica se as solicitações feitas pelos usuários ou sistemas sao validas.
    * Gerencia a autenticação dos usuários e verifica se a ação é permitida com base em permissões configuradas no cluster.
    * Interage com outros componentes como : kube-controller-manager e o kube-scheduler.
    * Pode ser configurado em um modo high-availability.

* Kube-Scheduler é um componente essencial responsável por decidir em qual nó (ou worker node) os pods recém criados devem server executados.
    * Identifica pods sem nó atribuído
    * Toma decisões baseadas em politicas de escalonamento
        * Capacidade de recursos : CPU, memoria e armazenamento disponível
        * Afinidade e anti-afinidades
        * Restrições de tolerâncias e taints
        * Distribuição de carga
    * Executar a decisão de escalonamento
    * Garantir alta performance e eficiência
