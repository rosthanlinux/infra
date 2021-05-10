
# configuração inicial no nó mestre.

Para a opção [--apiserver-advertise-address], especifique o endereço IP que o servidor da API Kubernetes escuta.

Para a opção [--pod-network-cidr], especifique a rede que a Rede Pod usa.

Existem alguns plug-ins para Pod Network. (consulte os detalhes abaixo): 

  ⇒ https://kubernetes.io/docs/concepts/cluster-administration/networking/

Neste exemplo para flag, especifique [--pod-network-cidr = 10.244.0.0/16] para permitir que a Rede Pod funcione normalmente.

Para Verificar seu IP pode utilizar o comando ip addr | grep inet

```
kubeadm init --apiserver-advertise-address=<Seu IP> --pod-network-cidr=10.244.0.0/16
...
...
mkdir -p $HOME/.kube
cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
chown $(id -u):$(id -g) $HOME/.kube/config

```

# Configurando a rede de Pods com Flannel

```
kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
kubectl get nodes
kubectl get pods -A
```


