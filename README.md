# k8s-example

__Kube Ctl__  

- Baixando o binário
 ```
 curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

- Instalando
```
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```
- Confirmando versão
``` 
kubectl version --client
```


__Kind__

 - Kind é uma ferramenta para executar clusters locais

- Instalando:

```
sudo curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.11.1/kind-linux-amd64
sudo chmod +x ./kind
sudo mv ./kind /usr/bin/kind
```

- Confirmando vesão
  ```
  kind --version
  ```

__Criando Clusters__  


- Criando com default
```
  kind create cluster
```
- Verificando
```
kind get clusters
```
- Criando cluster com nome desejado
```
kind create cluster --name clustername
```

__Usando o Kubectl__

Kubectl é um cliente para o Kubernets, que é controlado por uma API REST

Utiliza arquivos de configuração (cubeconfig) para organizar informaçoes sobre clusters, usuarios,k namespaces e mecanismos de autenticação.

Um elemento de contexto agrupa tres parametros em um nome escolhido:
    - Cluster
    - Namespace
    - Usuario

O kubectl se conecta a um cluster por vez (modificar o kind-nome_do_cluster para infos dos outros)

```
kubectl cluster-info --context kind-kind
```
- Retorno
  ```
  Kubernetes control plane is running at https://127.0.0.1:44169
CoreDNS is running at https://127.0.0.1:44169/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

 - Deletando clusters
```
kind delete clusters kind
``` 

__Multinode__  

Arquivo de configuração criado no diretório k8s

Comando para criar o cluster:
```
kind create cluster --name k8s-example --config kind-config.yml
```
Listando os nos

```
kubectl get nodes
```

Saida

```
NAME                        STATUS     ROLES                  AGE   VERSION
k8s-example-control-plane   Ready      control-plane,master   99s   v1.21.1
k8s-example-worker          NotReady   <none>                 57s   v1.21.1
k8s-example-worker2         NotReady   <none>                 57s   v1.21.1
``` 

Verificando informaçoes do contexto

```
kubectl cluster-info --context kind-k8s-example
```










   

