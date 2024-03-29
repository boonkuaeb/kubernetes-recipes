Now first we need to update all our nodes including kube-master, node-01, node-02.


```
 apt-get update && apt-get upgrade -y (on all nodes kube-master, node-01, node-02)
```

```
 apt install -y docker.io (on all nodes kube-master, node-01, node-02)
```


```
 curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - (on all nodes kube-master, node-01, node-02)
```


```
 vi /etc/apt/sources.list.d/kubernetes.list (on all nodes kube-master, node-01, node-02)

deb https://apt.kubernetes.io/ kubernetes-xenial main
```


```
 apt update (on all nodes kube-master, node-01, node-02)
```


```
 apt install -y kubelet kubeadm kubectl -y (on all nodes kube-master, node-01, node-02)
```


```
 swapoff -a (on all nodes kube-master, node-01, node-02)
```


```
 kubeadm init --pod-network-cidr=10.244.0.0/16
```

Now copy the one long command for kubeadm join for other nodes. In your case it would be different.


```
 kubeadm join 192.168.86.129:6443 --token 8951if.kmexn0g6z6xe2vnv --discovery-token-ca-cert-hash sha256:dde332f05cf2a84685dbaeb7324c01db142f213da0664eac94fa1023a3d37e6d 
```

Your need to run the following as a regular user.


```
 exit
```

The below command has to be done on kubernetes master.

Now we will exit from our root user and run the three commands mentioned below 

Creating a directory for kube configuration

```
 mkdir -p $HOME/.kube
Copying the necessary admin configuration files
```

```
 sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
Assigning proper permission to access the kube folder.
```

```
 sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

Now we get all the pods


```
 kubectl get pods --all-namespaces
```

To start flannel we need to tell kubectl to apply a proper .yaml file


```
 kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/bc79dd1505b0c8681ece4de4c0d86c5cd2643275/Documentation/kube-flannel.yml
```

After that we will check the flannel pod.

```
 kubectl get pods --all-namespaces
```
