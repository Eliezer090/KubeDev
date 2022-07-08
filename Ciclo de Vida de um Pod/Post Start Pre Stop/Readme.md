# Post Start e Pré Stop
- Post Start é rodado logo após a criacao do container, nele podemos disparar eventos para urls, fazer coisas dentro dele que podem ser util confome o cenário
- Pré Stop, é antes do container morrer, pode ser também utilizado para N coisas, fechar conexoes, enviar um log para algum lugar dizendo que foi matado o container etc.
- No geral estes 2 caras sao uteis para gerenciamento do container.