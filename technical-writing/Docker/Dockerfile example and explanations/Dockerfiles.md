## Dockerfiles
Docker is a set of platforms as a service (PaaS) products that use the Operating system level visualization to deliver software in packages called containers. Containers are isolated from one another and bundle their own software, libraries, and configuration files; they can communicate with each other through well-defined channels. All containers are run by a single operating system kernel and therefore use fewer resources than a virtual machine.

### Difference between Docker Containers and Virtual Machines
1. **Docker Containers**

Docker Containers contain binaries, libraries, and configuration files along with the application itself.
They don’t contain a guest OS for each container and rely on the underlying OS kernel, which makes the containers lightweight.
Containers share resources with other containers in the same host OS and provide OS-level process isolation.

2. **Virtual Machines**

Virtual Machines (VMs) run on Hypervisors, which allow multiple Virtual Machines to run on a single machine along with its own operating system.
Each VM has its own copy of an operating system along with the application and necessary binaries, which makes it significantly larger and it requires more resources.
They provide Hardware-level process isolation and are slow to boot.

### Important Terminologies in Docker 
1. **Docker Image**

It is a file, comprised of multiple layers, used to execute code in a Docker container.
They are a set of instructions used to create docker containers.

2. **Docker Container**

It is a runtime instance of an image.
Allows developers to package applications with all parts needed such as libraries and other dependencies.

3. **Docker file**

It is a text document that contains necessary commands which on execution helps assemble a Docker Image.
Docker image is created using a Docker file.

4. **Docker Engine**

The software that hosts the containers is named Docker Engine.
Docker Engine is a client-server based application
#### The docker engine has 3 main components:
**Server**: It is responsible for creating and managing Docker images, containers, networks, and volumes on the Docker. It is referred to as a daemon process.

**REST API**: It specifies how the applications can interact with the Server and instructs it what to do.

**Client**: The Client is a docker command-line interface (CLI), that allows us to interact with Docker using the docker commands.

5. **Docker Hub**

Docker Hub is the official online repository where you can find other Docker Images that are available for use.
It makes it easy to find, manage, and share container images with others.

## Dockerfile

Build stage base image
**FROM** node

Setting the working directory to /app
**WORKDIR** /app

Set the Author field of the generated images.
**MAINTAINER** jason

Copy the package.jason to /app
**COPY** package.jason /app

Run command to install npm in the image
**RUN** npm install

Copy project files and folders to the working directory
**COPY** . /app

Expose the application on port 80
**EXPOSE** 80

Start up command for the application
**CMD** ["node", "server.js"]
