# kubernetes
Kubernetes is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. It abstracts away many complexities of managing containers and provides tools for maintaining the desired state of your applications. 

# What Kubernetes can do:: 
![Diagram-52-1536x1203](https://github.com/karthiksaki/kubernetes/assets/124011389/f7377c84-1939-4c1b-bbfb-dad0746042a4)


# Architecture Diagram:: 
![Diagram-55-1536x1288](https://github.com/karthiksaki/kubernetes/assets/124011389/4081f925-7a39-4835-ad18-7465f44bd138)

**Master Node:**
        The control plane of Kubernetes is managed by the master node. It contains several components that make global decisions about the cluster, as well as manage its overall state.

1) **API Server:** This is the entry point for your requests, acting like an interface where you interact with Kubernetes. Using the Kubernetes API, you communicate your intentions, such as launching or scaling containers.

2) **Controller Manager:** Consider this the operations overseer. It maintains the desired state of your applications by running various control loops. If something goes off track, the controller manager adjusts it.

3) **Scheduler:** Visualize this as a manager allocating tasks to team members. It evaluates available resources and requirements, then intelligently assigns containers to suitable worker nodes, ensuring balanced workloads.

4) **etcd:** Think of this as the memory bank of Kubernetes. It's a distributed key-value store where critical data, configurations, and the real-time state of the cluster are stored. All nodes read from and write to etcd to stay coordinated.


**Node:**
These are worker machines where containers are deployed and managed. Each node runs several components:

i) **Kubelet:** Responsible for communicating with the master node and ensuring that containers are running in a Pod (a basic deployment unit in Kubernetes).

ii) **Container Runtime:** The software responsible for running containers, such as Docker or containerd.

iii) **Kube Proxy:** Maintains network rules on each node, enabling network communication between Pods and services.
 **Kube-Proxy works by maintaining a set of network rules on each node in the cluster, which are updated dynamically as services are added or removed. When a client sends a request to service the request is intercepted by kube-proxy on the node where it was received. Kuber proxy then looks up the destination endpoint for the service and routes the request accordingly. Kube-proxy is an essential component of a Kubernetes cluster as it ensures that services can communicate with each other**

**Pod:**
        The smallest deployable unit in Kubernetes. A Pod can contain one or more containers that share the same network and storage. Containers within the same Pod can communicate with each other using localhost.

**Service:**
        An abstraction that defines a logical set of Pods and a policy by which to access them. Services provide a stable IP address and DNS name for accessing Pods, even as Pods are created or terminated

**ReplicaSet:**
        Ensures a specified number of replica Pods are running at all times. It's a higher-level abstraction that allows you to scale your application horizontally.

**Deployment:**
        Provides declarative updates to applications. It manages ReplicaSets and allows you to define the desired state, making it easy to update and roll back application versions.

**Namespace:**
        A virtual cluster inside the physical cluster is used to divide resources between multiple users or projects. It provides a way to isolate resources and prevent naming conflicts.

**ConfigMap and Secret**:
        These are used to manage configuration data and sensitive information (like passwords and tokens) separately from the application code.

**Volume:**
        An abstraction that provides durable storage to Pods, even if the Pod is rescheduled to a different node.
        
**The benefits of Kubernetes are:**



Scalability
High availability
Portability
Security

![Diagram-54-1536x1204](https://github.com/karthiksaki/kubernetes/assets/124011389/13fe6327-89b4-4608-835f-5cc53d299d0a)


**KUBECTL CHEAT SHEET**

[https://kubernetes.io/docs/reference/kubectl/cheatsheet/]

**Kubernetes — Service Types**
There are four types of Kubernetes services — ClusterIP, NodePort, LoadBalancer and ExternalName. The type property in the Service's spec determines how the service is exposed to the network
**1. ClusterIP**
ClusterIP is the default and most common service type.
Kubernetes will assign a cluster-internal IP address to ClusterIP service. This makes the service only reachable within the cluster.
You cannot make requests to service (pods) from outside the cluster.
You can optionally set cluster IP in the service definition file.
**Use Cases**
Inter service communication within the cluster. For example, communication between the front-end and back-end components of your app.

**example**

apiVersion: v1
kind: Service
metadata:
  name: my-backend-service
spec:
  type: ClusterIP # Optional field (default)
  clusterIP: 10.10.0.1 # within service cluster ip range
  ports:
  - name: http
    protocol: TCP
    port: 80

**Kubernetes NodePort service**
NodePorts are open ports on every cluster node. Kubernetes will route traffic that comes into a NodePort to the service, even if the service is not running on that node. NodePort is intended as a foundation for other higher-level methods of ingress such as load balancers and are useful in development.

**Kubernetes Load Balancer service**
For clusters running on public cloud providers like AWS or Azure, creating a load LoadBalancer service provides an equivalent to a clusterIP service, extending it to an external load balancer that is specific to the cloud provider. Kubernetes will automatically create the load balancer, provide firewall rules if needed, and populate the service with the external IP address assigned by the cloud provider.

**How do Kubernetes services work?**
Services simply point to pods using labels. Since services are not node-specific, a service can point to a pod regardless of where it runs in the cluster at any given moment in time. By exposing a service IP address as well as a DNS service name, the application can be reached by either method as long as the service exists.

