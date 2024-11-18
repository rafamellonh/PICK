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
      │ Kube Proxy │         │ Kube Proxy │         │ Kube Proxy │
      │ (Gerencia  │         │ (Gerencia  │         │ (Gerencia  │
      │ o tráfego  │         │ o tráfego  │         │ o tráfego  │
      │ de rede)   │         │ de rede)   │         │ de rede)   │
      │ Pods       │         │ Pods       │         │ Pods       │
      │ (Unidade   │         │ (Unidade   │         │ (Unidade   │
      │ básica do  │         │ básica do  │         │ básica do  │
      │ Kubernetes)│         │ Kubernetes)│         │ Kubernetes)│
      └────────────┘         └────────────┘         └────────────┘
