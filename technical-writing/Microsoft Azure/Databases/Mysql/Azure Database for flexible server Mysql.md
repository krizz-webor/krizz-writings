## Azure Database for Flexible Server Mysql
### How to connect to the database using the Azure CLI
After the database has been created,
Click on the `Goto resource`.
On the `settings` bar, click on `Server Parameters`.
On the Search bar, type, `require secure transport`.
Click on the `arrow bar` and switch it to `OFF`.
Then click `save`.
Goto `Overview`.
Goto your Azure CLI.
Type,

    mysql -h <server name> -u <Server admin login name> -p
Hit `Enter`.
Then type your password.
