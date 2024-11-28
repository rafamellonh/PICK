## O que sao Probes no Kubernetes

* Probes sao verificadores de saúde usadas para determinar se um container esta funcionando corretamente
* Elas sao configuradas dentro das definições de pods e ajudam o kubernetes a tomar decisões automáticas, como reiniciar containers com problemas ou remover um container de um serviço para evitar que ele receba trafego.
* Existem 3 tipos de probes :
    1. Liveness Probe : 
        * Verifica se o container ainda esta "vivo" ou em funcionamento. Se a liveness probe falhar, o kubernetes reinicia o container.
        * É usada para detectar se o container entrou em um estado inoperável ou travou.
    2. Readiness Probe :
        * Determina se o container esta pronto para receber trafego
        * Se a Readiness probe falhar, o Kubernetes remove o pod do balanceador de carga, mas nao o reinicia.
        * É usada quando o aplicativo no container precisa de tempo ou certas condições para ficar funcionar.
    3. Startup Probe : 
        * É usada para verificar se o container iniciou corretamente.
        * Se a Startup probe falhar, as outras (Liveness e Readiness) assumem o controle
        * É usada quando o aplicativo precisa de mais tempo para inicializar do que seria considerado padrão pelas Liveness ou Readiness probe.        
* Elas sao usadas para containers.

1. Liveness Probe 
```
      containers:
      - image: nginx
        name: nginx
        resources:
          limits:
            cpu: "500m"
            memory: "256Mi"
          requests:
            cpu: "300m"
            memory: "128Mi"
        livenessProbe: # Aqui é onde vamos adicionar a nossa livenessProbe
          tcpSocket: # Aqui vamos utilizar o tcpSocket, onde vamos se conectar ao container através do protocolo TCP
            port: 80 # Qual porta TCP vamos utilizar para se conectar ao container
          initialDelaySeconds: 10 # Quantos segundos vamos esperar para executar a primeira verificação
          periodSeconds: 10 # A cada quantos segundos vamos executar a verificação
          timeoutSeconds: 5 # Quantos segundos vamos esperar para considerar que a verificação falhou
          failureThreshold: 3 # Quantos falhas consecutivas vamos aceitar antes de reiniciar o container
```
```     livenessProbe: # Aqui é onde vamos adicionar a nossa livenessProbe
          httpGet: # Aqui vamos utilizar o httpGet, onde vamos se conectar ao container através do protocolo HTTP
            path: / # Qual o endpoint que vamos utilizar para se conectar ao container
            port: 80 # Qual porta TCP vamos utilizar para se conectar ao container
          initialDelaySeconds: 10 # Quantos segundos vamos esperar para executar a primeira verificação
          periodSeconds: 10 # A cada quantos segundos vamos executar a verificação
          timeoutSeconds: 5 # Quantos segundos vamos esperar para considerar que a verificação falhou
          failureThreshold: 3 # Quantos falhas consecutivas vamos aceitar antes de reiniciar o container


```