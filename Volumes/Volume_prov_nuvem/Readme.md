# Utilizando volume do seu provedor de nuvem
- Nesta parte ao invéz de utilizarmos um volume criado por nós, iremos utilizar o volume do provedor de nuvem do nosso cluster kubernetes, com isso ao utilizar nao necessitamos criar um PersistentVolume mais, somente o PersistentVolumeClaim e sair usando.
## Listando os volumes do provedor
- Para listar os volumes do provedor pode ser rodado o comando abaixo, para a utilização deve ser utilizado o NAME dele:
`````
    kubectl get storageclass
`````