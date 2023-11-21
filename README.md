# kubernetes-wordpress
Repository to deploy a wordpress instance to local Kubernetes cluster

# Installation

## Create namespace
```
kubectl apply -f wordpress-namespace.yaml
```

## Create secret for MySQL
```
kubectl create secret generic mysql-pass --from-literal=password=welcome1 -n wordpress
```

## Deploy MySQL
```
kubectl apply -f mysql-deployment.yaml
```

MySQL deployment will fail because of storage permissions. Connect to NFS server and run the following:
```
sudo chown 999:999 /volume2/k8s/wordpress-mysql-pv-claim-pvc*
```

# Deploy Wordpress
```
kubectl apply -f wordpress-deployment.yaml
```