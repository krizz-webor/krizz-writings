# Amazon RDS
The world is changing, with every idea being converted into an application, millions of new applications go online every day. Now for any application or project to be successful, it should have a unique idea behind it.

Let’s talk about you, you just had the world’s most amazing idea, and you want to create an application around it.

Now imagine yourself 10 years back, when to have the application up and ready, you’d have to setup a back end server, research and install various softwares to support your application, after all of these tiring tasks you would have started developing your application.

What about its maintenance? You would have to install all the latest security patches and updates for your backend server and also make sure that it stays in a healthy state.

Now, while you were taking care of all that, your app becomes famous overnight, with tons of traffic directed at your application, the need to scale becomes your top most priority, now let’s not even think about the investment you will be making on this task, how will you accomplish this task of scaling up and configuring all these extra servers quickly?

Amazon Web Services (AWS) offers a service called RDS AWS (Relational Database Service), which does all these tasks (i.e. setup, operate, update) for you automatically.

You just have to select the database that you want to launch, and with just one click you have a back end server at your service which will be managed automatically!

Let’s take an example here, suppose you start a small company.

You want to launch an application which will be backed by a MySQL database and since there is a lot of Database work, there are chances that the development work will fall behind.

For bigger companies where you have a bigger team, which manages your database servers; using RDS, that team can be reduced to a significant number and perhaps be optimally deployed!

## The Amazon Relational Database Service (RDS AWS)
Is a web service that makes it easier to set up, operate, and scale a relational database in the cloud. It provides cost-efficient, re-sizable capacity in an industry-standard relational database and manages common database administration tasks.

So people often develop a misconception, when they confuse RDS with a database.

## RDS AWS Components:
* DB Instances
* Regions and Availability Zones
* Security Groups
* DB Parameter Groups
* DB Option Groups

**DB Instances**
* They are the building blocks of RDS. It is an isolated database environment in the cloud, which can contain multiple user-created databases, and can be accessed using the same tools and applications that one uses with a stand-alone database instance.
* A DB Instance can be created using the AWS Management Console , the Amazon RDS API, or the AWS Command line Interface .
* The computation and memory capacity of a DB Instance depends on the DB Instance class. For each DB Instance you can select from 5GB to 6TB of associated storage capacity.
* The DB Instances are of the following types:
1. Standard Instances (m4,m3)
2. Memory Optimised (r3)
3. Micro Instances (t2)

**Regions and Availability Zones**
* The AWS resources are housed in highly available data centers, which are located in different areas of the world. This “area” is called a region.
* Each region has multiple Availability Zones (AZ), they are distinct locations which are engineered to be isolated from the failure of other AZs.
* You can deploy your DB Instance in multiple AZ, this ensures a failover i.e. in case one AZ goes down, there is a second to switch over to. The failover instance is called a standby, and the original instance is called the primary instance.

**Security Groups**
* A security group controls the access to a DB Instance. It does so by specifying a range of IP addresses or the EC2 instances that you want to give access.
* Amazon RDS uses 3 types of Security Groups:
1. VPC Security Group
* It controls the DB Instance that is inside a VPC.
2. EC2 Security Group
* It controls access to an EC2 Instance and can be used with a DB Instance.
3. DB Security Group
* It controls the DB Instance that is not in a VPC.

**DB Parameter groups**
* It contains the engine configuration values that can be applied to one or more DB Instances of the same instance type.
* If you don’t apply a DB Parameter group to your instance, you are assigned a default Parameter group which has the default values.

**DB Option groups**
* Some DB engines offer tools that simplify managing your databases.
* RDS makes these tools available with the use of Option groups.

## Benefits of Amazon RDS
Let’s talk about some interesting advantages that you get when you are using RDS AWS,

* So usually when you talk about database services, the CPU, memory, storage, IOs is bundled together, i.e. you cannot control them individually, but with AWS RDS, each of these parameters can be tweaked individually.
* Like we discussed earlier, it manages your servers, updates them to the latest software configuration, takes backup, everything automatically.
* The backups can be taken in two ways
1. The automated backups where in you set a time for your backup to be done.
2. DB Snapshots, where in you manually take a backup of your DB, you can take snapshots as frequently as you want. 
* It automatically creates a secondary instance for a failover, therefore provides high availability.
* RDS AWS supports **read replicas** i.e. snapshots are created from a source DB and all the read traffic to the source database is distributed among the read replicas, this reduces the overall overhead on the source DB.
* RDS AWS can be integrated with IAM, for giving customized access to your users who will be working on that database.

