1. installing argocd
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
2. expose service
```
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
```
3. access web ui
```
k get secret -n argocd argocd-initial-admin-secret --template='{{.data.password | base64decode}}'
```
4. setup private repo
```
get [github access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).
or [github app](https://docs.github.com/en/developers/apps/getting-started-with-apps/about-apps#about-github-apps)
```
5. create application
```
Application Name: sn-platform
Project: default
SYNC POLICY: Automatic
Repository URL: https://github.com/yuweisung/pulsar-ops.git
Revision: v2.9 Tags
Path: default
Destination: https://kubernetes.default.svc
Namespace: sn-platform
```
6. modify and push the CRs
```
git commit -m 'upgrade image version'
git tag -a -f <tag-name> <commit-hash>
git push origin v2.9 --force
```
