## Container engine

* Ele é responsável por gerenciar, executar e orquestrar containers em um sistema. Por é responsável por fazer que tenhamos todo o ambiente </br>
necessário para a execução de containers.

* Funções do container engine :
    * Execução de container : Cria e gerencia os ciclos de vida dos containers, garantindo seu funcionamento.

* Isolamento : 
    * Utiliza tecnologias como namespace, chrgroups para garantir que os containers sejam isolados uns dos outros e do sistema.

* Gerenciamento de imagens: 
    * Permite download, armazenamento em cache e controle de versões de imagens de containers.

* Portabilidade : 
    * Os containers criados em uma Engine geralmente podem ser executados em qualquer sistema que suportem o mesmo padrão.

* Orquestração e Escalabilidade : 
    * Trabalha em conjunto com orquestradores como o Kubernetes ou Docker Swarm para gerenciar vários container em diferentes hosts.


* Nao se comunica com o Kernel, quem faz essa comunicação é o container runtime.

    * Temos o Docker e o Pod