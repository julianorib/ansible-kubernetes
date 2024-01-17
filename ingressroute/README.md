# Criação dos Ingress para acesso ao monitoramento.

Defina os nomes DNS que serão utilizados para acessar Traefik, Prometheus e Grafana.

Acessar o primeiro control plane (master)

Copiar os yaml da raiz do projeto para o master. 
- Traefik.yaml
- Prometheus.yaml
- Grafana.yaml 

Modificar o match: Host com o DNS definido.\
Modificar o secretName com a secret criada.

```
kubectl apply -f traefik.yaml
kubectl apply -f prometheus.yaml
kubectl apply -f grafana.yaml
```

**Senha admin grafana: prom-operator**
