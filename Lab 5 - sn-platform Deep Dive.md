## Lab 5 - sn-platform Deep Dive

### Instructions

1. Create all sn-platform manifests
```
helm template sn-platform -n sn-training streamnative/sn-platform -f value-overrides.yaml --output-dir sn-training

wrote sn-training/sn-platform/templates/detector/pulsar-detector-pdb.yaml
wrote sn-training/sn-platform/templates/bookkeeper/bookkeeper-service-account.yaml
wrote sn-training/sn-platform/templates/broker/broker-service-account.yaml
wrote sn-training/sn-platform/templates/detector/pulsar-detector-service-account.yaml
wrote sn-training/sn-platform/templates/prometheus/pulsar-operators-rbac.yaml
wrote sn-training/sn-platform/templates/proxy/proxy-service-account.yaml
wrote sn-training/sn-platform/templates/streamnative-console/streamnative-console-service-account.yaml
wrote sn-training/sn-platform/templates/toolset/toolset-serviceaccount.yaml
wrote sn-training/sn-platform/templates/vault/vault-service-account.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-backup-serviceaccount.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-restore-serviceaccount.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-service-account.yaml
wrote sn-training/sn-platform/templates/grafana/grafana-admin-secret.yaml
wrote sn-training/sn-platform/templates/vault/vault-public-key-secret.yaml
wrote sn-training/sn-platform/templates/alert-manager/alertmanager-configmap.yaml
wrote sn-training/sn-platform/templates/broker/broker-configmap-functionmesh.yaml
wrote sn-training/sn-platform/templates/broker/function-worker-configfile-configmap.yaml
wrote sn-training/sn-platform/templates/broker/function-worker-configmap.yaml
wrote sn-training/sn-platform/templates/grafana/grafana-configmap.yaml
wrote sn-training/sn-platform/templates/prometheus/prometheus-configmap.yaml
wrote sn-training/sn-platform/templates/streamnative-console/streamnative-console-configmap.yaml
wrote sn-training/sn-platform/templates/toolset/toolset-configmap.yaml
wrote sn-training/sn-platform/templates/vault/vault-configmap.yaml
wrote sn-training/sn-platform/templates/vault/vault-configmap.yaml
wrote sn-training/sn-platform/templates/zookeeper/gen-zk-conf.yaml
wrote sn-training/sn-platform/templates/prometheus/prometheus-pvc.yaml
wrote sn-training/sn-platform/templates/streamnative-console/streamnative-console-pvc.yaml
wrote sn-training/sn-platform/templates/bookkeeper/bookkeeper-cluster-role-binding.yaml
wrote sn-training/sn-platform/templates/broker/broker-cluster-role-binding.yaml
wrote sn-training/sn-platform/templates/prometheus/pulsar-operators-rbac.yaml
wrote sn-training/sn-platform/templates/bookkeeper/bookkeeper-cluster-role-binding.yaml
wrote sn-training/sn-platform/templates/broker/broker-cluster-role-binding.yaml
wrote sn-training/sn-platform/templates/prometheus/pulsar-operators-rbac.yaml
wrote sn-training/sn-platform/templates/vault/vault-service-account.yaml
wrote sn-training/sn-platform/templates/vault/vault-service-account.yaml
wrote sn-training/sn-platform/templates/alert-manager/alertmanager-service.yaml
wrote sn-training/sn-platform/templates/detector/pulsar-detector-service.yaml
wrote sn-training/sn-platform/templates/grafana/grafana-service.yaml
wrote sn-training/sn-platform/templates/prometheus/prometheus-service.yaml
wrote sn-training/sn-platform/templates/streamnative-console/streamnative-console-service.yaml
wrote sn-training/sn-platform/templates/toolset/toolset-service.yaml
wrote sn-training/sn-platform/templates/node-exporter/node-exporter.yaml
wrote sn-training/sn-platform/templates/alert-manager/alertmanager-deployment.yaml
wrote sn-training/sn-platform/templates/detector/pulsar-detector-deployment.yaml
wrote sn-training/sn-platform/templates/grafana/grafana-statefulset.yaml
wrote sn-training/sn-platform/templates/prometheus/prometheus-statefulset.yaml
wrote sn-training/sn-platform/templates/streamnative-console/streamnative-console-statefulset.yaml
wrote sn-training/sn-platform/templates/toolset/toolset-statefulset.yaml
wrote sn-training/sn-platform/templates/control-center/control-center-ingress.yaml
wrote sn-training/sn-platform/templates/bookkeeper/bookkeeper-authorizationpolicy.yaml
wrote sn-training/sn-platform/templates/bookkeeper/bookkeeper-role-binding.yaml
wrote sn-training/sn-platform/templates/bookkeeper/bookkeeper-storageclass.yaml
wrote sn-training/sn-platform/templates/broker/broker-authorizationpolicy.yaml
wrote sn-training/sn-platform/templates/broker/broker-configmap-functionmesh.yaml
wrote sn-training/sn-platform/templates/broker/broker-role-binding.yaml
wrote sn-training/sn-platform/templates/broker/broker-secret.yaml
wrote sn-training/sn-platform/templates/control-center/control-center-gateway.yaml
wrote sn-training/sn-platform/templates/control-center/control-center-virtualservice.yaml
wrote sn-training/sn-platform/templates/control-center/ingress-controller-configmap.yaml
wrote sn-training/sn-platform/templates/control-center/ingress-controller-deployment.yaml
wrote sn-training/sn-platform/templates/control-center/ingress-controller-rbac.yaml
wrote sn-training/sn-platform/templates/control-center/ingress-controller-service.yaml
wrote sn-training/sn-platform/templates/custom-metric-server/custom-metric-server-init.yaml
wrote sn-training/sn-platform/templates/custom-metric-server/custom-metric-server-prometheus.yaml
wrote sn-training/sn-platform/templates/custom-metric-server/custom-metric-server.yaml
wrote sn-training/sn-platform/templates/detector/pulsar-detector-authorizationpolicy.yaml
wrote sn-training/sn-platform/templates/entities/connection.yaml
wrote sn-training/sn-platform/templates/entities/namespaces.yaml
wrote sn-training/sn-platform/templates/entities/permissions.yaml
wrote sn-training/sn-platform/templates/entities/tenants.yaml
wrote sn-training/sn-platform/templates/entities/topics.yaml
wrote sn-training/sn-platform/templates/external-dns/external-dns-rbac.yaml
wrote sn-training/sn-platform/templates/external-dns/external-dns.yaml
wrote sn-training/sn-platform/templates/extra.yaml
wrote sn-training/sn-platform/templates/function-worker/function-worker-cluster-role-binding.yaml
wrote sn-training/sn-platform/templates/function-worker/function-worker-role-binding.yaml
wrote sn-training/sn-platform/templates/function-worker/function-worker-service-account.yaml
wrote sn-training/sn-platform/templates/function-worker/function-worker-service.yaml
wrote sn-training/sn-platform/templates/function-worker/function-worker-statefulset.yaml
wrote sn-training/sn-platform/templates/grafana/grafana-authorizationpolicy.yaml
wrote sn-training/sn-platform/templates/grafana/grafana-azuread-secret.yaml
wrote sn-training/sn-platform/templates/grafana/grafana-deployment.yaml
wrote sn-training/sn-platform/templates/grafana/grafana-storageclass.yaml
wrote sn-training/sn-platform/templates/grafana/loki-authorizationpolicy.yaml
wrote sn-training/sn-platform/templates/istio/default-peerauthentication.yaml
wrote sn-training/sn-platform/templates/namespace.yaml
wrote sn-training/sn-platform/templates/openshift/scc-role.yaml
wrote sn-training/sn-platform/templates/openshift/scc-rolebinding.yaml
wrote sn-training/sn-platform/templates/openshift/scc.yaml
wrote sn-training/sn-platform/templates/presto/presto-coordinator-configmap.yaml
wrote sn-training/sn-platform/templates/presto/presto-coordinator-statefulset.yaml
wrote sn-training/sn-platform/templates/presto/presto-service-ingress.yaml
wrote sn-training/sn-platform/templates/presto/presto-service.yaml
wrote sn-training/sn-platform/templates/presto/presto-worker-configmap.yaml
wrote sn-training/sn-platform/templates/presto/presto-worker-service.yaml
wrote sn-training/sn-platform/templates/presto/presto-worker-statefulset.yaml
wrote sn-training/sn-platform/templates/prometheus/prometheus-authorizationpolicy.yaml
wrote sn-training/sn-platform/templates/prometheus/prometheus-storageclass.yaml
wrote sn-training/sn-platform/templates/proxy/proxy-secret.yaml
wrote sn-training/sn-platform/templates/pulsar-coordinator/pulsar-coordinator.yaml
wrote sn-training/sn-platform/templates/streamnative-console/streamnative-console-authorizationpolicy.yaml
wrote sn-training/sn-platform/templates/streamnative-console/streamnative-console-azure-oauth2-secret.yaml
wrote sn-training/sn-platform/templates/streamnative-console/streamnative-console-google-oauth2-secret.yaml
wrote sn-training/sn-platform/templates/streamnative-console/streamnative-console-initialize.yaml
wrote sn-training/sn-platform/templates/streamnative-console/streamnative-console-okta-oauth2-secret.yaml
wrote sn-training/sn-platform/templates/streamnative-console/streamnative-console-storageclass.yaml
wrote sn-training/sn-platform/templates/tls/istio/tls-cert-internal-issuer.yaml
wrote sn-training/sn-platform/templates/tls/istio/tls-cert-public-issuer.yaml
wrote sn-training/sn-platform/templates/tls/istio/tls-certs.yaml
wrote sn-training/sn-platform/templates/tls/keytool.yaml
wrote sn-training/sn-platform/templates/tls/tls-cert-internal-issuer.yaml
wrote sn-training/sn-platform/templates/tls/tls-cert-public-issuer.yaml
wrote sn-training/sn-platform/templates/tls/tls-certs-internal.yaml
wrote sn-training/sn-platform/templates/tls/tls-certs-public.yaml
wrote sn-training/sn-platform/templates/vault/vault-authorizationpolicy.yaml
wrote sn-training/sn-platform/templates/vault/vault-clear-resource.yaml
wrote sn-training/sn-platform/templates/vault/vault-initialize-public-key.yaml
wrote sn-training/sn-platform/templates/vault/vault-initialize.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-authorizationpolicy.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-backup-clusterrolebinding.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-backup-configmap.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-backup-rolebinding.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-backup-service.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-backup-statefulset.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-restore-clusterrolebinding.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-restore-configmap.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-restore-rolebinding.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-storageclass.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-storageclass.yaml
wrote sn-training/sn-platform/templates/bookkeeper/bookkeeper-cluster.yaml
wrote sn-training/sn-platform/templates/broker/broker-cluster.yaml
wrote sn-training/sn-platform/templates/proxy/proxy-cluster.yaml
wrote sn-training/sn-platform/templates/vault/vault-statefulset.yaml
wrote sn-training/sn-platform/templates/zookeeper/zookeeper-cluster.yaml
```

2. Review the content of zookeeper-cluster.yaml and relative manifests

3. Review the content of bookkeeper-cluster.yaml and relative manifests

4. Review the content of broker-cluster.ymal and relative manifests


