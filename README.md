# My config files to deploy Portainer on Kubernetes

Follow the steps below to create a Persistent Volume, a Storage Class file and deploy a Portainer Community Edition. The config files are in the root of this directory ordered by name.

Read all config files to understand what are will configured. Use this files at your own risk.

## Creating the Persistent Volume
```
kubectl create -f 01-pv.yaml
```
## Creating the Storage
```
kubectl create -f 02-storage.yaml
```
## Definnig the created storage as default of Kubernetes
```
kubectl patch storageclass local-storage -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"true"}}}'
```
## Deploy Portainer
```
kubectl create -f 03-portainer.yaml
```
## Verify if the deploy was finished
```
kubectl get pods -n portainer -o wide
```
## Accessing the Portainer
When the pod is on running status the access of the web interface of the Portainer are on `http://ip-host:30777/`
