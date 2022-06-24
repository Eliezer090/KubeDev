# Instruções de como executar
- Antes de aplicar os arquivos services.yaml e deployment.yaml tanto da api quanto do mongodb é preciso criar 2 namespaces:
#####
    kubectl create namespace webapi
    kubectl create namespace mongodb
- Após criado pode ser aplicado os services e os deployments atribuindo os namesmaces:
####
    kubectl apply -f mongodb/service.yaml -n mongodb
    kubectl apply -f mongodb/deployment.yaml -n mongodb
    kubectl apply -f api/service.yaml -n webapi
    kubectl apply -f api/deployment.yaml -n webapi

- Após isso sua aplicação deve estar rodando no cluster kubernetes, lembrando deve estar rodando em um cluster na nuvem pois o service da api está com "type: LoadBalancer", com isso seu provedor de nuvem fornecerá um ip e poderá acessar a API: 
    - http://IP_PROVEDOR/swagger

# Link
- [Aula subindo a aplicação](https://kubedev.club.hotmart.com/lesson/94JMJqznOg/subindo-a-aplicacao)
- [Exercicio atribuindo namespaces](https://kubedev.club.hotmart.com/lesson/k7QlmpD2ey/exercicios)
