## Lab 1.1 - OLM Pulsar Operators Install

### Instructions

1. install operator-sdk

```
brew install operator-sdk
```

2. Install olm operator

```
operator-sdk olm install
```

3. Searching operator

```
kubectl -n olm get packagemanifest
```

4. Installing pulsar-operator
```
kubectl create -f https://operatorhub.io/install/bookkeeper-operator.yaml
kubectl create -f https://operatorhub.io/install/zookeeper-operator.yaml
kubectl create -f https://operatorhub.io/install/pulsar-operator.yaml
kubectl create -f https://operatorhub.io/install/function-mesh.yaml
```

5. Checking operator status
```
kubectl get csv -n operators
```
