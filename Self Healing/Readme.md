# Self Healing para garantir resiliencia nos Pods
# Obejetivo da sessão
- Aplicar o Self Healing para garantir a resiliencia dos pods, com isso se algum pod vier a dar problema ele será restartado, pois o kubernetes por sí não sabe quando um container deve ou nao ser restartado, para isso iremos trabalhar com 3 gerenciadores:
    - livenessProbe:
        - Utilizado para realizar os restarts dos pods, com ele podemos utilizar o "readinessProbe" e "startupProbe" que explico o funcionamento de cada um mais para baixo, eles auxiliam para definir quando o pod está com problema de fato e não é só uma lentidão.
        - Se configurar no modo default:
            - Se realizar um describe no pod irá ver a linha abaixo:
                -Liveness: http-get http://:80/health delay=0s timeout=1s period=10s #success=1 #failure=3
            - Ali terá todas as infos:
                - http-get: Irá fazer um teste HTTP.
                - http://:80/health: é o host.
                - #timeout=1s: Quanto tempo ele tolera a receber uma resposta.
                - #failure=3: Tolera 3 falhas se atingiu este limite ele restarta o pod.
        - Flags: 
            - initialDelaySeconds:
                - Serve para definir um tempo de dalay para começar de testar, pois se a aplicação demora para subir deve esperar para iniciar os testes de disponibilidade da aplicação.
            - periodSeconds:
                - De quanto em quanto tempo ele irá fazer o teste, mas cuidado pois este tempo for muito baixo pode ocasionar trafego desnecessário para a plicação e problemas de restars, para problemas de restart deve ser configurado o "initialDelaySeconds", pois se a pliucação demorar mais tempo que o "periodSeconds" para estartar pode ocasionar o erro "CrashLoopBackOff".
            - timeoutSeconds:
                - Quanto tempo ele tolera para receber a resposta.
            - failureThreshold:
                - Quantas falhas eu tolero até restartar o container.
    - readinessProbe
        - Utilizado para verificar se a aplicação está pronta para receber requisições, até que a mesma nao estiver de acordo o endpoint será removido, para isso se executar "kubectl get endpoints" verá que na coluna ENDPOINTS nao terá valor.
        - Flags:
            - Tenho as mesmas flags do "livenessProbe".
            - successThreshold: Quantos sucessos eu tenho que receber para zerar a quantidade de falhas.
    - startupProbe
        - Serve para dizer quanto tempo a aplicação tem para estartar, se configurarmos as 2 flagas "failureThreshold: 30" e "periodSeconds: 10" com esses valores estou dizendo que a aplicação tem 300 segundos para estartar.
## Conteúdo:
- Esta pasta é uma cópia do Deploy_Application_Kubernetes, dentro da pasta k8s está e explicado como executar o cluster.
- A pasta "pedelogo-catalogo" contém o código da api e o arquivo DockerFile para gerar a imagem docker.

# Estruturação: 
````
- K8s
    - api: contem os yamls reposáveis por subir e executar a aplicação.
    - mongodb: contem os yamls reposáveis por subir a base de dados.
- pedelogo-catalogo: Resposável pelo código fonte da aplicação.
````