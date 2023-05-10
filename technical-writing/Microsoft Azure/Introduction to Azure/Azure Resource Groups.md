# Azure Resource Groups
Resources are instances of azure services that you create, like virtual machines, app services, storage accounts, SQL databases, function apps etc. All these are azure services. Everytime you create an instance of a service, you are creating a resource. There are hundereds of azure services.
On the left you see the service categories like General, Compute, Networking, Storage etc. For example if you want to create a storage account to store your data, click on the Storage category and you will see all the services related to Storage. 

Anytime you create a resource, you also need to specify a resource group.
## Azure resource groups - Imporantant points to remember
1. An azure resource is any service instance that you create. For example, virtual machine, Azure sql database, storage account etc.
2. A resource group, as the name implies, a group of related azure resources.
3. In general, resources in a resource group share the same life cycle, so they can be easily created, deployed, updated, and deleted as a single unit.
4. When you create a resource group, you specify a region. It is this region where the meta-data about the resource group is stored. 
5. However, the resources themselves can be in any azure region. 
6. Resources in one resource group can interact with resources in other resource groups.
7. Each resource must be in one and only one resource group. You cannot have a resource in more than 1 resource group at the sametime.
8. You can move a resource from one resource group to another.
9. You can add or remove a resource from a resource group at any time.
10. You can group resources any way you want. Anyway that makes sense to your oragnisation really - By department, By country, By application, By resource type or a combination of these.

## Benefits of Azure Resource Groups
### Administration is much easier
When we create a virtual machine in azure several other associated resources like the following are created.

1. a data disk for the virtual machine
2. Public IP address
3. Network interface
4. Network security group
5. Virtual network

Without these resources, an azure virtual machine doesn't work as expected. After you are done with the VM, you may want to delete it to save on cost. However, when you delete the VM the associated resources are not automatically deleted. You have to delete them manually. If you forget to delete 1 or more associated resources, you are unnecessarily paying for those resources that you are not actually using.

On the other hand, if you create a virtual machine in a resource group, all the other associated resources are also created in the same resource group. When we delete the resource group, not just the virtual machine, all it's associated resources are also automatically deleted.

Another example. Let's say, you are creating a web application. To aid this you need several resources like a virtual machine,  storage account, sql database, virtual networks and many other dependant and related services.
Without resource groups, if you have to develop and deploy this application, you have to manually create all these azure resources. That too, you have to create them in the right order. If it's just one time, then it's okay. But in real-world, with every company using agile approach and CI/CD i.e Continuous Integration & Continuous Deployment, applications are deployed several times a day. For example, everytime, a new piece of code is checked-in to the source control, a new build is deployed to the test-environment. So everytime we have to do this, if we have to create all the resources manually, it's not only tedious and time consuimg, but also error-prone. What if you create the resources in the wrong order or even worse what if you forget to create a resource. It gets even more messy and complicated if you have to manage multiple applications and multiple environments.

## Cost management is easier
In the azure portal, on the cost analysis blade, you can see the cost of running each resource. You can also see the total cost of all the resources in the resource group. When you are done with a set of resources, there is no need for you to delete each resource individually. When you delete a resource group, all the resources in that group are also deleted. This obviously eliminates any possibility of orphaned resources (ghost resources) left running, and as a result running up costs.

## Role-based access control (RBAC)
Role-based access control (RBAC) can be applied at the resource group level. This makes it much easier to manage user access to the resources in the group. When the users log into the azure portal, they will only see resource groups they have access to and not others within the subscription. Administrators will still be able to assign access control for users to individual resources within the resource group based on their roles.