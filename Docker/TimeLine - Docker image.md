## Timeline " Criacao de uma imagem Docker

### Criação do Dockerfile :    

O primeiro passo para criar uma imagem Docker é criarmos um arquivo Dockerfile com todas as <br>
instruções necessários para construir a imagem.

### Build ad image :

Com o Dockerfile em mãos, é necessário executar o comando docker build para iniciar o processo de construção da imagem <br>
O Docker vai ler o arquivo e compilar a imagem.

### Tag da imagem : 

Apos concluir o build, é possível adicionar tags a uma imagem para facilitar a identificação

### Push da imagem

Para disponibilizar a imagem em um diretório remoto, é necessário utilizar o comando Docker push, ele envia a imagem para o DockerHub.

### Verificacao de vulnerabilidades :

É importante garantir a segurança da imagem antes de disponibiliza-la para uso. Para isso usamos ferramentas como Trivy. Essas ferramentas <br>
analisam a imagem em busca de componentes com falhar de segurança conhecidas.


### Assinatura com o Cosign : 

Para adicionar uma camada extra de segurança, é possível assinar digitalmente a imagem utilizando o Cosign.