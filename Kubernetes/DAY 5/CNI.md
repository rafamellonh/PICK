## O que é CNI?

* Container Network Interface é um padrão e conjunto de especificações utilizados para gerenciar redes em containers.
* Seu objetivo principal é permitir que os containers em execução em um cluster obtenham conectividade de rede de forma consistente e que as interfaces de rede possam ser criadas, configuradas e destruídas conforme necessário.
* Ele é compostos por dois componentes principais :
    * Plugins
    * Especificares

## Ciclo de vida rede com CNI

* Quando um container é criado, o orquestrador chama o plugin CNI para configurar a rede.
    * Criação do container
        * O orquestrador solicita ao plugin CNI que configure uma interface de rede para o container
        * O plugin cria e configura a interface de rede 
    * Atualização 
        * Durante a vida util do container, o plugin pode ser chamado para atualizar configurações, como politicas de segurança ou rotas
    * Remoção do container
        * Quando o container é removido, o plugin CNI é chamado para limpar a configuração de rede
* Principais Plugins de Rede CNI
    * Flannel
    * Calico
    * Weave Net
    * Cillium
    * Multus