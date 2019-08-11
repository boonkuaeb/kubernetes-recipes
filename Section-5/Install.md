```
curl -LO https://git.io/get_helm.sh

chmod 700 get_helm.sh

./get_helm.sh
```


```
kubectl --namespace=kube-system create clusterrolebinding add-on-cluster-admin --clusterrole=cluster-admin --serviceaccount=kube-system:default

```

```
git clone https://github.com/kubernetes/charts
```


```
helm init
```


```
helm install -f Section-5/Prometheus.yml charts/stable/prometheus --name prometheus --namespace prometheus
```
Save DNS of Prometheus


```
helm install -f Section-5/Grafana.yml charts/stable/grafana --name grafana --namespace grafana
```

```
kubectl expose deployment grafana --type="NodePort" --name grafana-ext --port=3000 -n grafana
```
