
# configuração do master node on premisse.

Para a opção [--apiserver-advertise-address], especifique o endereço IP que o servidor da API Kubernetes escuta.

Para a opção [--pod-network-cidr], especifique a rede que a Rede Pod usa.

Existem alguns plug-ins para Pod Network. (consulte os detalhes abaixo): 

  ⇒ https://kubernetes.io/docs/concepts/cluster-administration/networking/

Neste exemplo para flag, especifique [--pod-network-cidr = 10.244.0.0/16] para permitir que a Rede Pod funcione normalmente.

Para Verificar seu IP pode utilizar o comando ip addr | grep inet

```
kubeadm init --apiserver-advertise-address=<Seu IP> --pod-network-cidr=10.244.0.0/16


==== ### OUTPUT DO COMANDO ### ====
Your Kubernetes control-plane has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

Alternatively, if you are the root user, you can run:

  export KUBECONFIG=/etc/kubernetes/admin.conf

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

Then you can join any number of worker nodes by running the following on each as root:

kubeadm join <Seu IP>:6443 --token xu5skb.ola2ifa3aqxp9mhi \
        --discovery-token-ca-cert-hash sha256:5eede42ea30f93b84908bda157318b911a1156d589249744df745fabc3f0072b

==== ### FIM ### ====
...
...
mkdir -p $HOME/.kube
cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
chown $(id -u):$(id -g) $HOME/.kube/config

```

# Configurando a rede de Pods com Flannel

```
kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml

#Para ver informações sobre os Nodes

kubectl get nodes

# Para Listar os pods. No momento somente os Pods default do k8s estão disponiveis já que não fizemos nenhum deploy no nosso ainda pequeno cluster.

kubectl get pods -A
```





