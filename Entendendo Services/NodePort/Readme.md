# Service do tipo NodePort:
- O serviço do tipo NodePort expoe uma porta(Ela pode ocupar o range de 30000 até 32767 definida automaticamente) para o NÓ do cluster, com isso pode-se comunicar com os pods, para acessar deve-se verificar o IP do NÓ(pod) e a porta do NodePort que foi exposta.
- Para executar segue a mesma lógica do ClusterIP, somente alterando as infos acima descritas.