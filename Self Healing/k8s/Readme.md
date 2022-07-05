# Instruções de como executar
- Antes de aplicar os arquivos services.yaml e deployment.yaml tanto da api quanto do mongodb é preciso criar 2 namespaces:
````
    kubectl create namespace webapi
    kubectl create namespace mongodb
````
- Após criado pode ser aplicado os services e os deployments atribuindo os namesmaces:
    - Obs: Nos comandos abaixo temos o apply do "mongodb-secret.yaml" no namespace "webapi", é feito isso pois no deployment.yaml da api estamos pegando os dados de acesso da base do mongo, com isso como estamos separando por namespaces(webapi e mongodb) um nao enxerga o outro, por isso precisamos realizar o apply das config no outro namespace.
````
    kubectl apply -f mongodb/ -n mongodb
    kubectl apply -f mongodb/mongodb-secret.yaml -n webapi
    kubectl apply -f api/ -n webapi
````

- Após isso sua aplicação deve estar rodando no cluster kubernetes, lembrando deve estar rodando em um cluster na nuvem pois o service da api está com "type: LoadBalancer", com isso seu provedor de nuvem fornecerá um ip e poderá acessar a API: 
    - http://IP_PROVEDOR/swagger

# Link
- [ConfigMap e Secrets](https://kubedev.club.hotmart.com/lesson/PeA5J3goeW/configmap-e-secret)
- [Exercicio atribuindo namespaces](https://kubedev.club.hotmart.com/lesson/k7QlmpD2ey/exercicios)


