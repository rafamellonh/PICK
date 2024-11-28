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
        livenessProbe: # Onde definimos a nossa probe de vida
          exec: # O tipo exec é utilizado quando queremos executar algo dentro do container.
            command: # Onde iremos definir qual comando iremos executar
              - curl
              - -f
              - http://localhost:80/
          initialDelaySeconds: 10 # O tempo que iremos esperar para executar a primeira vez a probe
          periodSeconds: 10 # De quanto em quanto tempo iremos executar a probe
          timeoutSeconds: 5 # O tempo que iremos esperar para considerar que a probe falhou
          successThreshold: 1 # O número de vezes que a probe precisa passar para considerar que o container está pronto
          failureThreshold: 3 # O número de vezes que a probe precisa falhar para considerar que o container não está pronto
        readinessProbe: # Onde definimos a nossa probe de prontidão
          httpGet: # O tipo de teste que iremos executar, neste caso, iremos executar um teste HTTP
            path: / # O caminho que iremos testar
            port: 80 # A porta que iremos testar
          initialDelaySeconds: 10 # O tempo que iremos esperar para executar a primeira vez a probe
          periodSeconds: 10 # De quanto em quanto tempo iremos executar a probe
          timeoutSeconds: 5 # O tempo que iremos esperar para considerar que a probe falhou
          successThreshold: 1 # O número de vezes que a probe precisa passar para considerar que o container está pronto
          failureThreshold: 3 # O número de vezes que a probe precisa falhar para considerar que o container não está pronto
        startupProbe: # Onde definimos a nossa probe de inicialização
          tcpSocket: # O tipo de teste que iremos executar, neste caso, iremos executar um teste TCP
            port: 80 # A porta que iremos testar
          initialDelaySeconds: 10 # O tempo que iremos esperar para executar a primeira vez a probe
          periodSeconds: 10 # De quanto em quanto tempo iremos executar a probe
          timeoutSeconds: 5 # O tempo que iremos esperar para considerar que a probe falhou
          successThreshold: 1 # O número de vezes que a probe precisa passar para considerar que o container está pronto
          failureThreshold: 3 # O número de vezes que a probe precisa falhar para considerar que o container não está pronto


```