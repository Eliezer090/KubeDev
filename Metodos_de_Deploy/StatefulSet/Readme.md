# Utilizando StatefulSet
- Para esta parte iremos criar uma pagina nginx que irá exibir o nome da maquina que está rodando este serviço e iremos atachar outro container neste processo.
- Se caso estiver usando o StatefulSet precisa ter cuidado que para cada replica todas as definições do yaml serão escaladas, por exemplo se definirmos um volume e colocarmos 3 replicas, cada pod terá seu volume e assim para todos os recursos
- Um dos pontos fortes é que a escalabilidade é sequencial, ou seja, ele sobe uma replica por vez ao invez do Deployment que sobe todas as replicas de uma unica vez, no geral ele trabalha como uma pilha tanto para inclusão quanto para remoção dos pods.
## Qundo é recomendado a utilização
- Recomendado a utilização para aplicações que usam volumes por exemplo, banco de dados, RabbitMQ, etc. Toda e qualquer aplicação que usa volume é preciso ter um cuidado maior se forem dados que nao podem ser perdidos.

## Como executar
- Primeiro é preciso verificar os yamls as config de volume e adaptar para o seu provedor.
- Após é só implantar os yamls presente na pasta deste módulo.
- Após a implantação pode subir o numero de replicas e verá que irá subir de 1 em 1.
    - Se fizer a deleção verá que a deleção também será de 1 em 1.
    - Cuidado ao escalar pois o volume acoplado está como persistent, com isso eles não serão removidos ao deletar o pod.
- Após para conexão pode ser dubido uma maquina para fazer o curl:
`````
    kubectl run -i --tty --image kubedevio/ubuntu-curl ping-test --restart=Never --rm -- /bin/bash
`````
- Dentro da maquina pode rodar o comando abaixo e se tudo deu certo será retornado o nome do pod como resposta do curl:
`````
    curl <NAME_POD>.nginx-state.default.svc.cluster.local
`````
- Com isso é desta forma que se trabalha com StatefulSet e como comentado tem momentos certos de usar ele também.
