# Replicaset
- Serve para termos resiliência em caso de falha de pods, mantendo sempre as especificações definidas no yaml.

- A cascata de execução até aqui está a seguinte:
    - replicaset: Responsável por gerenciar os pods que serão executados.
        - pod: Responsável por executar os containers especificados pelo replicaset.