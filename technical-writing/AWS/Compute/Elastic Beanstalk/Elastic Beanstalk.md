## Elastic Beanstalk
Elastic Beanstalk is a platform within AWS that is used for deploying and scaling web applications. In simple terms this platform as a service (PaaS) takes your application code and deploys it while provisioning the supporting architecture and compute resources required for your code to run. Elastic Beanstalk also fully manages the patching and security updates for those provisioned resources. 

There are many PaaS solutions in the cloud computing space including Redhat Open Shift, Google App Engine, Scalingo, Python Anywhere, Azure App Service, however AWS Elastic Beanstalk remains one of the leading PaaS choices among app developers.

There is no charge to use Elastic Beanstalk to deploy your applications, you are only charged for the resources that are created to support your application.

AWS Elastic Beanstalk allows you to quickly deploy applications and services without having to worry about configuring underlying resources, services, operating systems or web servers.

Elastic Beanstalk takes care of the hosting infrastructure, coding language interpreter, operating system, security, https service and application layer. All you need to worry about is writing your code.

You can develop code in a number of languages which is then zipped up and the zip file is used when instantiating a new elastic beanstalk instance.

Supported language platforms include:

Ruby
Python
PHP
Go
Node.js
Java 
.NET on Windows Server IIS
.NET Core on Linux
Packer Builder
Glassfish
Docker
Tomcat
The web servers provisioned will be familiar to most web developers and include Apache, Tomcat, Nginx and IIS

You can still maintain control over the compute instance type used by elastic beanstalk when deploying your application to the cloud and you can also keep control over the database type and level of auto scaling required for your application.

You can access server log files of your deployed web application, update your application whenever required and enable HTTPS on the load balancer when required.

Using the Elastic Beanstalk platform delivers the opportunity to spend more time developing and less time managing your network, storage, o/s and compute runtimes as this is all handled by Elastic Beanstalk. This leads to quicker deployment since all you need to do is package up your code, feed it to Elastic Beanstalk and the platform takes it from there. 

You don't need to spend time selecting compute instances, database and storage requirements, security, monitoring services, load balancing resources and so on which leads to much faster deployment. You take care of the code and elastic beanstalk does the rest.

After deployment, the operations of your Elastic Beanstalk hosted applications is also easier. You no longer have to take on the role of monitoring servers, monitoring storage, managing network loads, keeping operating systems up to date since this is all taken care of by the platform.

**ELASTIC BEANSTALK FEATURES**

Elastic Beanstalk is possibly the simplest and fastest way to deploy web applications on AWS.

It allows you to focus on writing code instead of provisioning and configuring AWS resources.

Elastic beanstalk handles the auto scaling of resources needed to support your deployed application as demand grows or shrinks.

When Elastic Beanstalk analyses your application and selects the resources that will be requires, it also allows you to step in and select alternative resources that may be better suited to anticipated use cases it may not know about. For example you could select a higher spec EC2 instance type that better suits your needs.

## ELASTIC BEANSTALK COMPONENTS
**Application:**

Typically when you create an application, you will place all the related assets like code, resource configuration templates, code versions and required files in a folder. 

An Elastic beanstalk application is a similar concept, it is the entity that holds all the related files, platform resources and configuration information to support the application when you deploy your application via elastic beanstalk.

When you create and deploy a new application or version, the application name will appear in the elastic beanstalk console.

**Application Version:**

When you make changes to your application you can deploy the updated application via elastic beanstalk.  The application version relates to a specific labeled iteration of deployable code for your web application.

Within elastic beanstalk, the application version is a link to an S3 object that contains your deployable Zip or Java WAR file

The named version will appear as a new application should you choose to deploy it into a different environment rather than deploying from within an existing application.

**Environments:**

When you deploy your application with elastic beanstalk, an environment is created to house the version of the application you are deploying. The environment hosts the required EC2 instances, storage, load balancer, autoscaling groups or anything else required by this version of the application.

A single environment can only run one version of your application. You can deploy your new version over the top of an existing application environment, like say production, however you also have the flexibility to install to alternative environments like development, staging or testing environments.

Each environment will have a unique URL to access the running application.

**Environment Tiers:**

