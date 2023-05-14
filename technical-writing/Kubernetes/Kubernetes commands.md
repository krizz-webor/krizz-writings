## Kubernetes Commands
### Listing and getting resources
The kubectl get command allows you to get information about one or many Kubernetes resources, such as pods, namespaces, and deployments. It offers several useful flags such as -o or -output for customizing output format and -w or --watch to watch updates for a particular object.

**lists information about one or more resources.**

    kubectl get

**Gets a list of all the pods in the current namespace**

    kubectl get pods

Gets the pods in the specified namespace

    kubectl get pods --namespace=<namespace>
    
    e.g.,
    kubectl get pods --namespace=kube-system

**Generates a detailed list of all pods in the current namespace with information such as node name, status, age and IP**

    kubectl get pods -o wide

**Gets the YAML representation of a pod**

    kubectl get pod my-pod -o yaml

**Generates a list of all namespaces**

    kubectl get namespaces
    or
    kubectl get ns

### Permanently save the namespace for all subsequent kubectl commands in that context.

**Set current context to a namespace**

    kubectl config set-context --current --namespace=ggckad-s2

**lists all deployments**

    kubectl get deployment
    
    kubectl get deploy

**Lists a specified deployment**

    kubectl get deployment <deployment-name>
    
    e.g.,
    kubectl get deployment nginx-deploy

**Lists all services in the namespace**

    kubectl get services

### Creating resources
Kubectl uses imperative and declarative commands `kubectl create` is an imperative command.

This type of command tells Kubernetes what action you want to perform on an object, e.g., `kubectl create pod`. With the `kubectl create` command, you can create resources such as deployments, services and namespaces, and components from the command line.

**creates new resources from files or standard input devices**

    kubectl create

**creates a new namespace with the specified new-namespace name**

    kubectl create namespace <namespace-name>
    
    e.g., 
    kubectl create namespace new-namespace

**creates a deployment called nginx-deploy that runs on the image nginx**

    kubectl create deploy <deploy-name> --image=<image-name>
    
    e.g., 
    kubectl create deployment nginx-deploy --image=nginx

**creates a deployment called nginx-deploy that runs on image nginx with four replicas and exposes port number 3000**

    kubectl create deploy <deploy-name> --image=<image-name> --replicas=<no-of-replicas> --port=<port-number> 
    
    e.g., 
    kubectl create deployment nginx-deploy --image=nginx --replicas=4 --port=3000

### Viewing the current state of resources
The `kubectl describe` command displays detailed information about the state of a specific resource or a group of resources, which includes uninitialized resources by default.

**shows the details for all nodes**

    kubectl describe nodes

**shows the details for a specific deployment**

    kubectl describe deployment-name

**displays details about a service defined in the `service.yaml` file**

    kubectl describe -f service.yaml

**shows the details of the pods in a namespace**

    kubectl describe pods -n namespace

### Viewing logs
It's often helpful to pull logs from misbehaving pods. You can do this using the `kubectl logs` command.