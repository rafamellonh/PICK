## PersistentVolume (PV) 

* PersistentVolume é um recurso de armazenamento provisionado de forma independente do ciclo de vida dos pods. Ele representa uma peca de infraestrutura de armazenamento, como um disco no Azure ou AWS, um volume NFS, ou outro beckend de armazenamento. O PV é utilizado para fornecer armazenamento persistente a aplicativos que precisam reter dados além do ciclo de vida do pod.

## Para que serve um PV?
* Persistência de dados
* Abstração de armazenamento
* Compartilhamento entre pods
* Separação de configuração e uso


## Características principais

* Tamanhos configuráveis
* Modos de acesso
    * ReadWriteOnce : um pod pode montar o PV para leitura/escrita
    * ReadOnlyMany : Muitos pods podem montar o PV para somente leitura
    * ReadWriteMany : Muitos pods podem montar o PV para leitura e escrita (dependendo do provedor)

* Politicas de retenção
    * Retain: Mantém os dados
    * Delete: Exclui o volume
    * Recycle: Limpa o volume para reutilização (menos comum)

* Exemplo :

```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-pv
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  hostPath:
    path: "/mnt/data"
apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-pv
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  hostPath:
    path: "/mnt/data"
```