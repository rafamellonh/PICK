
```
Usuário (kubectl / API)
         (Ferramenta para interação com o cluster)
                    ↓
             ┌──────────────┐
             │ Control Plane │
             │ (Gerencia o estado do cluster) │
             └──────────────┘
                    ↓
 ┌─────────────────────────────────────────┬──────────────────────────────────────────┐
 │                                         │                                          │
┌───────────────┐                    ┌───────────────┐                         ┌───────────────┐
│ etcd (Dados)  │                    │ API Server    │                         │ Scheduler      │
│ (Banco de dados│                    │ (Interface de │                         │ (Decide em    │
│ distribuído que│                    │ comunicação)  │                         │ qual nó os    │
│ armazena o    │                    └───────────────┘                         │ pods serão    │
│ estado do     │                                                              │ executados)   │
│ cluster)      │                                                              └───────────────┘
└───────────────┘
                                       ↓
                               ┌────────────────┐
                               │ Controller     │
                               │ Manager        │
                               │ (Gerencia o    │
                               │ ciclo de vida  │
                               │ dos recursos)  │
                               └────────────────┘
                                       ↓
                              ┌─────────────────┐
                              │ Cloud Provider  │
                              │ (Integra com    │
                              │ provedores de   │
                              │ infraestrutura) │
                              └─────────────────┘
                                       ↓
                               ┌────────────────┐
                               │ Worker Nodes   │
                               │ (Máquinas que  │
                               │ executam as    │
                               │ aplicações)    │
                               └────────────────┘
                                       ↓
             ┌──────────────────────┬──────────────────────┐
             │                      │                      │
      ┌────────────┐         ┌────────────┐         ┌────────────┐
      │ Kubelet    │         │ Kubelet    │         │ Kubelet    │
      │ (Agente    │         │ (Agente    │         │ (Agente    │
      │ que garante│         │ que garante│         │ que garante│
      │ que os pods│         │ que os pods│         │ que os pods│
      │ estão rodando) │      │ estão rodando) │      │ estão rodando) │
      └────────────┘         └────────────┘         └────────────┘
             ↓                      ↓                      ↓
      ┌────────────┐         ┌────────────┐         ┌────────────┐
      │ Kube Proxy │         │ Kube Proxy │         │ Kube Proxy │
      │ (Gerencia  │         │ (Gerencia  │         │ (Gerencia  │
      │ o tráfego  │         │ o tráfego  │         │ o tráfego  │
      │ de rede)   │         │ de rede)   │         │ de rede)   │
      └────────────┘         └────────────┘         └────────────┘
             ↓                      ↓                      ↓
          ┌────────────┐        ┌────────────┐        ┌────────────┐
          │   Pods     │        │   Pods     │        │   Pods     │
          │ (Unidade   │        │ (Unidade   │        │ (Unidade   │
          │ básica do  │        │ básica do  │        │ básica do  │
          │ Kubernetes)│        │ Kubernetes)│        │ Kubernetes)│
          └────────────┘        └────────────┘        └────────────┘
Explicação dos novos componentes:
Cloud Provider: Este componente é responsável por integrar o Kubernetes com provedores de infraestrutura como AWS, Google Cloud, Azure, etc. Ele é usado para criar e gerenciar os recursos do cluster, como nós de trabalho e volumes de armazenamento, de forma automatizada.
Worker Nodes: Esses nós executam os pods. Cada worker node tem seus próprios componentes, como o Kubelet (que garante que os pods estejam rodando) e o Kube Proxy (que gerencia o tráfego de rede).
Componentes adicionados:
API Server: Interface de comunicação com o cluster.
Scheduler: Decide em qual nó os pods serão executados.
Controller Manager: Gerencia o ciclo de vida dos recursos do Kubernetes.
etcd: Banco de dados distribuído para armazenar o estado do cluster.
Cloud Provider: Integra com provedores de infraestrutura.
Kubelet: Garante que os pods estejam rodando nos nós.
Kube Proxy: Gerencia o tráfego de rede.
Pods: Unidade básica do Kubernetes onde os contêineres são executados.
```