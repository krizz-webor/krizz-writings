# Elastic load balancer
Do you want to implement the automatic distribution of your incoming web traffic across Amazon EC2 instances on the Amazon AWS cloud? If yes, then the Amazon Elastic Load Balancing (ELB) service is your answer. Be it incoming website or application traffic, ELB can automatically distribute this traffic across many targets. These targets include Amazon EC2 instances along with containers and IP addresses.

Additionally, AWS ELB can handle your varying traffic across single – or multiple – availability zones. So, even as your application traffic scales or changes over time, ELB can automatically scale its capability according to the workloads.

## How does Amazon ELB Work

Traditionally, load balancing worked by dividing the incoming traffic or users equally among multiple computers so that every user request is processed faster. In the case of ELB, the load balancer first checks the health of the targeted instances and routes the traffic only to healthy targets. Additionally, it stops directing traffic towards an unhealthy instance.

You can also configure your elastic load balancer to accept incoming traffic by selecting one or more listeners. Configured with a port number and network protocol, a listener checks for connection requests from clients to the load balancer.

## General features
* Accepts incoming traffic from clients and routes requests to its registered targets.
* Monitors the health of its registered targets and routes traffic only to healthy targets.
* Enable deletion protection to prevent your load balancer from being deleted accidentally. Disabled by default.
* Deleting ELB won’t delete the instances registered to it.

## Types of AWS Elastic Load Balancers
### Application Load Balancer:

This type of Load Balancer is used when there are HTTP and HTTPS traffic routing. I’m sure you guys are aware of the OSI Model. This load balancer works at the Application layer of the OSI Model. It provides advanced routing features such as host-based and path-based routing. It also works well with containers and microservices.
This load balancer is best designed for load balancing of HTTP/ HTTPS traffic and can route the incoming traffic towards the latest application architectures that include IP addresses, containers, EC2 servers, and Lambda functions.

Functions at the application layer, the seventh layer of the Open Systems Interconnection (OSI) model.
Allows HTTP and HTTPS.
At least 2 subnets must be specified when creating this type of load balancer.

**Components**:
* A load balancer serves as the single point of contact for clients.
* A listener checks for connection requests from clients. You must define a default rule for each listener that specifies a target group, condition, and priority.
* Target group routes requests to one or more registered targets. You can register a target with multiple target groups, and configure health checks on a per target group basis.

**Benefits**:
* Support for path-based and host-based routing.
* Support for routing requests to multiple applications on a single EC2 instance.
* Support for registering targets by IP address, including targets outside the VPC for the load balancer.
* Support for containerized applications.
* Support for monitoring the health of each service independently.
* Support for redirecting requests from one URL to another.
* Support for returning a custom HTTP response.

### Network load balancer
This load balancer is best designed for load balancing of traffic that uses protocols like TCP, User Datagram Protocol (or UDP), and Transport Security Layer (or TSL), which require good performance.

This load balancer can handle millions of user requests each second between the client device and the target instance.

The network load balancer is optimized to work with volatile and dynamic workloads and for handling a sudden increase in incoming traffic.

### Classic load balancer
This load balancer is best designed for basic load balancing that operates across multiple EC2 instances at both request and the connection level. The classic load balancer retrieves information – such as the network protocol and port number – from the incoming request and routes the traffic to the appropriate EC2 instance that is hosting the web application.

The classic load balancer is similar to traditional forms of load balancing using physical devices, except that this load balancer automatically performs balancing in a virtual environment. This load balancer is optimized to work with applications that were built in the classic EC2 network.
For use with EC2 classic only. Register instances with the load balancer. AWS recommends using Application or Network load balancers instead.

### Gateway Load Balancer
Gateway Load Balancers provides you the facility to deploy, scale, and manage virtual appliances like firewall. Gateway Load Balancers combines a transparent network gateway and then distributes the traffic.

### Features of load balancing
**HTTP**
It is the standard balancing request based on HTTP mechanism. It directs the traffic to the backend information for the original request.

**HTTPS**
It is the same as the HTTP forwarding rule with an additional feature of encryption. Encryption here is handled in one of the two ways: SSL Passthrough (encryption is all the way to backend) and SSL termination (encryption is done by the load balancer). In SSL termination, the traffic is sent to backend unencrypted.

**UDP**
A UDP Load Balancer uses User Datagram protocol which provides low latency for applications.

**TCP**
TCP is used for Load Balancing all the applications that do not use protocols like HTTP and HTTPScing.
