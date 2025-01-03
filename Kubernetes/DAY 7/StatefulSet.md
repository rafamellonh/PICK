## O que é StatefulSet?

* Ele é um recurso controlador usado para gerenciar aplicações com estado, ou seja aquelas que exigem um controle mais refinado sob como os pods sao criados, destruídos e gerenciáveis
* Ele é projeto para aplicações onde a identidade de cada pod é importante e precisa ser preservada. Exemplos mais comuns incluem banco de dados, caches distribuídos e sistemas distribuídos de armazenamento.

## Principais características do StatefulSet :  

* Identidade Persistente : Cada pod gerenciado por um StatefulSet possui um identificados único e persistente. Isso é garantido pelo uso de um nome ordinal (-0, -1, etc), que é anexado ao nome do pod. Por exemplo meu-app-0

* Volume persistente: O StatefulSet associa cada pod a um PVC exclusivo, garantindo que os dados de cada pod permaneçam persistentes mesmo que ele seja reiniciado ou recriado.

* Ordem de criação e exclusão : O StatefulSet gerencia os pods em uma ordem sequencial. Por exemplo
    * Criação : Os pods sao criados um por vez, começando com pod-0, depois pod-1 e assim por diante.
    * Exclusão : O Processo de exclusão também segue a ordem inversa.

* Nomeação Estável (Stable Network Identity) : Cada pod tem um nome DNS estável, facilitando a comunicação entre eles em uma aplicação distribuída. Por exemplo, se o nome do StatefulSet é meu-app e o namespace é default, o pod meu-app-0 pode ser acessado através de meu-app-0-.meu-app.default.svc.cluster.local.

* Rolling Updates Controlados : O StatefulSet permite atualizacoes controladas, garantindo que a atualizacao de um pod seja concluida antes de prosseguir para o proximo. Isso é utili para manter a consistencia em aplicativos com estado