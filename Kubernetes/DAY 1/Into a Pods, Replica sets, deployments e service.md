## Into a Pods, Replica sets, deployments e service

### Pods
* Um pod poder ter um ou mais containers que compartilham o mesmo namespace de rede, armazenamento e informações sobre como rodas os containers.
* So tem um ip que sera usado pelos containers ou pelo container

### Deployments 
* Usado para gerenciar a implantação e a atualização de Pods de maneira declarativa.
* Ele oferece um mecanismo poderoso para gerenciar versões de aplicativos, incluindo o gerenciamento de replicas, atualizações continuas, roolbacks e escalabilidade.

### Replica sets
* Sua função é garantir a quantidade de replicas configurado no deployment
* Monitora os Pods e garante a disponibilidade desses Pods, criando ou deletando Pods conforme necessário, para manter o numero desejado de replicas em funcionamento.

### Service
* Ele é um recurso que abstrai o acesso a um conjunto de Pods, fornecendo uma maneira estável e confiável de se comunicar com eles, independente de mudanças no cluster.
* Ele fornece funcionalidades como balanceamento de carga, escalabilidade, abstração de rede.
* Existe diferentes tipos de Service: ClusterIP, NodePort, LoadBalancer, ExternalName.