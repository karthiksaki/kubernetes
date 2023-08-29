
systemctl enable prometheus
systemctl status prometheus

kubectl get pods --> to know the list of running pods
kubectl run nginx --image=nginx --> to create a pod with the name nginx
kubectl describe pod "pod-name" --> to find the full details of the pod
kubetl delete pod "pod-name" --> to delete pod

kubectl run redis --image=redis123 --dry-run=client -o yaml > redis-definition.yaml --> to create a yaml file

kubectl edit pod redis --> to edit the file
kubectl get pods -o wide --> to display better output for the created pods

kubectl get replicasets

kubectl scale rs new-replica-set --replicas=5 --> to scale replicasets

Create an NGINX Pod::

kubectl run nginx --image=nginx


Generate POD Manifest YAML file (-o yaml). Don't create it(--dry-run)::

kubectl run nginx --image=nginx --dry-run=client -o yaml

Create a deployment::

kubectl create deployment --image=nginx nginx

Generate Deployment YAML file (-o yaml). Don't create it(--dry-run)::

kubectl create deployment --image=nginx nginx --dry-run=client -o yaml


Generate Deployment YAML file (-o yaml). Don’t create it(–dry-run) and save it to a file.::

kubectl create deployment --image=nginx nginx --dry-run=client -o yaml > nginx-deployment.yaml


Make necessary changes to the file (for example, adding more replicas) and then create the deployment ::

kubectl create -f nginx-deployment.yaml

In k8s version 1.19+, we can specify the --replicas option to create a deployment with 4 replicas::

kubectl create deployment --image=nginx nginx --replicas=4 --dry-run=client -o yaml > nginx-deployment.yaml
