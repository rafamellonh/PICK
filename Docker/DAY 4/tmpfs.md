#### Tmpfs

Volumes tmpfs no Docker armazenam dados temporariamente na memória RAM, oferecendo acesso rápido e alta performance, mas os dados são perdidos quando o contêiner para. São úteis para dados efêmeros ou temporários, como caches ou arquivos transitórios, sem consumir espaço em disco.


``` docker run -d --name web-2 --mount type=tmpfs,target=/test-tmpfs -p 8080:80 nginx ```