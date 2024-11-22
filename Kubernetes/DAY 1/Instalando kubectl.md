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
```kubectl apply -f pod.yml ```   Cria e/ou atualiza um pode (nao pode add ou remove um container) </br>
```kubectl delete -f pod.yml ```</br>  
```kubectl create -f pod.yml ```  Cria um pod</br>
```kubectl describe pods NAME```</br>
```kubectl logs NAME```</br>
```kubectl logs POD-NAME  -c CONTAINER-NAME ```</br>
```kubectl attach NAME-POD -ti ```</br>
```kubectl exec -ti strigus -- bash```</br>
```kubectl  ```


* Dry-run

```kubectl run --image nginx --port 80 giropops --dry-run=client``` </br> 
```kubectl run --image nginx --port 80 giropops --dry-run=client -o yaml ``` </br>
```kubectl run --image nginx --port 80 giropops --dry-run=client -o yaml > pod.yml```

