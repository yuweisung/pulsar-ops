## Lab 4 - SN-Platform

### Instructions

1. Fetch sn-platform chart

```
cd <workspace>
helm fetch streamnative/sn-platform --untart
cd sn-platform
```

2. Creating an value-overrides.yaml
```
vi value-overrides.yaml
```

3. Disable/Enable components in sn-platform

Add the following to the values-overrides.yaml.

```
components:
  vault: false
  functions: false
  toolset: false
  streamnative_console: false
  pulsar_detector: false

```

4. Install sn-platform

```
kubectl create namespace sn-training
helm install sn-platform -n sn-training streamnative/sn-platform -f value-overrides.yaml
```

5. Watch the pods

```
kubectl get pod -n sn-training -w
```
