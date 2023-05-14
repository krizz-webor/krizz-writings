## Kubernetes commands 2
**Alias**

    alias k="kubectl"


### Cluster Management
A Kubernetes cluster is a collection of nodes that execute containerized applications. It lets containers run across several machines and environments: cloud-based, virtual, on-premises and physical. Listed below are the kubectl commands can be utilised to manage a cluster.

**Display endpoint information regarding the services and master in the cluster**

    kubectl cluster-info

**Show the Kubernetes version functioning on the client and server**

    kubectl version


**Get the configuration of the cluster**

    kubectl config view

**Make a list of the available API resources**

    kubectl api-resources

**Make a list of the available API versions**

    kubectl api-versions

**List everything**

    kubectl get all –all-namespaces

### Namespaces
Shortcode = ns

**Create namespace <name>**

    kubectl create namespace <namespace_name>

**List one or more namespaces**

    kubectl get namespace <namespace_name>

**Show the detailed condition of one or more namespace**

    kubectl describe namespace <namespace_name>

**Delete a namespace**

    kubectl delete namespace <namespace_name>

**Edit and modify the namespace’s definition**

    kubectl edit namespace <namespace_name>

**Display Resource (CPU/Memory/Storage) usage for a namespace**

    kubectl top namespace <namespace_name>

### Node operations
A Node is a worker machine in Kubernetes and can either be a virtual or a physical machine, which depends on the cluster. Every Node is handled by the control plane. A Node can contain several pods, and the Kubernetes control plane handles scheduling the pods automatically across the Nodes in the cluster. Following commands can be utilised for Node Operations.

**Revise the taints on one or more nodes**

    kubectl taint node <node_name>

**List one or more nodes**

    kubectl get node

**Delete a node or multiple nodes**

    kubectl delete node <node_name>

**Display Resource usage (CPU/Memory/Storage) for nodes**

    kubectl top node

**Resource allocation per node**

    kubectl describe nodes | grep Allocated -A 5

**Pods running on a node**

    kubectl get pods -o wide | grep <node_name>

**Annotate a node**

    kubectl annotate node <node_name>

**Mark a node as unschedulable**

    kubectl cordon node <node_name>

**Mark node as schedulable**

    kubectl uncordon node <node_name>

**Drain a node in preparation for maintenance**

    kubectl drain node <node_name>

**Add the labels of one or more nodes**

    kubectl label node

### Listing Resources 
Kubernets resources also regarded as Kubernetes objects related to a certain namespace, you can either utilise individual kubectl get command to jot down every resource one by one, or you can jot down all the resources in a Kubernetes namespace by executing a single command. Mentioned below are the list of commands to get the resources information.

**Create a plain-text list of all namespaces**

    kubectl get namespaces

**Create a plain-text list of all pods**

    kubectl get pods

**Create a comprehensive plain-text list of all pods**

    kubectl get pods -o wide

**Create a list of all pods functioning on a certain node server**

    kubectl get pods–field-selector=spec. nodeName=[server-name]

In plain text, make a lst a specific replication controller

    kubectl get replicationcontroller [replication-controller-name]

**Generate a plain-text list of all replication services and controllers** 

    kubectl get replicationcontroller, services

### Daemonsets 
A Daemonset assures that some or all  Nodes run a copy of a Pod. As nodes are incorporated to the cluster, Pods are implemented to them. As nodes are erased  from the cluster, those Pods are garbage collected. Erasing a DaemonSet will clean up the Pods it created.

**List one or more daemonsets**

    kubectl get daemonset

**Edit and modify the definition of one or more daemonset**

    kubectl edit daemonset <daemonset_name>

**Delete a daemonset**

    kubectl delete daemonset <daemonset_name>

**Create a new daemonset**

    kubectl create daemonset <daemonset_name>

**Manage the rollout of a daemonset**

    kubectl rollout daemonset

**Show the comprehensive state of daemonsets within a namespace**

    kubectl describe ds <daemonset_name> -n <namespace_name>

### Events
Shortcode = ev

