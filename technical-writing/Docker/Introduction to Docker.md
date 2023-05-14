# Docker overview
As a developer, you have probably heard of Docker at some point in your professional life. And you're likely aware that it has become important tech for any application developer to know.

If you have no idea of what I'm talking about, no worries – that's what this article is for.

We'll go on a journey to discover what is this Docker everyone is talking about and what you can do with it. By the end, we'll also create, publish, and run our first Docker image.
## A Little Bit of Container History
Docker is a container runtime. A lot of people think that Docker was the first of its kind, but this is not true – Linux containers have existed since the 1970s.

Docker is important to both the development community and container community because it made using containers so easy that everyone started doing it.
Docker was created to work on the Linux platform, but has extended to offer greater support for non-Linux operating systems, including Microsoft Windows and Apple OS X. Versions of Docker for Amazon Web Services (AWS) and Microsoft Azure are available.
## Why use docker
Containerization is a technology that is enjoying huge popularity in the tech world – and Docker is a renowned player of it. You need to know that numerous IT giants are providing various enriching career opportunities to Docker professionals. The major reason behind such an immensely growing demand for Docker is that it actually resolves the cult problem of every development team – **"It works on my machine"**.

**Let us understand it with a basic example**.

*Suppose there are four developers in a team working on a single project. Meanwhile, one is having a Windows system, the second is owning a Linux system, and the third & fourth ones are working with macOS. Now, as you see, they are using the distinct environments for creating a single application or software they will be required to carry on the things in accordance with their respective machines such as the installation of different libraries & files for their system, etc. And such situations, especially on an organizational or larger level, often cause numerous conflicts and problems throughout the entire software development life cycle. However, the containerization tools such as Docker eliminates this problem.*

In particular, Docker is a containerization platform that enables you to create, deploy, and run applications conveniently with the help of containers. It is basically concerned with the packaging of applications with all their required libraries and other dependencies in a container by the developer. Docker was launched in 2013 by the American technology company Docker, Inc. – formerly known as dotCloud. Along with containers, Docker has several other major components as well like – Docker Images, Docker File, Docker Registries, etc. Truly, with the help of Docker – developers are able to write code or build applications without worrying about the environment.
## Major advantages of using Docker
* **Consistent & Isolated Environment** -

The very first advantage of Docker is that it provides you with a consistent and isolated environment. It takes the responsibility of isolating and segregating your apps and resources in such a way that each container becomes able to access all the required resources in an isolated manner i.e., without disturbing or depending on another container. It eventually allows you to run multiple containers simultaneously on the same host. Moreover, as each container is only allowed to access the assigned resources – it helps in reducing the risk of several potential issues such as downtime, etc. Also, you can easily remove any app by deleting its container, and it will not leave behind any temporary files, etc. on your system.

In simple words, what the consistent environment here means is that the Docker image created by you during any development stage will work similarly in other **SDLC**(Software Development Life Cycle) phases also such as testing, production, etc.

* **Rapid Application Deployment** -

Docker indeed fastens the application deployment process to a greater extent. It efficiently organizes the entire development lifecycle by providing a standardized working environment to the developers. You need to know that Docker creates a container for every individual process and subsequently the Docker apps do not boot into an OS – that saves a lot of time. The docker containers come up with the minimal runtime requirements of the application that allows them to deploy faster. Here, you’re not required to set up a new environment – all you need to do is download the Docker image to run it on different environments. These images are quite smaller in size that further prompts rapid application deployment. Docker is very preferable for Continuous Integration and Continuous Delivery (CI/CD) workflows.

* **Ensures Scalability & Flexibility** -

Docker leverages you with the utmost level of scalability and flexibility. Due to the consistent environment – the Docker images can be easily sorted across multiple servers. For instance, if you’re required to do an upgrade during the release of the application – you can conveniently do the changes in Docker containers, can test them & roll out new containers. Other than that, you can efficiently clean up or repair the application without completely taking it down. It has the ability to be deployed in multiple physical servers, data servers, or cloud platforms. Also, Docker allows you to rapidly create replications for redundancy reasons, and it makes you enable to start and terminate the application or services promptly to make things much easier.

* **Better Portability** -

Another enriching advantage of Docker is Portability! The applications created with Docker containers are immensely portable. The Docker containers can run on any platform whether it be Amazon EC2, Google Cloud Platform, VirtualBox, Rackspace server, or any other – though the host OS should support Docker. As the application and all its dependencies are packaged together in a Docker container – you can deploy it to any system that supports Docker and the application will perform similarly. For instance, the Docker containers can swiftly move from the cloud environment to localhost and vice-versa. It subsequently results in various benefits such as no wastage of time & resources in setting up environments, debugging issues in environments, etc. It really helps the developers to make the development process more responsive and agile.

