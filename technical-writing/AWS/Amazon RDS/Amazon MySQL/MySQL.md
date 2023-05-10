# MySQL
MySQL is the world’s most used and popular relational database, and Amazon RDS provides an easy way to set-up, operate, and scale. You can use the code which you are writing because RDS for MySQL covers all versions of MySQL.

It is an open source database management system which uses SQL (Structured Query Language) to access the data stored in its system.

**Pricing**
* Database Storage: $0.115/GB/month
* Backup Storage: $0.095/GB/month

## Creating a MySQL RDS Instance

### Using AWS management Console

AWS management console is the most convenient way to get started with RDS. You login to the AWS console using your AWS account details, locate the RDS service and then follow the steps shown below to create a MySQL DB instance.

**Step-1**
Select the MSSql Engine form the console.
![create_mysqldb_step_1](https://www.tutorialspoint.com/amazonrds/images/create_mysqldb_step_1.jpg)

**Step-2**
Specify the required DB details.
![create_mysqldb_step_3](https://www.tutorialspoint.com/amazonrds/images/create_mysqldb_step_3.jpg)

**Step-3**
In this step you decide on the db instance class, amount of storage allocated also set the master password along with few other details.
![create_mysqldb_step_4](https://www.tutorialspoint.com/amazonrds/images/create_mysqldb_step_4.jpg)

**Stpe—4**
The final step is to click create database, after which the MySql DB is created with a available end point as shown below.
![connecting_mysql_1](https://www.tutorialspoint.com/amazonrds/images/connecting_mysql_1.jpg)

## Connecting It to Your MySQL Shell
**Step-1**

Open your MySQL shell, and paste the command with your username, endpoint, and port number. Once you hit Enter, your password will be needed
![1.1](https://intellipaat.com/blog/wp-content/uploads/2019/05/1.1.png)

After entering the password, you would be logged in.
![1.2](https://intellipaat.com/blog/wp-content/uploads/2019/05/1.2.png)

Now, check whether the database which you created while creating the instance exists. Start using it as a local MySQL database
![1.3](https://intellipaat.com/blog/wp-content/uploads/2019/05/1.3.png)

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
To delete a table

     drop table [dbo].[books]