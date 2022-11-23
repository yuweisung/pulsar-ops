## Lab 7 mTLS hardway with sn-platform
### Self-signed CA and wide card key/cert
```
# self-sign ca key/cert
openssl req -x509 -newkey rsa:2048 -nodes -keyout ca-key.pem -keyform PEM -days 365 -subj '/CN=snp.cluster.local' -out ca-crt.pem
# broker key and csr
openssl req -newkey rsa:2048 -keyout generic-key.pem -keyform PEM -out generic.csr -keyform PEM -subj '/CN=*.svc.snp.cluster.local'
# decrypt broker key
openssl rsa -in generic-key.pem -out generic-key.pem
# signing
openssl x509 -req -days 360 -in generic.csr -CA ca-crt.pem -CAkey ca-key.pem -CAcreateserial -out generic-crt.pem
# create tls/ca secret
kubectl -n snp create secret generic generic-tls --from-file=ca.crt=./ca-crt.pem --from-file=tls.crt=./generic-crt.pem --from-file=tls.key=./generic-key.pem
kubectl -n snp create secret generic ca-tls --from-file=ca-crt.pem
```
### update caCertName and certSecretName in values.yaml
```

```
### client certs
```
openssl req -newkey rsa:2048 -keyout client-key.pem -keyform PEM -out client.csr -keyform PEM -subj '/CN=admin'
openssl rsa -in client-key.pem -out client-key.pem
openssl x509 -req -days 360 -in client.csr -CA ca-crt.pem -CAkey ca-key.pem -CAcreateserial -out client-crt.pem 
kubectl -n snp create secret generic client-tls --from-file=ca.crt=./ca-crt.pem --from-file=tls.crt=./client-crt.pem --from-file=tls.key=./client-crt.pem
```
### re-apply the release
```
kubectl create ns snp
helm upgrade --install -n snp snp1 streamnative/sn-platform --set initialize=true -f sn-platform/1-basic_mtls.yaml
```
