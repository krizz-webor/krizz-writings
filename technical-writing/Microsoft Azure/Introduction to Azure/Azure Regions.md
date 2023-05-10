# Azure Regions
This is Part 4 of Azure tutorial. In our previous 2 videos we discussed Azure Datacenters and Geographies. We will discuss

1. Azure Regions
2. Region Pairs
3. Availability Zones
4. Update Domains
5. Fault Domains,
6. Zonal Services
7. Zone-redundant services.

## What is an Azure Datacenter
An Azure data center is a unique physical building that contains thousands of physical servers with it's own power, cooling and networking infrastructure. These data ceneters are located all over the globe. As of November 2020, there are over 160+ Azure datacenters worldwide. It is these dataceneters that are the building blocks of gloabl Azure infrastructure.

## What is an Azure Geography
An Azure geography is an area of the world that contains one or more Azure Regions. For example, India, United States, United Kingdom are a few examples of Azure Geographies.

## Why are azure geographies important
For two reasons. First, let's say all of your customers are in India. You don't want to host your application somewhere in the United States. You don't want every request and the associated data travelling around the world. This causes unnecessary latency, delay and hence, poor performance. You want your application and data to be hosted as geographically close to your customer base as possible. Since all our customers are in India, we want to make sure, our application and data is hosted in India. One way Azure ensures this is by using geographies.

Another reason is compliance with regulations. regulated data like financial, health care or credit card data may not be allowed to leave the country. Legally your organisation may be required to store such data in the same country where the operations are being carried out. Again, azure ensures this, by using geographies.
So, for example, if you select India as the geography, Azure ensures your data is always stored in India, except for certain global services.
## What is an Azure Region
Simply put, an Azure Region is a set of Datacenters that are connected through a dedicated low-latency network. How many datacenters does a region contain. Well, we do not have a fixed number. It varies. There are regions of different sizes. A Region could be made up of just 1 dataceneter or multiple datacenters. The point is, an Azure Region is a group of one or more Azure Datacenters. As of this course recording, Azure has 58 regions worldwide.

You have the flexibility to deploy your applications and data to any Azure region you want. You can even deploy across multiple regions to deliver cross-region resiliency.

## What is cross-region resiliency
Well, in general, resilience is the ability of a software to react to problems in one of its components and still provide the best possible service.
Both your software and the underlying infrastructure must be resilient. If there is a problem, the end user should not know about it. The request must be handled and processed by another region. The end user should get the same level of service.

We can get this resiliency, by deploying our application and data in at least 2 regions.

In this example we have our application and data deployed in two regions - Region A and Region B. If there is a region level failure, for example, let's say Region A has gone down. The Azure Traffic Manager is smart enough to send all the requests to Region B. The end user gets the same response. He does not even know there is a region level failure. When Region A is back online, the Azure Traffic Manager will distribute the traffic between both the regions again.
## Why are Azure Regions important
Well, beacuse everytime we create an Azure resource like a Virtual Machine for example, we need to specify the Azure Region where we want this resource to be created. 
## What is an Azure Availability Zone
An Azure Availability Zone is a unique physical location within an Azure region. Each Availability Zone is made up of one or more datacenters with independent power, cooling, and networking. Not all Regions have Availability Zones. Regions that support Availability Zones have a minimum of three separate zones to ensure resiliency.
If one of the Availability Zones has gone down for some reason, we still have our applications and data available from the rest of the two Availability Zones. There is a physical separation between each Availability Zone and it is this separation that protects our applications and data from Datacenter failures. With Availability Zones, Azure offers industry best 99.99% VM uptime SLA.

