# Horizontal Pod Autoscaler
- Como o nome dele já diz serve para escalar a quantidade de pods automaticamente baseado nos valores parametrizados. 
- Para ele funcionar é preciso que tenha algumas configurações feitas, para este exemplo está sendo utilizado a aplicação que está no yaml "Resouce_Request_e_Limits>deployment-resource.yaml", nela temos configurado o grupo "requests>cpu", no yaml presente nesta seção "hpa.yaml" configuremos o "targetCPUUtilizationPercentage" que diz quantos por cento de utilização do CPU iremos aceitar até criar um novo pod.

## Para que seria util?
- É extremamente util para garantirmos a escalabilidade da aplicação sem que a mesma caia por excesso de requests.