There are two tiers instantiated when you deploy an application via elastic beanstalk.

The Web Server environment tier is the front facing segment that responds to http requests from users accessing the application URL.

A Worker environment tier is a background service that processes requests delegated by the web server tier and can also run workloads processing background tasks. You can write code and deploy that code to a worker environment instead of the main web server application.

**Environment Health:**

Elastic beanstalk monitors your web server application and worker environments and performs health checks on how the application is running.

The health of an environment is reported using colour codes for instant visual recognition that all is well, or not.

* Grey - lets you know your environment is being updated or is still being provisioned.

* Green - Your environment is healthy and has passed its latest health check.

* Yellow - Your environment has failed one or two recent checks

* Red - Your environment has failed three or more recent health checks.

**ELASTIC BEANSTALK WEB SERVER ARCHITECTURE:**

When you deploy an application using elastic beanstalk to a web server environment the environment will typically create the following architecture structure.

Elastic Beanstalk Environment

Elastic Load Balancer

Auto Scaling Group

EC2 Instances

Host Manager

Security Groups

**The Elastic Beanstalk environment** is the container for this unique version of the application and it provides a cname and URL entry point for users to access the application.

**The elastic load balancer** distributes http requests to the EC2 instances that have been provisioned within the environment.

**The Auto Scaling Group** will scale in and scale out the number of EC2 instances that exist within the environment based on traffic load.  You can specify how many EC2 instances you want to start with and how many you will allow the auto scaler to instantiate within the settings of the elastic beanstalk environment.

**The EC2 instances** are the compute images that run your workloads. Elastic beanstalk will suggest the size and type of EC2 instance, however you can manually change these instance types to increase or decrease CPU capacity and reserved memory should you anticipate higher or lower compute power will be required to adequately provide acceptable application performance for your users.

**The host manager** is present on each of your EC2 instances and is responsible for monitoring and reporting on the performance of your application, reports on resource instance level events and sends logs to your cloudwatch dashboard.

**A new security group** will be provisioned for an elastic beanstalk application environment which will allow http access to your application using port 80. Using the modify settings elastic beanstalk dashboard you can allocate additional security groups or an existing VPC to your web server environment.

**ELASTIC BEANSTALK WORKER ENVIRONMENT**

A worker environment is created to process specific background tasks, but will also be created to assist your web server application when it is under load.

When a web application is processing a time-intensive task in response to a user request, should a second user make a request the user will need to wait and there is the possibility that the request will time out.

To resolve this issue, when tasks are taking too much time to process at the web server, elastic beanstalk will pass the user requests to the background worker environment which will queue and process the requests in an orderly fashion. This frees up the web server to accept multiple requests without timing out as it passes the requests to the worker for processing.

**HOW DOES THE ELASTIC BEANSTALK AND WEB APPLICATION AND WORKER COMMUNICATE?**

When the web server detects a request is taking too long, subsequent requests are passed via SQS message to a SQS queue.  The worker environment has a daemon running that polls the SQS Queue and retrieves the SQS messages sequentially for processing. The worker environment then returns http responses back to the client that made the request.

**HOW TO DEPLOY AN APPLICATION USING ELASTIC BEANSTALK.**

The Elastic beanstalk service can be located under the compute services in your AWS console.

* First step is to create a new web app and give it a unique name. 

* You can also add up to 50 tags to the application at this point.

* Now you need to select a platform for the build.

* Select a platform, a platform branch (o/s) and a platform version

* At this point you can select a sample application which we’ll do in this example.  It's at this stage you can upload your own code.

* If you are uploading your own code, it will need to be a ZIP or WAR file either located on your local computer or stored in a public S3 bucket.  At this point you will need to allocate a version label to your code which needs to be unique.

* Then go ahead and create application.

Elastic Beanstalk will start to create all the required resources and display a status screen with the log of the supporting resources being created.

The process for the sample application creates:

* S3 bucket
* ELB
* Security Group
* Auto Scaling Group
* ASG Group Policy
* CloudWatch Alarms
* Load Balancer Listener
* EC2 instances
* MyAwesomeWebApp Environment

You can now open the URL displayed above the health check to open the application.