Kubernetes events are objects that displays what is happening within a cluster, like what decisions were implemented by the scheduler or why some pods were erased from the node. Events are the first thing to look at for application, along with infrastructure operations when something is not functioning as anticipated. Mentioned below are the kubectl commands to get the events.

**List current events for all resources in the system**

    kubectl get events

**List Warnings only**

    kubectl get events –field-selector type=Warning

**List events but exclude Pod events**

    kubectl get events –field-selector involvedObject.kind!=Pod

**Pull events for a single node with a distinct name**

    kubectl get events –field-selector involvedObject.kind=Node, involvedObject.name=<node_name>

**From a list of events, filter out normal events**

    kubectl get events –field-selector type!=Normal

### Logs
You can use Kubernets logs commands to monitor, log and debug the pods

**Print the logs for a pod**

    kubectl logs <pod_name>

**Print the logs for a pod for the last hour** 

    kubectl logs –since=1h <pod_name>

**Get the current 20 lines of logs**

    kubectl logs –tail=20 <pod_name>

**Get logs from a service and choose which container optionally**

    kubectl logs -f <service_name> [-c <$container>]

**Adhere to new logs and print the logs for a pod**

    kubectl logs -f <pod_name>

**For a container in a pod, Print the logs** 

    kubectl logs -c <container_name> <pod_name>

**Output the logs for a pod into a ‘pod.log’ file** 

    kubectl logs <pod_name> pod.log

**View the logs for the last failed pod**

    kubectl logs –previous <pod_name>

### Deployments
Shortcode = deploy.

A Kubernetes Deployment is utilised to inform Kubernetes how to design or change instances of the pods that hold a containerized application. Deployments can enhance the number of replica pods, enable rollout of revised code in a controlled way, or roll back to an earlier deployment version if required.

**List one or more deployments**

    kubectl get deployment

**Show the in-depth state of one or more deployments**

    kubectl describe deployment <deployment_name>

**Edit and revise the definition of one or more deployment on the server**

    kubectl edit deployment <deployment_name>

**Generate one a new deployment**

    kubectl create deployment <deployment_name>

**Generate one a new deployment with image**

    kubectl create deployment <deployment_name> --image=<image name> 

**Scale deployment and give replicaSets**

    kubectl scale deployment <deployment name> --replicas=5

**Delete deployments**

    kubectl delete deployment <deployment_name>

**Check the rollout status of a deployment**

    kubectl rollout status deployment <deployment_name>

### Replication Controllers
Shortcode = rc

**Make a list of  the replication controllers**

    kubectl get rc

**Make a list of  the replication controllers by namespace**

    kubectl get rc –namespace=”<namespace_name>” 

### ReplicaSets
Shortcode = rs

**List ReplicaSets**

    kubectl get replicasets

**Show the detailed state of one or more ReplicaSets**

    kubectl describe replicasets <replicaset_name>

**Scale a ReplicaSet**

    kubectl scale –replicas=[x]

### Secrets
A Kubernets Secret is an object that comprises minor portion of sensitive data like a token, a key or password.. Such data might otherwise be inserted in an image or in a Pod specification. Users can build Secrets and the system also generates a few Secrets with the help of the following kubectl commands.

**Create a secret**

    kubectl create secret

**List secrets**

    kubectl get secrets

**List details about secrets**

    kubectl describe secrets

**Delete a secret**

    kubectldelete secret <secret_name>

### Services and Service Accounts: 
A Kubernetes service is a logical abstraction for a deployed group of pods in a cluster (which all perform the same function) and Service accounts are used to provide an identity for pods. Pods that want to interact with the API server will authenticate with a particular service account.

**Make a list of  one or more services**

    kubectl get services

**Show the detailed state of a service**

    kubectl describe services

**Reveal a replication controller, service, deployment or pod as a new Kubernetes service**

    kubectl expose deployment [deployment_name]

**Edit and modify the definition of one or more services**

    kubectl edit services

**List service accounts**

    kubectl get serviceaccounts

**Show the in-depth state of one or more service accounts**

    kubectl describe serviceaccounts

**Replace a service account**

    kubectl replace serviceaccount

**Delete a service account**

    kubectl delete serviceaccount <service_account_name>

**To delete all services, deployment and pods**

    kubectl delete all --all