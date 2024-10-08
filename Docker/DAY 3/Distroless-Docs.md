##### A arte da minimização : Imagens Distroless

No mundo dos containers existe uma tendencia emergente chamada Distroless que é usar imagem de containers <br>
apenas com as dependências e artefatos necessários para a execução do aplicativo.

##### O que é Distroless? 

Distroless refere-se à estratégia de construir imagens de container que sao efetivamente "sem distribuição"<br>
Isso significa que eles nao contem uma disto tipica de um sistema operacional, como shell, utilitários ou bibliotecas <br>
desnecessárias. Ao invés disso, essas images contem apenas o ambiente runtime (Node.js, python, java e etc)

##### Beneficios

O principal beneficio é a segurança. Ao excluir componentes desnecessários, o potencial de ataque é significante reduzido. <br>
Além disso tem a questão que as imagens em bem menores.