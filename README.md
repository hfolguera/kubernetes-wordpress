# kubernetes-wordpress
Repository to deploy a wordpress instance to local Kubernetes cluster

# Requirements
In order to deploy a Wordpress instance, a MySQL database is needed. Follow instructions at [https://github.com/hfolguera/kubernetes-mysql] to deploy a MySQL database.

# Installation

## Create namespace
```
kubectl apply -f wordpress-namespace.yaml
```

## Create secret for MySQL
```
kubectl create secret generic mysql-pass --from-literal=password=welcome1 -n wordpress
```

# Deploy Wordpress
```
kubectl apply -f wordpress-deployment.yaml
```

# GitOps
You can also deploy a Wordpress instance through an ArgoCD application.
Use the example in: https://github.com/hfolguera/kubernetes-argocd/blob/main/applications/wordpress-application.yaml

Clone or download the repo, update and deploy it:
```
wget https://raw.githubusercontent.com/hfolguera/kubernetes-argocd/main/applications/wordpress-application.yaml
vim wordpress-application.yaml
kubectl apply -f wordpress-application.yaml
```