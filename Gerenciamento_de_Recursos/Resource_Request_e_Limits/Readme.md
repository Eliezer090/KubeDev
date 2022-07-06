# Gerenciamento de recursos da Aplicação
- O objetivo desta seção é aprender como podemos definir limites de memória, cpu, entre outros da aplicação para que uma aplicação nao consuma todos os recursos do cluster e acabe derrubando outras aplicações que nao tinham nada a ver.
- Para este tópico será utilizado uma aplicação do google "gcr.io/kubernetes-e2e-test-images/resource-consumer:1.5" que serve para este fim de explicar os o consumo de resoucers.

# Para funcionar o metric server
- Par que possa ver o quanto de recurso que o pod está utilizando é preciso rodar o comando abaixo para instalar o Metric Server:
````
kubectl delete -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
````
- Após pode ser rodado o comando:
`````
kubectl top pod <nome_do_pod>
`````