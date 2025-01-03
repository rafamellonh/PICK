## Passos para executar o desafio do primeiro dia


1. Install Docker : 
```
curl -fsSl https://get.docker.com | bash 
``` 
2. Install Kind : 
```
# For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.25.0/kind-linux-amd64
# For ARM64
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.25.0/kind-linux-arm64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```  

3. Install kubectl :
 ``` 
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" 
chmod +x kubectl 
mv kubectl /usr/local/bin 
```

4. Create ``` meu-primeiro-cluster.yaml ``` file
5. Create cluster : 
```
kind create cluster --config meu-primeiro-cluster.yaml --name cluster-mello
```
6. Create pod : 
```
kubectl apply -f meu-primeiro-pod.yaml
```
