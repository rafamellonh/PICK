## Install Kubernetes

* Instalar todos os componentes em todos os nodes, mas o kubeadm init em diante, somente no node master.

* Desabilitar swap :
```
sudo swapoff -a
vim /etc/fstab  (comentar linha do swap)
```

* Carregar os módulos do Kernel, adicione os modules overlay e br_netfilter no arquivo
```
sudo vim /etc/modules-load.d/k8s.cond

modprobe overlay
modprobe br_netfilter

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
* Reload config
```
sudo sysctl --system
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

* Inicializar o cluster e o admin.conf (SOMENTE no control-plane)

```
sudo kubeadm init --pod-network-cidr=10.10.0.0/16 --apiserver-advertise-address=192.168.1.201
```

* você verá uma mensagem informando que o cluster foi inicializado com sucesso. Além disso, você verá um comando para configurar o acesso ao cluster com o kubectl. Copie e cole esse comando em seu terminal:  (somente no control-plane)

```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

```
To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

Alternatively, if you are the root user, you can run:

  export KUBECONFIG=/etc/kubernetes/admin.conf

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

Then you can join any number of worker nodes by running the following on each as root:

kubeadm join 192.168.1.201:6443 --token iykm23.e2rzuz1fczhxvewu \
        --discovery-token-ca-cert-hash sha256:a69c226844a506d8c0287386c1f3155e289ffc8db0da72c206beb16311ae24f9 
```

* Adicionar nodes workers
```
sudo kubeadm join 192.168.1.201:6443 --token uzwc7m.auystlt1hyu60qlb \
        --discovery-token-ca-cert-hash sha256:a69c226844a506d8c0287386c1f3155e289ffc8db0da72c206beb16311ae24f9 
```

* Criar novo token e hash :

```
kubeadm token create

openssl x509 -pubkey -in /etc/kubernetes/pki/ca.crt | \
openssl rsa -pubin -outform der 2>/dev/null | \
openssl dgst -sha256 -hex | \
sed 's/^.* //'

```

* Instalar o CNI - Weave Net (use wget) (SEM ELE, OS WORKES FICARAM COMO NotReady)

```
kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml


```