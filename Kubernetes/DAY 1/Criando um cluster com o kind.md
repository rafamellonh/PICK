## Criando um cluster com o Kind


```
# For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.25.0/kind-linux-amd64
# For ARM64
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.25.0/kind-linux-arm64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

```

* Eh preciso instalar o Docker para usar o Kind.


* Criando Cluster
```
kind create cluster
kind delete cluster

```


* Crie um arquivo .yml (kind-cluster.yml)
* ```kind create cluster --config kind-cluster.yml --name cluster-mello```

```
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker
~                 


```