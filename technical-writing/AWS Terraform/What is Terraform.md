## What is Terraform?
Terraform is an infrastructure as code (IaC) tool that allows you to create, manage, and update infrastructure resources such as virtual machines, networks, and storage in a repeatable, scalable, and automated way.

### Why we use terraform?
Terraform is a tool for building, changing, and versioning infrastructure in a safe, repeatable way. It enables teams to manage infrastructure as code, providing a single source of truth for the infrastructure and ensuring that it is always in the desired state. Terraform can be used to manage infrastructure across multiple cloud providers and on-premises infrastructure, and it supports a wide range of resource types.

### What is Infrastructure as Code (IaC)?
Infrastructure as Code (IaC) is a practice of managing and provisioning infrastructure using code instead of manual processes. By treating infrastructure as code, teams can version control their infrastructure, automate the provisioning process, and improve collaboration between different teams. IaC enables teams to make changes to infrastructure in a safe and repeatable way, and it helps to reduce the risk of human error and inconsistencies.

### What is Resource?
In Terraform, a resource is a declarative representation of a component in a cloud infrastructure, such as a virtual machine, database, or network interface. Resources define the desired state of the component, and Terraform uses the resource definition to create, modify, or delete the component as needed.

### What is Provider?
In Terraform, a provider is a plugin that interfaces with a specific cloud infrastructure provider or service. Providers define the resources that Terraform can manage, as well as the methods for creating, updating, and deleting those resources. Examples of providers include AWS, Google Cloud, and Microsoft Azure.

### What is State file in terraform? What’s the importance of it ?
The Terraform state file is a JSON file that stores the state of the infrastructure managed by Terraform. It includes information about the resources that have been created, their current state, and any dependencies between them. The state file is critical to Terraform's operation, as it is used to plan and execute changes to the infrastructure. The state file should be kept in a safe and secure location, as it contains sensitive information about the infrastructure.

### What is Desired and Current State?
In Terraform, the desired state is the state that you want your infrastructure to be in, as defined in your Terraform configuration files. The current state is the actual state of the infrastructure, as represented in the Terraform state file. When you run terraform apply, Terraform compares the desired state with the current state and makes changes as needed to bring the infrastructure into the desired state.