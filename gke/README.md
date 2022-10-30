## setup and login gcloud
```
brew install --cask google-cloud-sdk
gcloud init
gcloud components install gke-gcloud-auth-plugin
gcloud auth login
```
## gke parameters
```
export PROJECT=sn-se-playground
export GKE_CLUSTER_NAME=sn-se-ysung1
export REGION=us-central1
export ZONE=us-central1-c
export K8S_VERSION=1.23.8-gke.1900
export MACHINE_TYPE=e2-standard-2
export DISK_SIZE=100
export NUM_NODES=3
```
### create a gke cluster
```
gcloud container clusters create $GKE_CLUSTER_NAME \
  --project $PROJECT \
	--zone $ZONE \
	--enable-dataplane-v2 \
	--no-enable-basic-auth \
	--cluster-version $K8S_VERSION \
	--release-channel "regular" \
	--machine-type $MACHINE_TYPE \
	--image-type "COS_CONTAINERD" \
	--disk-type "pd-standard" \
	--disk-size $DISK_SIZE \
	--metadata disable-legacy-endpoints=true \
	--num-nodes $NUM_NODES \
	--logging=SYSTEM,WORKLOAD \
	--monitoring=SYSTEM \
	--enable-ip-alias \
	--network "projects/$PROJECT/global/networks/default" \
	--subnetwork "projects/$PROJECT/regions/$REGION/subnetworks/default" \
	--no-enable-intra-node-visibility \
	--default-max-pods-per-node "110" \
	--no-enable-master-authorized-networks \
	--addons HorizontalPodAutoscaling,HttpLoadBalancing,GcePersistentDiskCsiDriver \
	--enable-autoupgrade \
	--enable-autorepair \
	--max-surge-upgrade 1 \
	--max-unavailable-upgrade 0 \
	--node-locations $ZONE
```
## get gke credential
```
gcloud container clusters get-credentials $GKE_CLUSTER_NAME --zone $ZONE
```
## delete gke cluster
```
gcloud container clusters delete $GKE_CLUSTER_NAME --zone $ZONE --quiet
```