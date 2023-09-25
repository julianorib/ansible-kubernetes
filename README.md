# Configurando um Cluster Kubernetes com Ansible

Este projeto cria um Cluster Kubernetes em um conjunto de Hosts com Ubuntu Linux.
<br>
Pode ser utilizado com qualquer provider.
<br>
O ideal é que se tenha ao menos 3 Hosts, sendo 1 para ControlPlane e 2 para Workers.


## Requisitos

- Tenha os IPs dos Hosts.
- Preencha o arquivo hosts.cfg com o IP dos Hosts.
- Tenha o ansible instalado (Linux)
*O ansible só funciona no Linux ou no Windows via WSL.*


## Detalhes do projeto

Este projeto executa o seguinte.

- Instala dependencias necessarias no Linux em todos os hosts
- Instala o ContainerD em todos os hosts
- Configura o ContainerD em todos os hosts

- Instala o Kubeadm, Kubectl, Kubelet em todos os hosts
- Configura os requisitos de Kubernetes em todos os hosts
- Reinicia todos os Hosts.

- Inicia/Cria um Cluster em 1 Host
- Instala um CNI (flannel)
- Configura os Workers no Cluster

- Configura o Usuario Ubuntu com o Kubeconfig no Host Controlplane.
- Copia o arquivo de config para a pasta atual.

## Faça o clone para sua estação
```
git clone 
```

## Execute o Playbook para instalação

```
ansible-playbook -i hosts.cfg -u ubuntu --private-key suachave playbook.yaml -b
```

## Validando

Acesse via SSH o Controlplane e digite:
```
kubectl get nodes
```