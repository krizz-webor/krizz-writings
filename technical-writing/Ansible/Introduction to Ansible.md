## Introduction to Ansible
### Ansible Architecture
The Ansible orchestration engine interacts with a user who is writing the Ansible playbook to execute the Ansible orchestration and interact along with the services of private or public cloud and configuration management database. You can show in the below diagram, such as:

**Inventory**: Inventory is lists of nodes or hosts having their IP addresses, databases, servers, etc. which are need to be managed.

**API's**: The Ansible API's works as the transport for the public or private cloud services.

**Modules**: Ansible connected the nodes and spread out the Ansible modules programs. Ansible executes the modules and removed after finished. These modules can reside on any machine; no database or servers are required here. You can work with the chose text editor or a terminal or version control system to keep track of the changes in the content.

**Plugins**: Plugins is a piece of code that expends the core functionality of Ansible. There are many useful plugins, and you also can write your own.

**Playbooks**: Playbooks consist of your written code, and they are written in YAML format, which describes the tasks and executes through the Ansible. Also, you can launch the tasks synchronously and asynchronously with playbooks.

**Hosts**: In the Ansible architecture, hosts are the node systems, which are automated by Ansible, and any machine such as RedHat, Linux, Windows, etc.

**Networking**: Ansible is used to automate different networks, and it uses the simple, secure, and powerful agentless automation framework for IT operations and development. It uses a type of data model which separated from the Ansible automation engine that spans the different hardware quite easily.

**Cloud**: A cloud is a network of remote servers on which you can store, manage, and process the data. These servers are hosted on the internet and storing the data remotely rather than the local server. It just launches the resources and instances on the cloud, connect them to the servers, and you have good knowledge of operating your tasks remotely.

**CMDB**: CMDB is a type of repository which acts as a data warehouse for the IT installations.

### Ansible Terms
**Controller machine/Ansible server**: The machine where the Ansible is installed, responsible for running the provisioning on the servers you are managing and from which all tasks and playbooks will be ran.

**Inventory**: An installation file that contains information about the servers you are managing.

**Playbook**: The entry point of Ansible provisioning, where the automation is defined through tasks using YAML format

**Task**: A block that defines a single procedure to be executed, eg. install a package.

**Module**: A module typically abstact a system task, like dealing with packages or creating changing files, Ansible has a multitude of built-in modules, but you can also create custom ones.

**Roles**: A way of organizing tasks and related files to be later called in a playbook. A pre-defined way of organizing playbooks and other files in other to facilitate sharing and re-using portions of a provisioning.

**Facts**: Information fetched from the client system from the global variables with the gather-facts operation. Global variables containg information about the system, like network interfaces or operating system.

**Handler**: Used to trigger service status changes, restarting and stopping service.

**Play**: A provisioning executed from start to finish is called a play. In simple word, execution of a playbook is called Play.

**Notifier**: Section attributed to a task which calls a handler if the output is changed.

**Tag**: Name set to a task which can be used later on to issue just that specific task or group of tasks.

