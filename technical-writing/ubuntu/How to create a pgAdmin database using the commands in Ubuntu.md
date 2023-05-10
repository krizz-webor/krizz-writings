## How to create a pgAdmin database using the commands in Ubuntu

To create a database, click on the arrow close to the servers.
* Right-click on the databases, goto create and click on Database.
* Give it a name, you can select the user, by clicking on the owner row. Then click on save.
* To ccreate a Table, right-click on the database thatn you want to draw the atble on, goto Querry Tool on the scroll.
* On the Querry, type: N/B: For the columns.
1. CREATE TABLE <table name>(
2.    std_id INT PRIMARY KEY,
3.    std_name VARCHAR(240) NOT NULL,
4.    std_course VARCHAR(240) NOT NULL,
5.    std_stream VARCHAR(240)
6.);      Press F5 or the Execution button that looks like a play button at the top of the screen, for execution.
*. Next, is to create the rows. After pressing the Execution button, clear the terminal by highlighting and deleting everything.
*. Type:
1. INSERT INTO <name of database>
2.    (std_id, std_name, std_course, std_stream)
3.    VALUES
4.    (1, "Stan", "Eng 201", "mind")
5.    (2, "Chris", "Maths 201", "mind")
6.    (3, "Edu", "Eng 202", "mind")
7. ;        Then press then Execution button to execute.
*.  To view the table that was created, type "SELECT * FROM <table name>;    then click on execute icon.