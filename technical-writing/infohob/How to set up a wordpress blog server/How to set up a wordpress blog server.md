## How to set up  a wordpress blog server
Things to do

1. Create an Ubuntu instance(t3.small)
instance Name:(wordpress), image:(ubuntu 22), key-pair:(infohub.pem), VPC:(infohob-vpc), subnet:(public-subnet-01)
2. Create a DNS for the blog using Route 53 as sub domain.
3. ssh into the instance, 
4. udate the instance
 
       sudo apt update

5. Create a user(deploy)
* Create ubuntu user

      sudo adduser <username>
      sudo usermod -aG sudo <username>

* Permit user to perform sudo without password
      
      sudo nano /etc/sudoers
      # Allow <username> user to execute any command
      <username>  ALL=(ALL) NOPASSWD:ALL

* Enable password login
* 
      sudo nano /etc/ssh/sshd_config
      PasswordAuthentication yes
      **SET**
      sudo service sshd restart 

**N/b**: **Paste** 
(# Allow deploy user to execute any command
       deploy  ALL=(ALL) NOPASSWD:ALL)
       
Below
%sudo ALL=(ALL:ALL) ALL

**LIKE THIS**
%sudo ALL=(ALL:ALL) ALL

(# Allow deploy user to execute any command
       deploy  ALL=(ALL) NOPASSWD:ALL)

Remove the open and close bracket at the start and end of the # Allow

Then save.

If you have been logged out of the server and you want to log in, use,

    ssh -i PrivateKey <user>@ipaddress

6. Create a folder in that directory and name it  wordpress

7. Create a file name docker-compose.yml in the folder(wordpress)
8.  Add these to the docker-compose.yml file

        version: '3.1'
        services:
          
         wordpress:
            image: wordpress:latest
            restart: always
            ports:
              - 8085:80
            environment:
              WORDPRESS_DB_HOST: mysql-db
              WORDPRESS_DB_USER: dp_wordpress_prod
              WORDPRESS_DB_PASSWORD: your-password
              WORDPRESS_DB_NAME: db-name
            volumes:
              - wordpress:/var/www/html
        
        volumes:
          wordpress:
      
9. Install docker and docker compose in  the server

       sudo apt update
        
       sudo apt install apt-transport-https ca-certificates curl software-properties-common
        
       curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
        
       sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
        
       apt-cache policy docker-ce
        
       sudo apt install docker-ce
        
       sudo systemctl status docker
        
       # install docker compose
        
       sudo apt-get update
       
       sudo apt-get install docker-compose-plugin
       
       # Verify that Docker Compose is installed correctly by checking the version.
        
       docker compose version        
        

10. Add user to the docker group
* Create the docker group.

      sudo groupadd docker

* Add your user to the docker group.

      sudo usermod -aG docker <USER>

You can list the members of the docker group to confirm that the jenkins user has been added successfully:

    grep docker /etc/group

11. Create a serverless aurora mysql db for the wordpress.
instance name:(infohob-mysql), Username: (infohob_prod_user)
12. Install MySQL in the server
* Update the server

      sudo apt update

* Then install the mysql-server package

      sudo apt install mysql-server

* Ensure that the server is running using the systemctl start command

      sudo systemctl start mysql.service

13. Log into the database and create a user(wordpress_user)

You can log into the database using the terminal

    mysql -h <endpoint> -u <username> -p
    Then enter your password

    # To create user
    
    CREATE USER '<user>'@'%' IDENTIFIED BY '<password>';

Goto MySQL workbench and log in

    # To grant user privileges
    
    GRANT ALL PRIVILEGES ON *.* TO '<user>'@'%' WITH GRANT OPTION;
    
    # To confirm a user account's privileges
    
    SHOW GRANTS FOR '<user>'@'%';
    
13. Exit the database and login again using the user that you created and granted privilege as the username for the login
14. Also create a database so as to prove that the use has privilege to create database

        # create database
        
        CREATE DATABASE book;
        
        # delete the database
        
        DROP DATABASE book;

15. Input the values of the database in the docker-compose.yml file

        version: '3.1'
        services:
          
         wordpress:
            image: wordpress:latest
            restart: always
            ports:
              - 8085:80
            environment:
              WORDPRESS_DB_HOST: mysql-db
              WORDPRESS_DB_USER: dp_wordpress_prod
              WORDPRESS_DB_PASSWORD: your-password
              WORDPRESS_DB_NAME: db-name
            volumes:
              - wordpress:/var/www/html
        
        volumes:
          wordpress:

16. Save the file and run

        docker compose up -d

17. Test if it’s working fine 

        curl http://localhost:the-port-of-app

18. Run the command below to see if the container is running

        docker ps

19. To see the logs of the container, run

        docker logs id-of-the-container

20. Whenever you make a change in the docker-compose.yml file, restart the docker compose file

        docker compose restart

21. Visit the Wordpress on your browser

        Ip-of-the-server:port-of-Wordpress

22. Install nginx and do the configuration
23. Setting up certificates using Letsencrypt

        # Install Certbot and it’s Nginx plugin with `apt`:
        
         sudo apt install certbot python3-certbot-nginx
        
        # Obtain an SSL Certificate
        
         sudo certbot --nginx -d blog.infohob.com

If that’s successful, `certbot` will ask how you’d like to configure your HTTPS settings.

    Output
    Please choose whether or not to redirect HTTP traffic to HTTPS, removing HTTP access.
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    1: No redirect - Make no further changes to the webserver configuration.
    2: Redirect - Make all requests redirect to secure HTTPS access. Choose this for
    new sites, or if you're confident your site works on HTTPS. You can undo this
    change by editing your web server's configuration.
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    Select the appropriate number [1-2] then [enter] (press 'c' to cancel):

Select your choice then hit `ENTER`. The configuration will be updated, and Nginx will reload to pick up the new settings. `certbot` will wrap up with a message telling you the process was successful and where your certificates are stored:

    Output
    IMPORTANT NOTES:
     - Congratulations! Your certificate and chain have been saved at:
       /etc/letsencrypt/live/example.com/fullchain.pem
       Your key file has been saved at:
       /etc/letsencrypt/live/example.com/privkey.pem
       Your cert will expire on 2020-08-18. To obtain a new or tweaked
       version of this certificate in the future, simply run certbot again
       with the "certonly" option. To non-interactively renew all of
       your certificates, run "certbot renew"
     - If you like Certbot, please consider supporting our work by:
    
       Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
       Donating to EFF:                    https://eff.org/donate-le

Your certificates are downloaded, installed, and loaded. Try reloading your website using `https://` and notice your browser’s security indicator. It should indicate that the site is properly secured, usually with a lock icon.