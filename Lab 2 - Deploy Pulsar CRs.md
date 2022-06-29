Lab 2 - Deploy Pulsar CRs

1. Downloading CR examples

git clone https://github.com/yuweisung/pulsar-ops.git
cd pulsar-ops/default

2. Customizing the zk-cluster spec

# Modifying pod resources

cat zk-cluster.yaml

apiVersion: zookeeper.streamnative.io/v1alpha1
kind: ZooKeeperCluster
metadata:
  name: my
  namespace: pulsar
spec:
  image: streamnative/pulsar:2.9.2.17
  replicas: 1
  pod:
    resources:
      requests:
        cpu: "50m"
        memory: "128Mi"
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


3. Creating the zk-cluster CR

# Open a terminal and watch the zk operator log
kubectl logs -n sn-system pulsar-operator-zookeeper-controller-manager-6bccdb8469-48qtk -f

# In another terminal, create namespace and apply the CR
kubectl create namespace pulsar

kubectl apply -n pulsar -f zk-cluster.yaml

# Record the zk service name/Cluster-IP
kubectl get service -n pulsar

4. Creating the bk-cluster CR

# Modify the pod resources
# Add zk-service name to zkServers

cat bk-cluster.yaml

apiVersion: bookkeeper.streamnative.io/v1alpha1
kind: BookKeeperCluster
metadata:
  name: my
  namespace: pulsar
spec:
  image: streamnative/pulsar:2.9.2.17
  replicas: 3
  pod:
    resources:
      requests:
        cpu: "100m"
        memory: "128Mi"
  storage:
    reclaimPolicy: Retain
    journal:
      numDirsPerVolume: 1
      numVolumes: 1
      volumeClaimTemplate:
        accessModes:
        - ReadWriteOnce
        resources:
          requests:
            storage: "8Gi"
    ledger:
      numDirsPerVolume: 1
      numVolumes: 1
      volumeClaimTemplate:
        accessModes:
        - ReadWriteOnce
        resources:
          requests:
            storage: "16Gi"
  zkServers: my-zk-headless:2181

kubectl apply -n pulsar -f bk-cluster.yaml

# Watch the pod

kubectl get pod -n pulsar -w

5. Creating the br-cluster CR

# Modify the pod resource
# Add zk-service name to zkServers

cat br-cluster.yaml

apiVersion: pulsar.streamnative.io/v1alpha1
kind: PulsarBroker
metadata:
  name: my
  namespace: pulsar
spec:
  image: streamnative/pulsar:2.9.2.17
  pod:
    resources:
      requests:
        cpu: 200m
        memory: 256Mi
    terminationGracePeriodSeconds: 30
  config:
    custom:
      webSocketServiceEnabled: "true"
  replicas: 1
  zkServers: my-zk-headless:2181

kubectl apply -n pulsar br-cluster.yaml

# Watch the pod

kubectl get pod -n pulsar -w

# Record the zk service name/Cluster-IP

kubectl get service -n pulsar

6. Creating the px-cluster CR

# Modify the pod resource
# Add broker-service name to brokerAddress

cat px-cluster.yaml

apiVersion: pulsar.streamnative.io/v1alpha1
kind: PulsarProxy
metadata:
    name: my
    namespace: pulsar
spec:
    brokerAddress: my-broker-headless
    dnsNames: []
    #webSocketServiceEnabled: true
    image: streamnative/pulsar:2.9.2.17
    config:
      tls:
        enabled: false
    issuerRef:
      name: ""
    pod:
      resources:
        requests:
          cpu: 100m
          memory: 128Mi
    replicas: 1

kubectl apply -n pulsar px-cluster.yaml

# Watch the pod

kubectl get pod -n pulsar -w




