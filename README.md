kloia Wordpress Migration from EC2 to GKE

Steps:
1- Create cluster on GKE with name wpress-cluster-1
2- Authenticate to the cluster: 

gcloud container clusters get-credentials wpress-cluster-1

3- Create persistent disks for MySQL and Wordpress

gcloud compute disks create --size 20GB mysql-disk
gcloud compute disks create --size 20GB kloiacom-wordpress-disk

4- Create secret

kubectl create secret generic mysql --from-literal=password=changeit

5- Create Mysql pod and service

kubectl create -f mysql.yaml
kubectl create -f mysql-service.yaml

6- Create Wordpress pod and service

kubectl create -f kloiacom-wordpress.yaml
kubectl create -f kloiacom-wordpress-service.yaml



