# Configuração do Deployment, Pod e Container no Kubernetes

```yaml
# 🔲 Deployment: Configurações gerais que gerenciam os pods.
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: nginx-deployment  # 🔲 Deployment: Rótulo para identificar o Deployment.
  name: nginx-deployment    # 🔲 Deployment: Nome do Deployment.
spec:
  replicas: 1               # 🔲 Deployment: Número de réplicas dos pods.
  selector:                 # 🔲 Deployment: Seleção de pods com base nos rótulos.
    matchLabels:
      app: nginx-deployment
  strategy: {}              # 🔲 Deployment: Configurações de estratégia (vazio por padrão).

  # 🔲 Pod: Modelo para criar os pods.
  template:
    metadata:
      labels:
        app: nginx-deployment  # 🔲 Pod: Rótulo para identificar o pod.
    spec:                     # 🔲 Pod: Especificações do pod.
      containers:             # 🔲 Container: Lista de containers que compõem o pod.
      
      # 🔲 Container: Configurações específicas do container.
      - image: nginx           # 🔲 Container: Imagem usada pelo container.
        name: nginx            # 🔲 Container: Nome do container.
        resources:             # 🔲 Container: Configuração de recursos.
          limits:
            cpu: "500m"        # 🔲 Container: Limite máximo de CPU.
            memory: "256Mi"    # 🔲 Container: Limite máximo de memória.
          requests:
            cpu: "300m"        # 🔲 Container: CPU garantida para o container.
            memory: "128Mi"    # 🔲 Container: Memória garantida para o container.
```