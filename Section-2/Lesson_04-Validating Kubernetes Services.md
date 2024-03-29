Ensure that all the nodes are in ready state if not we can troubleshoot it. So the one reason would be the swap functionality enabled on the node or not.

 
``` 
swapoff -a (which disable the feature on swap on the current node)
``` 

If you want it to permenantly disable the swap comment the swap line in
`/etc/fstab` and type the below command

 
``` 
mount -a
``` 

For the confirmation 

 
``` 
free -h
``` 

 
``` 
cat /proc/swaps
``` 

If for some reason the swap feature is disabled than we need to check the kubelet service on that node.

 
``` 
kubelet logs node-01
``` 

Or if that is not working we need to ssh that node and get the logs of kubelet via journalctl command.

 
``` 
journalctl -u kubelet -f
``` 

Next we need to check the services of kubelet kube-proxy process running on the master and worker node

 
``` 
ps -aux | grep kube-proxy
``` 

and also for kubelet

 
``` 
ps -aux | grep kubelet
``` 

and finally we can get the overall information and status of the cluster using the kubectl


``` 
kubectl cluster-info
``` 
