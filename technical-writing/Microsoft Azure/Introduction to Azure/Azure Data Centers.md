# Azure Data Centers

To understand Azure better, we need to understand Azure global infrastrcuture specific terms like 

1. Datacenters
2. Regions
3. Region Pairs
4. Availability Zones and
5. Geographies

## What are Azure Data Centers
When we provision a resource from Azure cloud, like a Virtual Machine or an Azure SQL Database for example.
These resources obviously require a physical server space to be created.

**A datacenter** is simply a building that contains the physical server. Not just one server, many many physical servers which are connected over a network. It also has it's own power, and cooling.

So, in simple terms, an Azure data center is a unique physical building that contains many many physical servers with it's own power, cooling and networking infrastructure. These data ceneters are located all over the globe. As of this course recording, there are over 160+ Azure datacenters worldwide. The exact location of these datacenters is not published by Microsoft for obvious security reasons. It is these dataceneters that are the building blocks of gloabl Azure infrastructure.

## Microsoft Datacenters at the bottom of the ocean
To power and maintain all these dataceneters lot of energy is required. Micrsofot has been actively researching to source clean-energy. As part of this initiative, Microsoft has been experimenting placing Datacenters at the bottom of the ocean. They called this Project Natick. In spring 2018, Microsoft’s Project Natick team deployed a shipping-container-sized datacenter on the sea-floor in Scotland. It stayed underwater, for almost over 2 years. During these 2 years, the underwater datacenter servers are extensively tested and monitored for performance and reliability.

With this experiment, the team concluded that a sealed datacenter on the ocean floor could provide ways to improve the overall reliability of datacenters. On land, corrosion from oxygen and humidity, temperature fluctuations and bumps and jostles from people who replace broken components are all variables that can contribute to equipment failure.

If you want to learn more about Microsoft underwater datacenter, you have more details on their news website - https://news.microsoft.com/innovation-stories/project-natick-underwater-datacenter/

With this experiment, Microsoft finds underwater datacenters are reliable, practical and use energy sustainably. Hopefully we will soon see underwater dataceneters. As of this course recording though, all azure dataceneters are still on Land and it is these dataceneters that are the building blocks of azure global infrastrcuture

An Azure data center is a unique physical building that contains thousands of physical servers with it's own power, cooling and networking infrastructure. These data ceneters are located all over the globe. As of this course recording, there are over 160+ Azure datacenters. These dataceneters are organised into Azure Regions.