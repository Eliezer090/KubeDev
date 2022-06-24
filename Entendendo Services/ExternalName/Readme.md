# Service do tipo ExternalName:
- Ele funciona como um mapeamento/encurtamento de nome, ou seja, é melhor para resolução de caminhos para comunicação interna entre os pods, mais facil do que usar "eliezer.dev.svc.cluster.local".
- Pode ser visto que tanto o "deployment.yaml" quanto o "service.yaml", estão com "namespace" que até este momento do curso nao foi ensinado, porém foi utilizado abribuindo ao namespace "dev", o mesmo deve ser criado antes de subir os 2 yamls.
## Ordem de execução:
- Primeiro deve-se criar o namespace "dev":
######
    kubectl create namespace dev

- Depois deve subir o "deployment.yaml":
######
    kubectl apply -f deployment.yaml

- Depois deve subir o "service.yaml":
######
    kubectl apply -f service.yaml

- Depois deve subir o "service-external.yaml":
######
    kubectl apply -f service-external.yaml