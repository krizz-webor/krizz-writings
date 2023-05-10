## How to Install Mysql in Ubuntu
Firstly, you have to update your system software

    sudo apt update

Then install the `mysql-server` package:

    sudo apt install mysql-server

Ensure that the server is running using the `systemctl start` command:

    sudo systemctl start mysql.service