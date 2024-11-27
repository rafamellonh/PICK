##  O que é DaemonSet

* DaemonSet é um objeto usado para garantir que uma copia de um pod especifico seja executada em cada no do cluster.
* Ele é ideal para workloads que precisam estar presenters em todos os nos para fornecer funcionalidades de suporte ou infraestrutura
* Principais características
    * Presença em todos os nos
    * Usos típicos
    * Seleção de nos específicos
    * Gerenciamento automático


# Diferenças entre DaemonSet e ReplicaSet/Deployment

| **Aspecto**       | **DaemonSet**                     | **ReplicaSet/Deployment**         |
|--------------------|-----------------------------------|------------------------------------|
| **Escopo**         | Todos os nós (ou específicos).    | Quantidade fixa de réplicas.      |
| **Finalidade**     | Infraestrutura ou serviços locais.| Aplicativos ou workloads gerais.  |
| **Escalabilidade** | Escala com a quantidade de nós.   | Escala manual ou com HPA.         |
