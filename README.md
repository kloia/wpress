## kloia Wordpress Migration from EC2 to GKE ##<br />
<br />
Steps: <br />
1- Create cluster on GKE with name wpress-cluster-1 <br />
2- Authenticate to the cluster:  <br />
<br />
gcloud container clusters get-credentials wpress-cluster-1 <br />
<br />
3- Create persistent disks for MySQL and Wordpress<br />

gcloud compute disks create --size 20GB mysql-disk<br />
gcloud compute disks create --size 20GB kloiacom-wordpress-disk<br />
<br />
4- Create secret<br />
<br />
kubectl create secret generic mysql --from-literal=password=changeit<br />
<br />
5- Create Mysql pod and service<br />
<br />
kubectl create -f mysql.yaml<br />
kubectl create -f mysql-service.yaml<br />
<br />
6- Create Wordpress pod and service<br />
<br />
kubectl create -f kloiacom-wordpress.yaml<br />
kubectl create -f kloiacom-wordpress-service.yaml<br />