The updates to your database in RDS AWS are applied in a **maintenance window**. This maintenance window is defined during the creation of your DB Instance, the way it functions is like this:

* When an update is available for your DB you get a notification in your RDS Console you can take one of the following actions
1. Defer the maintenance items.
2. Apply maintenance items immediately.
3. Schedule a time for those maintenance items.
* Once maintenance starts, your instance has to be taken offline for updating it, if your instance is running in Multi-AZ, in that case the standby instance is updated first, it is then promoted to be a primary instance, and the primary instance is then taken offline for updating, this way your application does not experience a downtime.
* If you want to scale your DB instance, the changes that make to your DB instance also happen during the maintenance window, you can also apply them immediately, but then your application will experience a downtime if its in a Single-AZ.

**Pricing**
RDS AWS is billed based on the following parameters:

1. **Instance Class** i.e. the type of instance that you are choosing.
2. **Running Time** i.e. the amount of time an instance is running, partial hours are billed as full hours.
3. **Storage** i.e. the amount of storage that you have provisioned to your DB Instance
4. **I/O Requests per Month** i.e. the I/O requests that are made to your DB Instance per month
5. **Data Transfer**: Data transfer in and out of your DB Instance.

Another way of getting billed for AWS RDS is by reserving some instances.
**Reserved Instance** is also a way of using AWS RDS, in this you reserve an RDS Instance for a term, which can be for one or three years by making a one time payment, it is a less expensive way compared to the monthly bill that one pays.

**Free Tier**
AWS has an amazing free tier usage for most of its services, so that the customer can first use the service and then do the needful.

Similarly it offers free tier usage for RDS AWS, which includes the following benefits:

* 750 hours of Amazon RDS usage in single-AZ for db.t2.micro instance, every month for one year from signup.
* 20 GB of DataBase Storage: any combination of General Purpose (SSD) or Magnetic storage.
* 10 million IOs
* 20GB of backup storage

RDS is not a database, it’s a service that manages databases, having said that, let’s discuss the databases that RDS can manage as of now:
### Amazon Aurora
It is a relational database engine made by amazon which combines the speed and reliability of high-end commercial databases with the simplicity and cost-effectiveness of open source databases. 
* 5 times faster than standard MySQL
* 3 times faster than standard PostgreSQL

**Pricing**
Prices vary according to the region; if you have North Virginia as the region:

* Database Storage: $0.10/GB/month
* Backup Storage: $0.021/GB/month
### MySQL
MySQL is the world’s most used and popular relational database, and Amazon RDS provides an easy way to set-up, operate, and scale. You can use the code which you are writing because RDS for MySQL covers all versions of MySQL.

It is an open source database management system which uses SQL (Structured Query Language) to access the data stored in its system.

**Pricing**
* Database Storage: $0.115/GB/month
* Backup Storage: $0.095/GB/month
### PostgreSQL
PostgreSQL is yet another open source database management system which uses SQL to access the data.

**Pricing**
* Database Storage: $0.115/GB/month
* Backup Storage: $0.095/GB/month
### SQL Server
SQL Server is a Relational Database Management System, which was developed by Microsoft in 2005 for the enterprise environment.

**Pricing**
* Database Storage: $0.115/GB/month
* Backup Storage: $0.095/GB/month
### ORACLE
It is object-relational database management system which was developed by Oracle Inc.

**Pricing**
* Database Storage: $0.115/GB/month
* Backup Storage: $0.095/GB/month
### MariaDB
MariaDB is created by original creators of MySQL and it is very popular in creating PHP based applications. All versions of MariaDB is covered by Amazon EDS.

MariaDB is a community developed **fork** of MySQL DBMS. The reason for its fork, was the concern over the acquisition of Oracle over MySQL.
**Fork** means copying the source code of the original application, and starting development over the new application.

**Pricing**
* Database Storage: $0.115/GB/month
* Backup Storage: $0.095/GB/month

