## How to create a Mysql database using the commands in Ubuntu
First, log into your Mysql using the command:

    mysql -u root -p

and then enter password.
First, you create a database, using:

    CREATE DATABASE <database_name>;

To view the database that you just created, use:

    SHOW DATABASES;

This will list the databases that are present in your machine including the one you created.
To enter into the database and create your database, use:

    USE <database_name>;

You will get a response of `Database changed`.

To create a table, use:

    CREATE TABLE <table_name>(
    book_id INT PRIMARY KEY,
    book_name VARCHAR (50) NOT NULL,
    book_course VARCHAR (50) NOT NULL,
    book_stream VARCHAR (50) NOT NULL);

To view the database, use:

    DESCRIBE <table_name>;
To insert values to the table that we created, use:

    INSERT INTO <table_name> VALUE
    (1, "stan", "phsics", "mind"),
    (2, "obi", "chemistry", "mind"),
    (3, "chris", "biology", "mind");

To view the table that you have created including the values that was inserted, use:

    SELECT * FROM <table_name>;

To delete the table that was created, use:

    DROP TABLE <table_name>;

To delete the database that was created, use:

    DROP DATABASE <database_name>;


