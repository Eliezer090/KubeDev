# Service do tipo ClusterIP
- Podemos utilizar o ClusterIP para comunicação entre os pods.
## Executando 
- Ao executar o deployment.yaml, será subido um Pod que irá rodar uma api que converte fahrenheit para celsius, na porta 8080.
## Executando uma segunda maquina:
- Podemos executar uma segunda aplicação para testes e entrar em modo interativo já:
######
    kubectl run -i --tty --image kubedevio/ubuntu-curl ping-test --restart=Never --rm -- /bin/bash
### Executando uma requisição para a API:
- Estando dentro da maquina que subimos acima podemos rodar um Curl para a API com o IP do Pod:
#### Dirretamente com o IP do POD:
    curl http://<IP_POD>:8080/temperatura/fahrenheitparacelsius/100
#### Com o Service:
- Para que isso funcione, precisamos criar um Service "service.yaml", que irá se comunicar com os pods a partir dos labels(spec>selector>app), após isso podemos usar o "name"(metadata>name) para realizar a requisição para a API(O service irá fazer o balanceamento de carga entre os pods caso haja mais de um):
######
    curl http://api-service/temperatura/fahrenheitparacelsius/100