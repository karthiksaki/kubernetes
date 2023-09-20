## command to list all the running pods
kubectl get pods
## command to create pod with the image name 
kubectl run nginx --image=nginx 
## describe pod
kubectl describe pod "pod-name" 
## to delete pod
kubetl delete pod "pod-name" --> to delete pod
## command to create a yaml file for the creation of pod
kubectl run redis --image=redis123 --dry-run=client -o yaml > redis-definition.yaml 
## command to edit the pod
kubectl edit pod redis --> to edit the file
##  to display better output for the created pods
kubectl get pods -o wide 
## to display replicasets
kubectl get replicasets
## to scale replicasets
kubectl scale rs new-replica-set --replicas=5 
## Create an NGINX Pod::
kubectl run nginx --image=nginx
## Generate POD Manifest YAML file (-o yaml). Don't create it(--dry-run)::
kubectl run nginx --image=nginx --dry-run=client -o yaml
## Create a deployment::
kubectl create deployment --image=nginx nginx
## Generate Deployment YAML file (-o yaml). Don't create it(--dry-run)::
kubectl create deployment --image=nginx nginx --dry-run=client -o yaml
## Generate Deployment YAML file (-o yaml). Don’t create it(–dry-run) and save it to a file.::
kubectl create deployment --image=nginx nginx --dry-run=client -o yaml > nginx-deployment.yaml
## Make necessary changes to the file (for example, adding more replicas) and then create the deployment ::
kubectl create -f nginx-deployment.yaml
## In k8s version 1.19+, we can specify the --replicas option to create a deployment with 4 replicas::
kubectl create deployment --image=nginx nginx --replicas=4 --dry-run=client -o yaml > nginx-deployment.yaml

# command to find a particualr pod from all the namespaces
kubectl get pods --all-namespaces | less 

# setting up the port number 
kubectl expose deployment nginx --port 80

## setting up the image
kubectl set image deployment nginx nginx=nginx:1.18

## Generate POD Manifest YAML file (-o yaml). Don't create it(--dry-run)

kubectl run nginx --image=nginx --dry-run=client -o yaml

## Generate Deployment YAML file (-o yaml). Don't create it(--dry-run)

kubectl create deployment --image=nginx nginx --dry-run=client -o yaml

# Generate Deployment with 4 Replicas

kubectl create deployment nginx --image=nginx --replicas=4

# Service
# Create a Service named redis-service of type ClusterIP to expose pod redis on port 6379

kubectl expose pod redis --port=6379 --name redis-service --dry-run=client -o yaml

## Create a Service named nginx of type NodePort to expose pod nginx's port 80 on port 30080 on the nodes:
kubectl create service {"service_type} nginx --tcp=80:80 --node-port=30080 --dry-run=client -o yaml

kubectl create deployment {"name"} --image={"name"} --replicas=3 --dry-run=client -o yaml > nginx-deployment.yaml

## Create a pod called httpd using the image httpd:alpine in the default namespace. Next, create a service of type ClusterIP by the same name (httpd). The target port for the service should be 80.
kubectl run httpd --image=httpd:alpine --port=80 --expose

## command to display the default status of the kube-system
kubectl get pods --namespace kube-system


## Create a taint on node01 with key of spray, value of mortein and effect of NoSchedule
kubectl taint nodes node01  spray=mortein:NoSchedule

## command to remove the taint on controlplane, which currently has the taint effect of NoSchedule.
kubectl taint nodes controlplane node-role.kubernetes.io/control-plane:NoSchedule-

## To check if a node is assigned with any Taint
kubectl describe node kubemaster | grep Taint

## command to check the list of nodes and their respective nodes
kubectl get pods --all-namespaces -o wide

## example for taints and tolerants
---
appiversion: v1
kind: Pod
metadata:
  name: bee
spec:
  containers:
  - image: nginx
    name: bee
  tolerations:
  - key: spray
    value: mortein
    effect: NoSchedule
    operator: Equal

## NodeSelectores -How to label the nodes 
kubectl label nodes {node-name} {label-key}={label-value}\
# example if a node name is karthik :
kubectl label nodes karthik size=Medium 
# Nodeaffenity 

## sample link
https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands
