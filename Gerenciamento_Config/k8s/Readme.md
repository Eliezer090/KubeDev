# Obejetivo da sessão
- Aplicar a separação das configurações para o configmap e secrets(Utilizado para dados sensiveis) para conseguirmos deixar mais dinamicos os deployment.yaml
- O que são e como criar os secrets:
    - Eles são resposaveis por conter as informações sensiveis do software(Usuários e senhas), com isso precisamos encodificar em base64 os dados, para isso utilizamos o comando:
        - echo -n "TEXTO_A_SER_ENCRIPTADO" | base64

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
<<<<<<< HEAD
- [Exercicio atribuindo namespaces](https://kubedev.club.hotmart.com/lesson/k7QlmpD2ey/exercicios)
=======
>>>>>>> a3b6d9165f49d49fc6b81f942ab89abd13370807


