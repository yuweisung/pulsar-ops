## Lab 3 - Reconfig CRs

### Instructions

1. Modify br-cluster.yaml (optional: you can use git to control the version)

```
cat zk-cluster.yaml

apiVersion: zookeeper.streamnative.io/v1alpha1
kind: ZooKeeperCluster
metadata:
  name: my
  namespace: sn-platform
spec:
  image: streamnative/pulsar:2.9.2.20
  replicas: 3
  pod:
    resources:
      requests:
        cpu: "50m"
        memory: "256Mi"
  persistence:
    reclaimPolicy: Retain
    data:
      accessModes:
      - ReadWriteOnce
      resources:
        requests:
          storage: "5Gi"
    dataLog:
      accessModes:
      - ReadWriteOnce
      resources:
        requests:
          storage: "2Gi"
```

2. Reapply the zk-cluster.yaml

```
kubectl apply -f zk-cluster.yaml
```

3. Watch the pod

```
kubectl get pod -n pulsar -w
```
