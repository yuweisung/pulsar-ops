# pulsar-ops
## Pre-requisites
1. [GKE](https://github.com/streamnative/global-se-practice/tree/pulsar-ops/gke/README.md)
2. [Kind](https://github.com/streamnative/global-se-practice/tree/pulsar-ops/kind/README.md)

## 1. Pulsar Operator Installation

[Lab 1](https://github.com/streamnative/global-se-practice/tree/pulsar-ops/Lab%201%20-%20Pulsar%20Operators%20Install.md) describes the instructions of pulsar operator

## 2. Deploy Pulsar CRs

[Lab 2](https://github.com/streamnative/global-se-practice/tree/pulsar-ops/Lab%202%20-%20Deploy%20Pulsar%20CRs.md) describes the instructions of pulsar CRs

## 3. Reconfigure CRs

[Lab 3](https://github.com/streamnative/global-se-practice/tree/pulsar-ops/Lab%203%20-%20Reconfig%20CRs.md) describes the reconfiguration of CRs

## 4. Use SN-Platform to compose Pulsar cluster

[Lab 4](https://github.com/streamnative/global-se-practice/tree/pulsar-ops/Lab%204%20-%20sn-platform%20install.md) describes the instructions of sn-platform composition.

## 5. SN-Platform Deep Dive

[Lab 5](https://github.com/streamnative/global-se-practice/tree/pulsar-ops/Lab%205%20-%20sn-platform%20Deep%20Dive.md) describes the instructions of sn-platform deep dive

## 6. SN-Platform Self-signed TLS

[Lab 6](https://github.com/streamnative/global-se-practice/tree/pulsar-ops/Lab%206%20-%20sn-platform%20self-sign.md) describe how to setup self-signed tls without cert-manager

---
## Some sn-platform examples

* [1-basic](sn-platform/1-basic.yaml) - 3 zk, 3 bk, 1 br and 1 autorecovery.
* [2-basic_toolset](sn-platform/2-basic_toolset.yaml) - 3 zk, 3 bk, 1 br and 1 toolset.
* [3-basic_proxy](sn-platform/3-basic_proxy.yaml) - 3 zk, 3 bk, 2 br and 1 proxy.
* [4-basic_monitoring](sn-platform/4-basic_monitoring.yaml) - 3 zk, 3 bk, 2br, 1 proxy, prome and grafana
* [5-basic_monitoring_2.9.3.2](sn-platform/5-basic_monitoring_2.9.3.2.yaml) - upgrade images from 2.9.2.10 to 2.9.3.2
* [6-basic_monitoring_2.10.1.3](sn-platform/6-basic_monitoring_2.10.1.3.yaml) - upgrade images to 2.10.1.3
