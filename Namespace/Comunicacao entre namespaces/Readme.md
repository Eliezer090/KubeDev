# Comunicação utilizando Namespaces:
- Esta seção depende da "Usando Namespaces", após subir os 2 e atribuir seus devidos namespaces, podemos utilizar o "service.yaml" atribuindo o namespace ao mesmo também, com isso ficando vinculado o service com o namespace.
    - Exemplo: kubectl apply -f service.yaml -n <nome_do_namespace>
- Para comunicação externa é utilizado o IP de cada Nó do cluster, atribuido a porta fornecida pelo NodePort.
- Para comunicação entre os pods é preciso utilizar o namespace, mas utilizando o "service-nginx-color" dirretamente nao acessa pois este cara é o mesmo para as 2 aplicações, com isso para acessar é preciso utilizar uma sequencia de nomes:
    - Nome do serviço: neste caso "service-nginx-color"
    - Nome do namespace: neste caso "blue" ou "green"
    - Service: Aqui é fixo "svc"
    - Referencia de Cluster: Neste caso é fixo "cluster"
    - Referencia de local: Neste caso é fixo "local"
        - Exemplo com tudo junto:
            - http://service-nginx-color.blue.svc.cluster.local

# Configuração ExternalName
- Para simplificar os requests foi feito mais 2 services, um para cada aplicação "serviceblue.yaml" e "servicegreen.yaml", com isso ao fazer os requests pode ser utilizado o "name".
    - Exemplo: http://service-nginx-green
