# PluralSight Packaging applications with Helm for Kubernetes
 
Please follow instruction in module : Installing Kubernetes and Helm

Here bellow are the commands to be launched :

## Minikube installation
```
curl -o minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikube
sudo cp minikube /usr/local/bin/minikube
minikube version
minikube start
```
## Helm installation
```
curl -LO https://storage.googleapis.com/kubernetes-helm/helm-v2.14.3-linux-amd64.tar.gz
tar -zxvf helm-v2.14.3-linux-amd64.tar.gz
sudo mv linux-amd64/helm /usr/local/bin/helm

helm version --short
kubectl config view
helm init
helm version --short
kubectl get all --namespace=kube-system -l name=tiller
helm create nginx-demo
helm install nginx-demo
kubectl get all | grep nginx-demo
```
## Helm local tiller
```
curl -LO https://storage.googleapis.com/kubernetes-helm/helm-v2.14.3-linux-amd64.tar.gz 
tar -zxvf helm-v2.14.3-linux-amd64.tar.gz
sudo mv linux-amd64/tiller /usr/local/bin/tiller
tiller

sudo mv linux-amd64/helm /usr/local/bin/helm
helm init --client-only
export HELM_HOME=/home/$(whoami)/.helm
helm version --short
export HELM_HOST=localhost:44134
helm version --short

helm create nginx-localtiller-demo
helm install nginx-localtiller-demo
kubectl get all | grep localtiller
kubectl get pod --namespace=kube-system -l name=tiller
kubectl get configmaps --namespace=kube-system
```
## Helm delete
```
helm list
helm delete calling-horse
kubectl get configmaps --namespace=kube-system
helm delete calling-horse --purge
helm reset
```

