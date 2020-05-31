# liftbridge-helm-chart
A Helm Chart to bring up liftbridge.io on a Kubernetes cluster.

## Prerequistes
NATS should already be deployed. If it's not you can install it with the following.

```
$ helm repo add nats https://nats-io.github.io/k8s/helm/charts/
$ helm repo update
$ helm install nats-cluster --namespace nats-io --set cluster.auth.enabled=true,cluster.auth.username=my-user,cluster.auth.password=T0pS3cr3t nats/nats --create-namespace
```

## Deploy
```
$ helm repo add pozetron https://www.pozetron.com/helm
$ helm repo update
$ helm search repo pozetron
$ helm upgrade --install liftbridge --namespace liftbridge-io pozetron/liftbridge --create-namespace   
```

### Contributors

Special thanks to: [Hazim](https://github.com/hazim1093)
