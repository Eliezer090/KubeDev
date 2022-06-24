# Deployment
- Resposável por fazer o gerenciamento de mudanças de um recurso.
- Deployment é a mesma extrutura do Replicaset, porém, o Deployment consegue fazer o gerenciamento de mudanças que ocorrem no yaml, o que muda entre eles é o kind.
- A extrutura que temos aqui é a seguinte:
    - deployment
        - replicaset
            - pod