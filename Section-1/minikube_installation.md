``` 
apt-get update
```
```
 sudo apt-get install curl
```
Minikube requires hardware virtualization for that we need to download and install virtualbox with its extension pack.

```
 sudo apt-get install virtualbox virtualbox-ext-pack
```
In the process it will ask you to accept the terms and condition hit OK and YES on it.

This guide is for the installation and configuration of minikube as elobrated in lecture.

We will make the directory for minkube

```
 mkdir minikube
```
```
 cd minikube
```

Download the minikube binary.

```
 curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

```

Now we will change the permission of minikube binary file

```
 chmod +x minikube
```
Now we will move it to /usr/local/bin

```
 sudo mv -v minikube /usr/local/bin
```
Now we will download the kubectl binary

```
 curl -Lo kubectl https://storage.googleapis.com/kubernetes-release/release/v1.8.0/bin/linux/amd64/kubectl
```
Now we will apply the same permission to kubectl utility

```
 chmod +x kubectl
```
As same we will move it to /usr/local/bin 
``` sudo mv -v kubectl
/usr/local/bin
```

Now to check the services that minikube has been installed

```
 kubectl get pods --all-namespaces
 ```