* **Cost-Effective** -

Needless to say, every tech organization wants to opt for such development and deployment practices or resources that can help them to reduce overall cost without compromising with the standard workflow or product quality. And Docker can help them to achieve this feat! As Docker reduces the need for more infrastructure resources for development and the container created for individual processes can be shared with other apps with instances of these containerized apps using less memory compared to virtual machines – it makes the development and deployment process more cost-effective. With Docker, developers can run multiple containers on a single server that results in the efficient use of resources. Meanwhile, Docker subsequently requires a smaller team of professionals compared to the traditional workflow that also leads to minimized workforce costs for the organization.

* **In-Built Version Control System** -

Going down with the list, let us tell you another prominent advantage of Docker – it comes up with an in-built version control system. The Docker containers allow you to commit changes to the Docker images and version control them conveniently. For instance – if you are having some issues with the current or upgraded version of the image – you can quickly roll back to a previous stable version of the Docker image. Docker enables you to easily track successive versions of a container and inspect the differences before rolling back to the previous versions. In addition, the containers can maintain all configurations and dependencies internally and the components from the previous layers can be reused by the containers for better efficiency.

## What can I use Docker for?

**Fast, consistent delivery of your applications**

Docker streamlines the development lifecycle by allowing developers to work in standardized environments using local containers which provide your applications and services. Containers are great for continuous integration and continuous delivery (CI/CD) workflows.

Consider the following example scenario:

* Your developers write code locally and share their work with their colleagues using Docker containers.
* They use Docker to push their applications into a test environment and execute automated and manual tests.
* When developers find bugs, they can fix them in the development environment and redeploy them to the test environment for testing and validation.
* When testing is complete, getting the fix to the customer is as simple as pushing the updated image to the production environment.

**Responsive deployment and scaling**

Docker’s container-based platform allows for highly portable workloads. Docker containers can run on a developer’s local laptop, on physical or virtual machines in a data center, on cloud providers, or in a mixture of environments.

Docker’s portability and lightweight nature also make it easy to dynamically manage workloads, scaling up or tearing down applications and services as business needs dictate, in near real time.

**Running more workloads on the same hardware**

Docker is lightweight and fast. It provides a viable, cost-effective alternative to hypervisor-based virtual machines, so you can use more of your compute capacity to achieve your business goals. Docker is perfect for high density environments and for small and medium deployments where you need to do more with fewer resources.

## Docker architecture
Docker uses a client-server architecture. The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing your Docker containers. The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon. The Docker client and daemon communicate using a REST API, over UNIX sockets or a network interface. Another Docker client is Docker Compose, that lets you work with applications consisting of a set of containers.

**The Docker daemon**

The Docker daemon (dockerd) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. A daemon can also communicate with other daemons to manage Docker services.

**The Docker client**

The Docker client (docker) is the primary way that many Docker users interact with Docker. When you use commands such as docker run, the client sends these commands to dockerd, which carries them out. The docker command uses the Docker API. The Docker client can communicate with more than one daemon.

**Docker Desktop**

Docker Desktop is an easy-to-install application for your Mac or Windows environment that enables you to build and share containerized applications and microservices. Docker Desktop includes the Docker daemon (dockerd), the Docker client (docker), Docker Compose, Docker Content Trust, Kubernetes, and Credential Helper. For more information, see Docker Desktop.

**Docker registries**

A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub by default. You can even run your own private registry.

When you use the docker pull or docker run commands, the required images are pulled from your configured registry. When you use the docker push command, your image is pushed to your configured registry.

**Docker objects**
When you use Docker, you are creating and using images, containers, networks, volumes, plugins, and other objects. This section is a brief overview of some of those objects.

**Images**
An image is a read-only template with instructions for creating a Docker container. Often, an image is based on another image, with some additional customization. For example, you may build an image which is based on the ubuntu image, but installs the Apache web server and your application, as well as the configuration details needed to make your application run.

You might create your own images or you might only use those created by others and published in a registry. To build your own image, you create a Dockerfile with a simple syntax for defining the steps needed to create the image and run it. Each instruction in a Dockerfile creates a layer in the image. When you change the Dockerfile and rebuild the image, only those layers which have changed are rebuilt. This is part of what makes images so lightweight, small, and fast, when compared to other virtualization technologies.

**Containers**
A container is a runnable instance of an image. You can create, start, stop, move, or delete a container using the Docker API or CLI. You can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state.

By default, a container is relatively well isolated from other containers and its host machine. You can control how isolated a container’s network, storage, or other underlying subsystems are from other containers or from the host machine.

A container is defined by its image as well as any configuration options you provide to it when you create or start it. When a container is removed, any changes to its state that are not stored in persistent storage disappear.