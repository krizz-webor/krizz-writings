## Virtual Networks
* An Azure Virtual Network (VNet) is a network or environment that can be used to run VMs and applications in the cloud.
* The Azure Virtual Network is a logical representation of the network in the cloud. So, by creating an Azure Virtual Network, we can define our private IP address range on Azure, and also deploy different kinds of Azure resources. For Example - Azure virtual machine, App service environment, Integration service environment, etc.

When it is created, the services and Virtual Machines within the Azure network interact securely with each other.

### Advantages of Using Azure Virtual Network
Some of the major advantages of using Microsoft Azure VNet are as follows:

1. It provides an isolated environment for your applications
2. A subnet in a VNet can access the public internet by default
3. We can easily direct traffic from resources
4. It is a highly secure network
5. It has high network connectivity
6. It builds sophisticated network topologies in a simple manner.

### Azure Vnet Capabilities
Following are the capabilities of the Azure Vnet:

* **Isolation and segmentation**: To deploy resources such as virtual machines into virtual networks, they will be isolated from other resources. By putting the virtual machine into your virtual network, it cannot be reached from the Internet or other Azure resources unless we enable communication in between. We can also use subnets within virtual networks to further segment our resources within the network.

* **Communication with the Internet**: All resources in a virtual network can communicate outbound to the Internet by default. But it needs to establish an inbound connection from the Internet. We can either use public IP or load balancers.
* **Communication between resources**: Communication between the number of resources inside the virtual network or with other resources through service endpoints.

* **Communication with on-premises resources**: 
* **Point-to-site virtual private network**: This method connects a virtual network and a single computer in your network with each computer configuring its own connection. You need not make fundamental changes to your existing network for this connectivity.
* **Site-to-site VPN**: This type of connection works between an on-premises VPN device and an Azure VPN Gateway in the context of a virtual network. Any resource you authorize can communicate within the specified virtual network.
* **Azure ExpressRoute**: This connection method enables the communication between your network and Azure through an ExpressRoute partner.

The first two connectivity methods work by creating an encrypted tunnel to communicate over the Internet while Azure ExpressRoute creates a private connection. 

By establishing either point to site VPN(Virtual Private Network - a service that helps you stay private online. A VPN establishes a secure, encrypted connection between your computer and the internet, providing a private tunnel for your data and communications while you use public networks.) or site to site VPN or Express route, your workloads within Azure virtual network can seamlessly communicate with workloads within our on-premises(On-premises is the software and technology that is located within the physical confines of an enterprise often in the company’s data center as opposed to running remotely on hosted servers or in the cloud) data center.

There are lots of capabilities within the Azure virtual network that we can use to control the traffic.

* **Filter network traffic**: We can use Network Security Groups, Application Security Group, Azure firewall, or third-party network virtual appliance to filter the traffic coming to the resources in the virtual network.

* **Route network traffic**: We can route the network traffic using the routing tables, we can configure user-defined routes to route all the outbound traffic, let's say via a firewall.

* **Monitor network traffic**: By network security groups and traffic analytics monitoring solution, you'll be able to carry out extensive monitoring on both inbound and outbound communications.

### Components of Azure VNet
Azure networking components provide a wide range of functionalities that can help companies build efficient cloud applications that meet their requirements.

Subnets
Routing
Network Security Groups

**Subnet** plays a vital role because many configurations will be done at a subnet level. It is a range of IP addresses in the VNet. Vnet can be divided into multiple subnets based on different design considerations, for example - we can deploy a virtual machine, App services environment, integration service environment, etc. VMs & PaaS services deployed to subnets n the same VNet and can communicate with each other without any extra configuration. Route tables, NSG, Service endpoints, and policies are configured to the subnets.

Subnets let users segment the virtual network into one or more sub-networks.
These sub-networks can be separated logically, and each subnet consists of a server.
We can further divide a subnet into two types:
Private
Public
* **Private** - Instances can access the Internet with NAT (Network Address Translation) gateway that is present in the public subnet.
* **Public** - Instances can directly access the internet.

**Routing** It delivers the data by choosing a suitable path from source to destination.
For each subnet, the virtual network automatically routes traffic and creates a routing table.

**Network Security Groups** It is a firewall that protects the virtual machine by limiting network traffic.
It restricts inbound and outbound network traffic depending upon the destination IP addresses, port, and protocol.


A **NAT gateway** is a Network Address Translation (NAT) service. You can use a NAT gateway so that instances in a private subnet can connect to services outside your VPC but external services cannot initiate a connection with those instances.



.