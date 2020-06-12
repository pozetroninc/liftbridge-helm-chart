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
## Chart Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| replicaCount | int | `3` | Number of Pods to create. |
| liftbridge.port | int | `9092` | Port for liftbridge |
| liftbridge.loglevel | string | `"info"` | Log level for liftbridge logging |
| liftbridge.minInsyncReplicas | int | `1` | Min number of replicas of data [More info](https://liftbridge.io/docs/ha-and-consistency-configuration.html#minimum-in-sync-replica-set) |
| nats[] | list | List of nats address | List of nats addresses, port and auth |
| nats[].address | string | `nats-cluster.nats-io.svc` | Address/hostname to the running nats cluster |
| nats[].port | int | `4222` | Port of the nat cluster |
| nats[].port.auth.enabled | boolean | `true` | Set to true if NATS cluster is secured by authentication |
| nats[].port.auth.username | string | `my-user` | Username for the NATS cluster |
| nats[].port.auth.password| string | - | `"Username for the NATS cluster"` |
| image.repository | string | `"pozetroninc/liftbridge"` | The Docker (Hub) repository for the image. |
| image.tag | string | `""` | The version of KeyDB to install e.g. "v5.3.3" |
| persistence.enabled | bool | `false` |  |
| persistence.size | string | `1G` | How much persistent storage for each pod. |
| persistence.accessMode | string | `ReadWriteOnce` | The [storage class](https://kubernetes.io/docs/concepts/storage/storage-classes/) |

### Contributors

Special thanks to: [Hazim](https://github.com/hazim1093)
