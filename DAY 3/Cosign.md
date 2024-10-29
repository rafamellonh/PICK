###### Cosign

https://www.docs.sigstore.dev/sys

https://docs.sigstore.dev/cosign/system_config/installation/

https://github.com/sigstore/cosign

cosign generate-key-pair


https://docs.sigstore.dev/cosign/signing/signing_with_containers/

login no docker hub
push da imagem
cosign sign -key cosign.key rafamellonh/linuxtips-giropops-senhas-assinado:1.0
cosign verify --key cosign.pub rafamellonh/linuxtips-giropops-senhas-assinado:1.0