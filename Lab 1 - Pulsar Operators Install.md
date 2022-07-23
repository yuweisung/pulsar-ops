## Lab 1 - Pulsar Operators Install

### Instructions:

1. Adding streamnative helm chart repo

```
helm repo add streamnative https://charts.streamnative.io
helm repo update
```

2. Searching pulsar-operator (list all versions)

```
helm search repo pulsar-operator -l

NAME                        	CHART VERSION	APP VERSION	DESCRIPTION
streamnative/pulsar-operator	0.11.5       	0.11.5     	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.11.1       	0.11.1     	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.11.0       	0.11.0     	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.10.3       	0.10.3     	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.10.0       	0.10.0     	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.9.0        	0.9.4      	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.8.23       	0.8.21     	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.8.22       	0.8.21     	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.8.21       	0.8.21     	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.8.17       	0.8.17     	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.8.11       	0.8.10     	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.8.10       	0.8.10     	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.8.9        	0.8.9      	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.8.7        	0.7.4      	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.7.4        	0.7.4      	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.7.2        	0.7.2      	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.7.1        	0.7.0      	Apache Pulsar Operators Helm chart for Kubernetes
streamnative/pulsar-operator	0.7.0        	0.7.0      	Apache Pulsar Operators Helm chart for Kubernetes
```

3. Installing pulsar-operator
```
kubectl create namespace sn-system
helm install pulsar-operator -n sn-system streamnative/pulsar-operator
```

4. Checking operator status
```
kubectl get pod -n sn-system

NAME                                                             READY   STATUS    RESTARTS   AGE
pulsar-operator-bookkeeper-controller-manager-559f6c7c9f-bzpmf   1/1     Running   0          34s
pulsar-operator-zookeeper-controller-manager-6bccdb8469-48qtk    1/1     Running   0          34s
pulsar-operator-pulsar-controller-manager-6776667bf9-ftbbs       1/1     Running   0          34s
```
5. Checking api endpoints
```
kubectl api-resources | egrep 'streamnative'

bookkeeperclusters                bk            bookkeeper.streamnative.io/v1alpha1    true         BookKeeperCluster
pulsarbrokers                     pb,broker     pulsar.streamnative.io/v1alpha1        true         PulsarBroker
zookeeperclusters                 zk            zookeeper.streamnative.io/v1alpha1     true         ZooKeeperCluster
```
6. Explaining CR
```
kubectl explain zookeeperclusters 
kubectl explain zookeeperclusters.spec
kubectl explain zookeeperclusters --recursive=true > zk-template.txt
```



