## O que sao volumes no Kubernetes?

* Volumes sao nada mais do que um diretório dentro do pod que pode ser utilizado para armazenar dados. Eles podem ser utilizados para armazenar dados que precisa ser persistidos, como por exemplo um banco de dados.
* Temos basicamente 2 tipos de ephemeral volumes e os persistent volumes.
* Os ephemeral volumes, que inclusive ja vimos durante o treinamento o emptyDir, sao volumes que sao criados e destruídos junto com o pod. Ele também é um volume porem nao é persistent.
* Agora quando estamos falando de persistent volumes, estamos falando de volumes que sao criados e nao sao destruídos junto com o pod.