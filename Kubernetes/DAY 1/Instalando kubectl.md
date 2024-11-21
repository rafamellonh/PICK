## Instalando o kubectl

* Iremos utilizar o kubectl para alguns testes antes de configurar um cluster Kubernetes.

* Install kubectl binary with curl on Linux 
    * Download the latest release with the command:
    ```    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" ```
    *  ``` chmod +x kubectl  ```
    * ```  mv kubectl /usr/local/bin ```


* Comandos 

```  kubectl get nodes ``` </br>
```  kubectl get pods ``` </br>
```  kubectl get namespace ``` </br>
```  kubectl get nodes -n kube-system``` </br>
```  kubectl get nodes -n kube-system -o wide``` </br>