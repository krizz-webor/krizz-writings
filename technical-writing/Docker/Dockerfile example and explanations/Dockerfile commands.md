## Dockerfile Commands

### Dockerfile
A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Think of it as a shellscript. It gathered multiple commands into a single document to fulfill a single task.

Build command is used to create an image from the Dockerfile.

     $ docker build 

You can name your image as well.

     $ docker build -t my-image .

If your Dockerfile is placed in another path,

     $ docker build -f /path/to/a/Dockerfile . 

Let's first look at a Dockerfile and discuss those commands.

We are going to take the official MySQL Dockerfile as an example.

    FROM debian:stretch-slim
    
    # add our user and group first to make sure their IDs get assigned consistently, regardless of whatever dependencies get added
    
    RUN groupadd -r mysql && useradd -r -g mysql mysql
    
    RUN apt-get update && apt-get install -y --no-install-recommends gnupg dirmngr && rm -rf /var/lib/apt/lists/*
    
    RUN mkdir /docker-entrypoint-initdb.d
    
    ENV MYSQL_MAJOR 8.0
    
    ENV MYSQL_VERSION 8.0.15-1debian9
    
    VOLUME /var/lib/mysql
    
    # Config files
    
    COPY config/ /etc/mysql/
    
    COPY docker-entrypoint.sh /usr/local/bin/
    
    RUN ln -s usr/local/bin/docker-entrypoint.sh /entrypoint.sh # backwards compat
    
    ENTRYPOINT ["docker-entrypoint.sh"]
    
    EXPOSE 3306 33060
    
    CMD ["mysqld"]

Here's what's being done here:

* Select the operating system.

* Create a user for MySQL.

* Update packages and install software.

* Configure the environment.

These are the steps we will use to install MySql in our Linux machine. Now it's bundled inside the dockerfile to anyone to get and create images.

Let's try to understand the purposes of these commands.

### Dockerfile Commands
* FROM - specifies the base(parent) image. Alpine version is the minimal docker image based on Alpine Linux which is only 5mb in size.

* **RUN** - runs a Linux command. Used to install packages into container, create folders, etc

* **ENV** - sets environment variable. We can have multiple variables in a single dockerfile.

* **COPY** - copies files and directories to the container.

* **EXPOSE** - expose ports

* **ENTRYPOINT** - provides command and arguments for an executing container.

* **CMD** - provides a command and arguments for an executing container. There can be only one CMD.

* **VOLUME** - create a directory mount point to access and store persistent data.

* **WORKDIR** - sets the working directory for the instructions that follow.

* **LABEL** - provides metada like maintainer.

* **ADD** - Copies files and directories to the container. Can unpack compressed files.

* **ARG** - Define build-time variable.

**COPY vs. ADD**
Both commands serve a similar purpose, to copy files into the image.

* **COPY** - let you copy files and directories from the host.

* **ADD** - does the same. Additionally it lets you use URL location and unzip files into image.

Docker documentation recommends to use COPY command.

**ENTRYPOINT vs. CMD**
 **CMD** - allows you to set a default command which will be executed only when you run a container without specifying a command. If a Docker container runs with a command, the default command will be ignored.

* **ENTRYPOINT** - allows you to configure a container that will run as an executable. ENTRYPOINT command and parameters are not ignored when Docker container runs with command line parameters.

**VOLUME**
You declare VOLUME  in your Dockerfile to denote where your container will write application data. When you run your container using -v   you can specify its mounting point.

### Frequently used Dockerfile commands -
**FROM** - Defines a base image, it can be pulled from docker hub
(for example- if we want to create a javascript application with node as backend then we need to have node as a base image, so it can run node application.)

**RUN** - Executes command in a new image layer( we can have multiple run commands )

**CMD** - Command to be executed when running a container( It is asked to have one CMD command, If a Dockerfile has multiple CMDs, it only applies the instructions from the last one.

**EXPOSE** - Documents which ports are exposed (It is only used for documentation)

**ENV** - Sets environment variables inside the image

**COPY** - It is used to copy your local files/directories to Docker Container.

**ADD** - It is more feature-rich version of the COPY instruction. COPY is preferred over ADD. Major difference b/w ADD and COPY is that ADD allows you to copy from URL that is the source can be URL but in COPY it can only have local ones.

**ENTRYPOINT** - Define a container's executable (You cannot override and ENTRYPOINT when starting a container unless you add the --entrypoint flag.)

**VOLUME** - It defines which directory in an image should be treated as a volume. The volume will be given a random name which can be found using docker inspect command.

**WORKDIR** - Defines the working directory for subsequent instructions in the Dockerfile(Important point to remember that it doesn't create a new intermediate layer in Image)

    # Basic Dockerfile
    FROM ubuntu:18.04
    
    COPY . /app
    
    RUN make /app
        
    CMD python /app/app.py

**FROM** creates a layer from the ubuntu:18.04 Docker image.
**COPY** adds files from your Docker client’s current directory.
**RUN** builds your application with make.
**CMD** specifies what command to run within the container.
