# Configuração Secret para Certificado Traefik

Para colocar um certificado Wildcard para utilização no Traefik.\
Copie o crt e chave para o primeiro control plane (master).

Crie um secret:
```
kubectl create secret tls seudominio-secret --cert=certificado.crt --key=certificado-key.pem
```

**Crie este mesmo secret para todos os namespace que for utilizá-lo.**

```
kubectl create secret tls seudominio-secret --cert=certificado.crt --key=certificado-key.pem -n traefik

kubectl create secret tls seudominio-secret --cert=certificado.crt --key=certificado-key.pem -n monitoring
```

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
