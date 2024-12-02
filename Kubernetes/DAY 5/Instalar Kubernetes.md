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

* Instalar Container Runtime

```

sudo apt-get update && sudo apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update && sudo apt-get install -y containerd.io

```

* Configurando ContainerD
```
sudo containerd config default | sudo tee /etc/containerd/config.toml

sudo sed -i 's/SystemdCgroup = false/SystemdCgroup = true/g' /etc/containerd/config.toml

sudo systemctl restart containerd
sudo systemctl status containerd

```

* Habilitando o servico kubelet
```
systemctl enable --now kubelet
```

* Abrir portas no firewall :

```
sudo ufw status
sudo ufw enable
sudo ufw reload

```


```
sudo ufw allow 6443/tcp
sudo ufw allow 10250:10255/tcp
sudo ufw allow 6783/tcp

```
