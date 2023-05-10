## Basic Terraform Commands

### terraform init:
Initializes a new or existing Terraform working directory by downloading the required provider plugins and sets up the backend to store the state. This command must be run before any other Terraform command is executed.

### terraform init -upgrade:
Upgrades the configuration to the latest version of Terraform. This is useful if you've upgraded your Terraform version and want to ensure that your configuration is compatible with the new version.

### terraform plan:
Shows the changes that Terraform will make to the infrastructure to bring it into the desired state, without actually making the changes. This is useful to see what changes Terraform will make before actually applying them.

### terraform apply:
Applies the changes to the infrastructure described in the Terraform configuration file. This command will create, modify, or delete resources as needed to bring the infrastructure into the desired state.

### terraform validate:
Validates the syntax and structure of the Terraform configuration file. This command checks for errors, missing required arguments, and other issues.

### terraform fmt:
Rewrites Terraform configuration files to a canonical format, which makes it easier to read and maintain.

### terraform destroy:
Destroys all the infrastructure created by Terraform, freeing up resources and ensuring that you're not paying for unused infrastructure. This command should be used with caution as it will delete all the resources described in the configuration file.

## What are the main competitors of Terraform?
### AWS CloudFormation
AWS CloudFormation is an IaC tool provided by Amazon Web Services (AWS). It allows users to define and manage infrastructure resources in a declarative way using JSON or YAML templates. CloudFormation supports a wide range of AWS services and is tightly integrated with other AWS tools and services.

### Ansible
Ansible is an open-source IaC tool that uses YAML scripts to define and manage infrastructure resources. Ansible can be used for provisioning, configuration management, and application deployment across multiple platforms and cloud providers.

### Kubernetes
Kubernetes is another IT automation alternative to Terraform. It is an open-source solution that enables automated deployment, management, and scaling of containerized applications. It simplifies container communication. It facilitates container discovery and management within an application.

### Puppet
Puppet is another open-source IaC tool that uses a declarative language to define and manage infrastructure resources. Puppet has a large community of users and contributors and supports a wide range of platforms and cloud providers.

### Chef
Chef is an open-source IaC tool that uses Ruby scripts to define and manage infrastructure resources. Chef is particularly well-suited for managing large-scale infrastructures and supports a wide range of platforms and cloud providers.

### Packer
Packer create identical machine images for multiple platforms from a single source configuration. A common use case is creating golden images for organizations to use in cloud infrastructure.

### Cloud Foundry
Cloud Foundry is an open source cloud application platform that makes it faster and easier to build, test, deploy, and scale apps in your choice of cloud, framework, and language. Remove the cost and complexity associated with configuring, managing, and securing infrastructure for your app with Cloud Foundry.