## Install Kubernetes

* Desabilitar swap :
```
sudo swapoff -a
```

* Carregar os módulos do Kernel, adicione os moduloes overlay e br_netfilter no arquivo
```
sudo vim /etc/modules-load.d/k8s.cond

```

* Carregue os modules
```
sudo modprobe overlay
sudo modprobe br_netfilter

```

* Configure os parametros do sistema :
```
cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
net.bridge.bridge-nf-call-iptables  = 1
net.bridge.bridge-nf-call-ip6tables = 1
net.ipv4.ip_forward                 = 1
EOF
```

* Instalando pacotes:
```

sudo apt-get update && sudo apt-get install -y apt-transport-https curl

curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.30/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg

echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.30/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list

sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl

sudo apt-mark hold kubelet kubeadm kubectl


```









