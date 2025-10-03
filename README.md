# Redis Helm Chart

A Helm chart for deploying Redis 7.2 on Kubernetes.

## Installation

```bash
helm install my-redis ./redis-chart
```

## Configuration

The following table lists the configurable parameters of the Redis chart and their default values.

| Parameter | Description | Default |
|-----------|-------------|---------|
| `replicaCount` | Number of Redis replicas | `1` |
| `image.repository` | Redis image repository | `redis` |
| `image.tag` | Redis image tag | `7.2` |
| `image.pullPolicy` | Image pull policy | `IfNotPresent` |
| `service.type` | Kubernetes service type | `ClusterIP` |
| `service.port` | Redis service port | `6379` |
| `redis.password` | Redis password (empty = no auth) | `""` |
| `redis.maxmemory` | Max memory limit | `256mb` |
| `redis.maxmemoryPolicy` | Eviction policy | `allkeys-lru` |
| `persistence.enabled` | Enable persistent storage | `true` |
| `persistence.storageClass` | Storage class name | `""` |
| `persistence.accessMode` | PVC access mode | `ReadWriteOnce` |
| `persistence.size` | PVC size | `8Gi` |
| `resources.limits.cpu` | CPU limit | `500m` |
| `resources.limits.memory` | Memory limit | `512Mi` |
| `resources.requests.cpu` | CPU request | `250m` |
| `resources.requests.memory` | Memory request | `256Mi` |

## Examples

### Install with custom password

```bash
helm install my-redis ./redis-chart --set redis.password=mypassword
```

### Install without persistence

```bash
helm install my-redis ./redis-chart --set persistence.enabled=false
```

### Install with custom memory settings

```bash
helm install my-redis ./redis-chart \
  --set redis.maxmemory=512mb \
  --set redis.maxmemoryPolicy=allkeys-lfu
```
