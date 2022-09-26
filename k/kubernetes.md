# Kubernetes

Kubernetes takes care of automatic deployment of the containerized applications across different servers (physical or virtual), distribution of the load across those servers, auto-scaling of the deployed applications, and the monitoring and health checks of the containers including automatically replacing the failed containers.

Containerization allows you to create self-contained Linux execution environments. Any program and all its dependencies can be bundled up into a single file and then shared on the internet. Anyone can download the container and deploy it on their infrastructure with very little setup required. Creating a container can be done programmatically, allowing powerful CI and CD pipelines to be formed.

Multiple programs can be added into a single container, but it’s better to have many small containers than one large one as it makes updates easier to deploy and issues easier to find.

#### Architecture of Kubernetes

* _Pod_

The smallest unit in Kubernetes. Containers are created inside the pod, along with shared volumes, and shared network resources eg. shared IP address.

Generally common to have one container per pod, but when some containers heavily depend on each other it’s possible to create several containers in the same pod.

Each pod must be on the same server.

* _Cluster_

Clusters consists of nodes. Each node is a server, either physical or virtual. These servers can be located anywhere, but generally are closer together to perform the jobs more efficiently. Inside of the node there are pods, which are the smallest units in Kubernetes and contain containers. Nodes will not automatically go into clusters - these must be set.

Each node has a Kubelet, which is an agent for managing the node and communicating with the Kubernetes control plane. The node should also have tools for handling container operations, such as Docker. A Kubernetes cluster that handles production traffic should have a minimum of three nodes because if one node goes down, both an etcd member and a control plane instance are lost, and redundancy is compromised. You can mitigate this risk by adding more control plane nodes.

In each Kubernetes cluster there is a master node, or control plane, and other nodes called worker nodes. The master node manages worker nodes, for example distributing work across the nodes. All pods for applications are deployed to worker nodes, master node only deploys system nodes that work for the Kubernetes cluster in general - doesn’t run client applications.

Container runtime runs actual containers inside of each node.

* _Nodes_

A Pod always runs on a Node. A Node is a worker machine in Kubernetes and may be either a virtual or a physical machine, depending on the cluster. Each Node is managed by the control plane. A Node can have multiple pods, and the Kubernetes control plane automatically handles scheduling the pods across the Nodes in the cluster. The control plane's automatic scheduling takes into account the available resources on each Node.

Every Kubernetes Node runs at least:

Kubelet, a process responsible for communication between the Kubernetes control plane and the Node; it manages the Pods and the containers running on a machine. A container runtime (like Docker) responsible for pulling the container image from a registry, unpacking the container, and running the application.

#### Node services&#x20;

* Kubelet - a service in the worker that communicates with the API server in the master node
* Kube-proxy - responsible for network communications inside each node and between nodes

#### Master node services&#x20;

* Scheduler - distributes load between worker nodes&#x20;
* Kube controller manager - controls what happens on each node in the cluster&#x20;
* Cloud controller manager - communicates with cloud service provider where the cluster is deployed&#x20;
* ETCD - service that stores all logs for all cluster operations&#x20;
* DNS service also runs on master node&#x20;
* API server - main service on master node. Manages whole cluster with kubectl which is a CL tool to manage - can connect to the API server on the Master node through HTTPS. Can manage any remote Kubernetes cluster with this.

#### Using Kubectl

To view the nodes in the cluster, run the kubectl get nodes command. This shows all nodes that can be used to host our applications.

Once you have a running Kubernetes cluster, you can deploy your containerized applications on top of it. To do so, you create a Kubernetes Deployment configuration. Do this in kubectl: kubectl create deployment {deployment name} –image={image location} List deployments: Kubectl get deployments

#### Deployments and proxies

Pods that are running inside Kubernetes are running on a private, isolated network. By default they are visible from other pods and services within the same kubernetes cluster, but not outside that network. When we use kubectl, we're interacting through an API endpoint to communicate with our application.

The kubectl command can create a proxy that will forward communications into the cluster-wide, private network. The proxy can be terminated by pressing control-C and won't show any output while its running.

#### Kubectl proxy

We now have a connection between our host (the online terminal) and the Kubernetes cluster. The proxy enables direct access to the API from these terminals.

The API server will automatically create an endpoint for each pod, based on the pod name, that is also accessible through the proxy.

#### Kubernetes Pods

A Pod is a Kubernetes abstraction that represents a group of one or more application containers (such as Docker), and some shared resources for those containers. Those resources include shared volumes, networking (like a unique cluster IP address), and information about how to run each container, such as the container image version or specific ports to use.

Pods are the atomic unit on the Kubernetes platform. When we create a Deployment on Kubernetes, that Deployment creates Pods with containers inside them (as opposed to creating containers directly). Each Pod is tied to the Node where it is scheduled, and remains there until termination (according to restart policy) or deletion. In case of a Node failure, identical Pods are scheduled on other available Nodes in the cluster.

####

#### KUBECTL commands

The most common operations can be done with the following kubectl commands:

kubectl get - list resources kubectl describe - show detailed information about a resource kubectl logs - print the logs from a container in a pod kubectl exec - execute a command on a container in a pod kubectl delete service -l app=kubernetes-bootcamp - delete a service You can use these commands to see when applications were deployed, what their current statuses are, where they are running and what their configurations are.

#### Services

A Kubernetes Service is an abstraction layer which defines a logical set of Pods and enables external traffic exposure, load balancing and service discovery for those Pods. A Service is defined using YAML (preferred) or JSON, like all Kubernetes objects. Services are the abstraction that allows pods to die and replicate in Kubernetes without impacting your application.

Although each Pod has a unique IP address, those IPs are not exposed outside the cluster without a Service. Services allow your applications to receive traffic. Services can be exposed in different ways by specifying a type in the ServiceSpec, see this tutorial and this one for more detail.

Services match a set of Pods using labels and selectors, a grouping primitive that allows logical operation on objects in Kubernetes. Labels are key/value pairs attached to objects and can be used in several ways:

* Designate objects for development, test, and production Embed version tags Classify an object using tags
* Labels are mutable and can be attached to objects at any time.



#### Links

* [Kubernetes cheat sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
* [Kubernetes docs](https://open.spotify.com/track/56Afib9o78iCsB7c5sNOXn?si=45ff0727400e42a2)
