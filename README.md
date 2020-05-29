# liftbridge-helm-chart
A Helm Chart to bring up liftbridge.io on a Kubernetes cluster.

## Prerequistes
- NATS Operator should be deployed. [More information](https://github.com/nats-io/nats-operator/tree/master/helm/nats-operator)

## Deploy
```
helm upgrade --install lb liftbridge -n liftbridge --create-namespace   
``` 