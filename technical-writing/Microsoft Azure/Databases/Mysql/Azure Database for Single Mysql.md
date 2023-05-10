## Azure Database for Single Server Mysql
Azure database for Mysql is a Relational Database Service provider powered by Mysql community edition. You can use either Single server or Flexible serverto host Mysql dadabase in Azure. It's a fully managed database as a service offering that can handle mission-crirteria workloads with predictable performance and dynamic scalability.

Azure Database for MySQL is a PaaS feature in Microsoft’s Azure Cloud. Basically, you get a fully functional, fully managed relational MySQL database server based on the latest MySQL Community edition (MYSQL version 8.0.28 at the time of writing). The only difference is that the server is hosted on the Azure cloud. Microsoft is responsible for managing the infrastructure of servers and providing high redundancy, high availability, and up to 99.99% uptime SLAs.

### Business benefits of using Azure Database for MySQL:

* **99.99% availability** – Azure provides a high availability SLA for all its services, ensuring that you face virtually zero downtime. Find a detailed region-wise SLA guide here.
* **Fully managed service** – No upfront cost of installations, no hassles of routine security, maintenance, updates, and patches.
* **Easily set up and deploy your server** within minutes. Azure Database for MYSQL provides two popular deployment models – Single server deployment for existing workloads and **Flexible Server Deployment** which gives you more granular control of the database.
* **Get intelligent insights** – Get customized recommendations to improve database performance.
* **Pay-as-you-go** – Pay only for servers that you use. You can easily provision servers, scale up, and change your pricing tier whenever needed.

Azure Database for MySQL
supports two different deployment options:
* **Azure Database for MySQL - Single Server**, the first deployment option we introduced,
automatically handles most database management functions, including patching, backups, and
security—with minimal user configuration and control.
* **Azure Database for MySQL - Flexible Server** provides new innovations that go beyond what’s in Single Server, including greater flexibility and more granular control over database configuration and management. Flexible Server also provides additional cost optimization controls, including a burstable compute pricing tier and the ability to start and stop the server for development or test scenarios—and only pay for storage while the database is stopped. Flexible Server is recommended for most new Azure Database for MySQL deployments, including migrations from on-premises or VM-based (IaaS) MySQL environments and new cloud-native apps.

### To connect to Mysql using the Azure CLI
After the database has been created,
Click on the `Goto resource`.
On the `settings` bar, click on `Connection security`.
On the **Firewall rules**, `eneble` allow access to Azure services.
On the SSL settings, `disable` enforce ssl connection.
Select Add current client IP address, and then select `Save`.
Goto `Overview`.
Goto your Azure CLI.
Type,

    mysql --host=<server name> --user=<server admin login name> -p
Press Enter.
Enter your password and you are into the database.



### What is SSL
**SSL Definition**
SSL is short for secure socket layer - a technology that encrypts communication between users and a website. This encryption ensures that important data such as usernames, passwords, and credit card information is sent from the user to the site without the risk of interception.

An SSL certificate is a certified piece of code on a website that binds this encryption to the organization responsible for the website.

An SSL-certified website runs on https protocol. This activates the browser padlock or a prominent green browser bar to show visitors it is safe to browse. Reputable websites use SSL to protect their customer’s data and their online transactions; their reputation depends on it.



## To Create a Database for mysql
**Step-1**
View databases that are available

    show databases;
Step-2
Create your database

    create database < database name >;

Step-3
Use the databases that you created

    use < database name >;

Step-4
Create your table and insert columns

    create table < table name > (
    std_id int primary key,
    std_name varchar(50) not null,
    std_age int(5) not null,
    std_class varchar(20) not null
    );

Step-5
Insert values in the table

    insert into < table name > (
    std_id, std_name, std_age, std_class)
    values
    (1, "john", 14, "maths"),
    (2, "emeka", 12, "english"),
    (3, "ebuka", 15, "maths");

Step-6
Display how our table looks like

    select * from < table name >;

Step-7
To update our table

    update `book` set `std_name`='jason' where `std_id`=1

Step-8
To do multiple update

    update `book` set `std_name`='jason', `std_age`=13 where `std_id`=1

Step-9
To delete a value in our table

    delete from `book` where `std_id`=3

Step-10
To delete  a database

    drop database < database name >;