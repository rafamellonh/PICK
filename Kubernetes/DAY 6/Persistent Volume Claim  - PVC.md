## Persistent Volume Claim 

* No Kubernetes PVC é Persistent Volume Claim, ele é uma abstração que permite que os usuários solicitem armazenamento persistente para seus aplicativos de forma declarativa.

## Entendendo o conceito :

* Persistente Volume:
    * Ele é um recurso de armazenamento provisionado no cluster. Ele pode ser fornecido por um administrador ou automaticamente provisionado com base em configurações especificas.
    * Ele é independente do ciclo de vida do pod

* Persistente Volume Claim
    * É a solicitação de um PV. O PVC define as características desejadas do volume, como :
        * Capacidade
        * Mode de armazenamento
    * Quando um PVC é criado, o kubernetes tenta encontrar um PV que atenda os requisitos solicitados.

* StorageClass :
    * Especifica o tipo de armazenamento desejado (como SSD, HDD NFS etc) e ajuda no provisionamento dinâmico dos volumes.


## FLuxo de funcionamento 

* O administrador ou um mecanismo de provisionamento cria um PV
* O desenvolvedor cria um PVC declarando as necessidades de armazenamento
* O Kubernetes liga o PVC a um PV que satisfaz os requisitos
* O PVC pode ser montado por um pod, garantindo armazenamento persistente para os dados mesmo que o pod seja destuido.