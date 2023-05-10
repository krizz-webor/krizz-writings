# Azure Active Directory
## What is Active Directory
Active Directory (AD): Is used to store and organize information about various elements of an organizations network such as computers, users, resources like printers, shared files or folders.
## Azure Active Directory(Azure AD)
Is the identity management solution for azure. It is a live directory or database that stores users accounts and their passwords, computers, files shares, security groups, permissions and so much more. It also provides a single sign-on, which means that the user just need only one username and password to be able to access different services that he has been given permissions to.
Before Microsoft provided azure active directory, he already provided an on premise active directory service which was known as windows active directory.
but windows active directory was not actually designed to handle web based services or information related to web based services. So that was one major draw back which made Microsoft to come up with another active directory which is called Azure Active Directory.
## Windows Active Directory
Is a windows OS directory service that offers a single interface for organizing and maintaining information about the organization's network.
## Difference between Windows and Azure AD
#### Provisioning Users
* For Windows, Organizations create internal users manually or use an in-house or automated provisioning system, like the Microsoft Identity Manager, to integrate with an HR system.
* For Azure AD, Existing AD organizations use Azure AD Connect to sync identities to the cloud.
It adds support to automatically create users from cloud HR systems and provision identities in SCIM-enabled SaaS apps to automatically provide apps with the necessary details to allow access for users.
#### Admin Management (AKS)
* For Windows, Organizations will use a combination of domains, organizational units, and groups in AD to delegate administrative rights to manage the directory monitored resources.
* For Azure AD, Azure AD provides built-in roles with its Azure AD RBAC system, with limited support for creating custom roles to delegate privileged access to the identity system, the apps, and the resources it controls.
#### Infrastructure Apps
* For Windows, Active Directory forms the basis for many infrastructure on-premises components, like DNS, DHCP, IPSec, WiFi, NPS, and VPN access.
* For Azure AD, In a new cloud world, Azure AD is the new control plane for accessing apps and relying on networking controls. When users authenticate, Conditional access (CA) controls which users have access to which apps under required conditions.
#### Mobile
* For Widows, Active Directory doesn’t natively support mobile devices without third-party solutions.
* For Azure AD, Microsoft Intune (mobile device management solution) is integrated with Azure AD. It provides device state information to the identity system to evaluate during authentication.
## Service Audience
1. IT Administrator
2. Application Developers
3. Online Customers

**IT Administrators**: These are responsible for all the sign-ins and sign-ups. They provide relevant authentication and permissions to customers and users. They also resolve authentication issues.

**Application Developers**: They are the ones who want to use the services for which they have been given the permission. So with Azure AD, the application developers only have to remember just one set of password and username to access any service that they want to use for the application development purpose, provided that they were granted the permission to use such services by the IT Administrator.

**Online Customers**: These can access services such as office 365, and other CRM services offered by azure with their azure active directory credentials.
### Terminologies in Azure AD
* **Tenant**: A Tenant refers to a single dedicated and trusted instance of Azure Active Directory and it gets created automatically when you sign up for a Microsoft cloud service subscription. In broader terms, when your organization signs up for cloud service subscription. A tenant, therefore, represents a single organization, identity, or a person.Although when an organization or an individual signs up for the first time, only a single tenant is created and associated, but multiple tenants can be created after signing up and, therefore, an organization can have more than one tenant, depending upon organizational requirement. Each tenant has its own Azure Active Directory, thereby having a one-to-one relation between the tenant and the Azure AD, where each tenant is referred to as an organization. In a single tenant, resources within the tenant have access to other services and resources within that tenant, whereas, when the resources within a tenant have access to other resources and services in a shared environment across multiple organizations (i.e., multiple tenant), they are considered as multi-tenant. A Tenant can have one or more subscriptions. This is the case in large organization, where there are different departments and each department has their own subscription, whereas, a Subscription can only be associated with a single Azure AD Tenant at any time.
* **Domain**: A domain is a DNS zone for which the tenant has proven ownership which means that its the public domain of the organization which means that no one else can use that particular domain. When you create an azure active directory, you get a default domain with you azure active directory which is in the format of .onmicrosoft.com. The prefix of this domain depends on the name of the azure active directory. Which means that the organization gets to decide what will be the prefix of this domain.
* **Users**: these are the individuals that have been given permissions and sets of username and password to access and use certain services.

**Types of users**
1. **New user**: User are given road so that they can access your azure services, but within some specified permissions and access control. When you create a new user, it displays on the user display as a member. Which indicate that such user is part of the company or organization.
2. **New guest user**: This is often used when your organization wants to collaborate with some external partners. So that they can give them access to some of the resources. When you create a new guest user, it displays on the user display as guest. Which indicates that such person is not an integral part of the company but a partner or customer.
* **Groups**: This is a logical collection of users. Groups are created to organize users or devices on the basis of geographical location, departments, types of services or hardware characteristics.

**Group types**
1. **Security**: A Security Group will be used to collectively assign resources to users. By using a Security Group, we assign the resource to the Group once and adjust the Group members to reflect who has access to the resource.
2. **Office 365**: An Office 365 Group will give any group member access to a Group email address (specified during creation) and SharePoint Site and is best suited for when collaboration is required between both internal and/or external users. 

**Membership type**
1. **Assigned**: An Assigned Group Membership Type indicates that members (users/devices) are manually added or removed from the Group.
2. **Dynamic User**: Dynamic users, the members are added when they meet the rules which are configured. Dynamic User allows you to dynamically add or remove users to the Group based on one or many of their account attributes. Once the Membership rules are defined, Users are added/removed dynamically.
3. **Dynamic device**: It allows you to dynamically add or remove Devices to the Group based on one or many of the Device attributes. Once the Membership rules are defined, Devices are added/removed dynamically. The only difference is that it automatically removes device only instead of users. A Dynamic Device Membership Type is not available for Office 365 Group Types.