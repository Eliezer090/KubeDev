# Namespaces
## Criando Namespaces
- Antes de começar de utilizar os namespaces é necessário cria-los no cluster, para isso podemos utilizar o comando:
#####
    kubectl create namespace <nome_do_namespace>
## Utilização:
- Podemos utilizar de duas formas: 
    - Após criar os namespaces podemos ir no .yaml e colocar o namespace no grupo "metadata", desta forma fica mais engessado mas funciona.
    - A segunda forma e permite reaproveitamento de yamls é setando no comando "apply":
        - kubectl apply -f <arquivo_yaml> -n <nome_do_namespace>