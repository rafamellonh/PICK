## Instalando o kubectl

* Iremos utilizar o kubectl para alguns testes antes de configurar um cluster Kubernetes.

* Install kubectl binary with curl on Linux 
    * Download the latest release with the command:
    ```    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" ```
    *  ``` chmod +x kubectl  ```
    * ```  mv kubectl /usr/local/bin ```


* Comandos 

```kubectl get nodes ``` </br>
```kubectl get pods ``` </br>
```kubectl get pods -A``` </br>
```kubectl get pods -n kube-system``` </br>
```kubectl get namespace ``` </br>
```kubectl get nodes -n kube-system``` </br>
```kubectl get nodes -n kube-system -o wide``` </br>
```kubectl run giropops --image nginx --port 80```</br>
```kubectl exec -it giropops -- bash```</br>
```kubectl apply -f pod.yml ```
```kubectl describe pods NAME```
```kubectl  attach NAME-POD -ti ```
```kubectl  exec -ti strigus -- bash```
```kubectl  ```


* Dry-run

```kubectl run --image nginx --port 80 giropops --dry-run=client``` </br> 
```kubectl run --image nginx --port 80 giropops --dry-run=client -o yaml ``` </br>
```kubectl run --image nginx --port 80 giropops --dry-run=client -o yaml > pod.yml```
