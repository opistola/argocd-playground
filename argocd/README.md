# Argocd notes

This project was intended to start playing with Argocd on my minikube cluster.

## Start minikube

```
minikube start
```

Check argocd namespace

```
kubectl get ns
```

if argocd is there skip next step

## Install argocd

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/core-install.yaml
```

## Login

### Get admin password

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

### WEB UI

First port forward the web UI

```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

### argocd cli

```
argocd login localhost:8080
```

##
