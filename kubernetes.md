# Instalar kubernetes 

Servidor Ubuntu 20.4

```
root@master:~# apt -y install docker.io apt-transport-https
Reading package lists... Done
Building dependency tree
Reading state information... Done
apt-transport-https is already the newest version (2.0.5).
docker.io is already the newest version (20.10.2-0ubuntu1~20.04.2).
0 upgraded, 0 newly installed, 0 to remove and 59 not upgraded.

```

# cgroup driver usando systemd

```
cat > /etc/docker/daemon.json <<EOF
{
  "exec-opts": ["native.cgroupdriver=systemd"],
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "100m"
  },
  "storage-driver": "overlay2"
}
EOF
```

#Startando Deamon no boot

```
 systemctl restart docker
 systemctl enable docker

```

#Configurando Karnel para Kubernetes

```
cat > /etc/sysctl.d/k8s.conf <<EOF
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
EOF
```
