# Deploying Docker containers on AWS ECS
### Deploy a Docker App to AWS using ECS
AWS proposes two container orchestrations services: ECS and Kubernete.

Well integrated with the AWS ecosystem, ECS is the proprietary version.

### What we will build
In this tutorial we will explain how to:

* Package and build a node application and package a simple node application with Docker
* Create an ECR repository to store our Docker Image
* Upload the Docker image to the repository
Create and launch an Elastic Container Cluster (ECR)
* Launch our application as a task within the Elastic Container Cluster
* Expose and open this application on the internet

![schema01](../../../media/schema01.png)

* **Docker** is a technology that helps to package and ship applications easily in production.
* **ECS** stands for Elastic Container Service. It is a fully managed container orchestration service
* **ECR** stands for Elastic Container Repository. ECR allows storage of Docker Images on AWS.

### Concepts:

* **A cluster** is a logical grouping of hardware resources.
* **A task** is a set of metadata (memory, CPU, port mapping, environmental variables, etc) that describes how a container should be deployed.
* **Services** are responsible for managing advanced configurations such as load balancing

### The NodeJS application to deploy
We want to deploy a basic express node application that displays the current time each time the index page is refreshed.

### package.json

    {
      "name": "docker_web_app",
      "version": "1.0.0",
      "description": "Node.js on Docker",
      "author": "Raphaël MANSUY raphael.mansuy+contact@gmail.com>",
      "main": "server.js",
      "scripts": {
        "start": "node server.js"
      },
      "dependencies": {
        "express": "^4.17.1"
      }
    }

### server.js

    "use strict"
    
    const express = require("express")
    
    // Constants
    const PORT = 8080
    const HOST = "0.0.0.0"
    
    // App
    const app = express()
    app.get("/", (req, res) => {
      res.send(`Hello World - ${new Date().toISOString()}`)
    })
    
    app.listen(PORT, HOST)
    console.log(`Running on http://${HOST}:${PORT}`)

### Package the node.js application with a Docker file
In the same directory of this application, we can create a Dockerfile that explains how to build a container with this application:

### Dockerfile

    FROM node:14
    
    #Create app directory
    WORKDIR /usr/src/app
    
    #Install app dependencies
    #A wildcard is used to ensure both package.json AND package-lock.json are copied
    #where available (npm@5+)
    COPY package*.json ./
    
    RUN npm install
    #If you are building your code for production
    #RUN npm ci --only=production
    
    #Bundle app source
    COPY . .
    
    EXPOSE 8080
    
    CMD [ "node", "server.js" ]

**This file defines the following steps:**

* start from the node:14 image
* create a directory `/usr/src/app` inside the container
* copy the local file with pattern `package*.json` in the container
* run `npm install`
* copy all the local files to the container
* expose the port `8080` inside the container
* run `node` with the file `server.js` when the container starts

### Building the image
Run the following command to build an image with the tag `node-web-app`

    docker build -t node-web-app .

### Running the image
Run the following command to start the application in detached mode:

    docker run -p 80:8080 -d node-web-app

The container is now running and the 8080 port within the container is exposed as the 80 port on your local machine.

We can now test the application with the `CURL command`

    curl http://localhost:80

**Results:**

    Hello World - 2021-02-11T05:06:12.739Z

We are now ready to deploy this container to the cloud.

### Connect to AmazonECR
**Prerequisites**

* `aws cli` must be installed
* your `aws profile` must be configured and have ECS admin rights enabled

Run the following command:

    aws ecr get-login-password --region us-west-2 | docker login

If you have access, you should have this displayed on the terminal:

    Authenticating with existing credentials...
    Login Succeeded

### Create your AmazonECR in the AWS Console
Connect to the AWS Console and to the ECS Administration screen to create a new repository.

![ecr1](../../../media/ecr1-1.png)

Click on `Create Repository` and choose `testrepository` as a name for your repository:

![ecr2](../../../media/ecr2.png)

The ECR repository has now been created:

![ecr3](../../../media/ecr3.png)

### Upload the image on AWS ECR
Click now on the `push commands button` on the repository screen:

![ecr4](../../../media/ecr4.png)

Copy and execute each command on your machine:

![ecr5](../../../media/ecr5.png)

**connect:**

    aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin 3680199100XXX.dkr.ecr.us-west-2.amazonaws.com

**build:**

    docker build -t testrepository .

**build:**

    docker tag testrepository:latest 3680199100XXX.dkr.ecr.us-west-2.amazonaws.com/testrepository:latest

**push to ECR:**

    docker push 3680199100XXX.dkr.ecr.us-west-2.amazonaws.com/testrepository:latest

The image is now published and available on ECR ready to be deployed:

![ecr6](../../../media/ecr6.png)

If you look at AmazonECR, repositories we can see the newly created image.

![ecr6_1](../../../media/ecr6_1.png)

![ecr6_2](../../../media/ecr6_2.png)

Copy the image URI: we need to keep this to create a task definition for the following steps.

    368019910004.dkr.ecr.us-west-2.amazonaws.com/testrepository:latest

### Create an ECS Cluster
Go to the ECS home page and click on the `create cluster` button:

![ecr7](../../../media/ecr7.png)

Choose `EC2 Linux + Networking` and then click `next`:

![ecr8](../../../media/ecr8.png)

Then enter the following information:

* name of the cluster: `ecs01`
* EC2 instance type: `t3-micro`
* Number of instances: `1`

![ecr9](../../../media/ecr9.png)

Then choose:

* Default VPC
* Auto assign IP: `Enabled`
* Security group: `default`
* Choose one of the subnet

![ecr10](../../../media/ecr10.png)

And then next press Enter

### Create a new Task definition
**A task** is a set of metadata (memory, CPU, port mapping, environmental variables, etc) that describes how a container should be deployed.

Click on new `Task definition`

![ecr11](../../../media/ecr11.png)

Choose `EC2`
![ecr12](../../../media/ecr12.png)

Then `next`

Choose `NodeWebAppTask` for the name of the task definition.

![ecr13](../../../media/ecr13.png)

Enter `128` for memory size.

Click `Add Container:`

![ecr14](../../../media/ecr14.png)

* Add the name of the container: NodeWebApp
* Set the image URI that we have saved to add the end of the add image step
* Set the port mappings 80:8080

![ecr15](../../../media/ecr15.png)

Click `create`.

![ecr16](../../../media/ecr16.png)

Then go to `Run Task`

![ecr17](../../../media/ecr17.png)

![ecr18](../../../media/ecr18.png)

The task is now running:

![ecr19](../../../media/ecr19.png)

If we click on the container instance:

![ecr20](../../../media/ecr20.png)

We can modify the security group associated with the instance to open the port `80`

![ecr21](../../../media/ecr21.png)

![ecr22](../../../media/ecr22.png)

Add `80` to the inbound rule for the security group:

![ecr23](../../../media/ecr23.png)

If we try now to open the url using the public IPV4 DNS: http://ec2-52-38-113-251.us-west-2.compute.amazonaws.com:

![ecr24](../../../media/ecr24.png)