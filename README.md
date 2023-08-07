# kubernetes
Kubernetes is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. It abstracts away many complexities of managing containers and provides tools for maintaining the desired state of your applications.


**Master Node:**
        The control plane of Kubernetes is managed by the master node. It contains several components that make global decisions about the cluster, as well as manage its overall state.

![Diagram-55-1536x1288](https://github.com/karthiksaki/kubernetes/assets/124011389/4081f925-7a39-4835-ad18-7465f44bd138)



1) **API Server:** This is the entry point for your requests, acting like an interface where you interact with Kubernetes. Using the Kubernetes API, you communicate your intentions, such as launching or scaling containers.

2) **Controller Manager:** Consider this the operations overseer. It maintains the desired state of your applications by running various control loops. If something goes off track, the controller manager adjusts it.

3) **Scheduler:** Visualize this as a manager allocating tasks to team members. It evaluates available resources and requirements, then intelligently assigns containers to suitable worker nodes, ensuring balanced workloads.

4) **etcd:** Think of this as the memory bank of Kubernetes. It's a distributed key-value store where critical data, configurations, and the real-time state of the cluster are stored. All nodes read from and write to etcd to stay coordinated.


**Node:**
These are worker machines where containers are deployed and managed. Each node runs several components:

i) **Kubelet:** Responsible for communicating with the master node and ensuring that containers are running in a Pod (a basic deployment unit in Kubernetes).

ii) **Container Runtime:** The software responsible for running containers, such as Docker or containerd.

iii) **Kube Proxy:** Maintains network rules on each node, enabling network communication between Pods and services.

**Pod:**
        The smallest deployable unit in Kubernetes. A Pod can contain one or more containers that share the same network and storage. Containers within the same Pod can communicate with each other using localhost.

**Service:**
        An abstraction that defines a logical set of Pods and a policy by which to access them. Services provide a stable IP address and DNS name for accessing Pods, even as Pods are created or terminated

**ReplicaSet:**
        Ensures a specified number of replica Pods are running at all times. It's a higher-level abstraction that allows you to scale your application horizontally.

**Deployment:**
        Provides declarative updates to applications. It manages ReplicaSets and allows you to define the desired state, making it easy to update and roll back application versions.

**Namespace:**
        A virtual cluster inside the physical cluster, is used to divide resources between multiple users or projects. It provides a way to isolate resources and prevent naming conflicts.

**ConfigMap and Secret**:
        These are used to manage configuration data and sensitive information (like passwords and tokens) separately from the application code.

**Volume:**
        An abstraction that provides durable storage to Pods, even if the Pod is rescheduled to a different node.


**The benefits of Kubernetes are:**

Scalability
High availability
Portability
Security
