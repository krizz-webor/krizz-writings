## How to configure Nginx Configuration for an EC2 instance and giving it a Domain name in Route 53

**Launch an EC2 instance**: 

First, launch an EC2 instance on AWS with your desired operating system. Make sure that it has an elastic IP address attached to it.

**Create an Elastic IP**: To ensure that your EC2 instance maintains a consistent public IP address, you should allocate an Elastic IP address to it.

You can do this by navigating to the EC2 console, selecting `Elastic IPs` from the sidebar, and clicking `Allocate new address`.

Once an Elastic IP address is allocated, you need to associate it with your EC2 instance. 

**Configure security groups**:

You need to configure the security group for your EC2 instance to allow HTTP/HTTPS traffic.

You can do this by adding inbound rules to your security group to allow traffic on port 80 (HTTP) and 443 (HTTPS).

Once your instance is running, you can connect to it using SSH.

**Install Nginx**: 

Next, install Nginx on your EC2 instance using the package manager for your operating system. For example, if you are using Ubuntu, you can use the following command:

    sudo apt-get update
    sudo apt-get install nginx
    sudo systemctl start nginx
    sudo systemctl enable nginx

**Adjusting the Firewall**:

Before testing Nginx, the firewall software needs to be adjusted to allow access to the service. Nginx registers itself as a service with `ufw` upon installation, making it straightforward to allow Nginx access.

List the application configurations that `ufw` knows how to work with by typing:

    sudo ufw app list

You should get a listing of the application profiles:

    Output
    Available applications:
      Nginx Full
      Nginx HTTP
      Nginx HTTPS
      OpenSSH
As demonstrated by the output, there are three profiles available for Nginx:

**Nginx Full**: 

This profile opens both port 80 (normal, unencrypted web traffic) and port 443 (TLS/SSL encrypted traffic)

**Nginx HTTP**: 

This profile opens only port 80 (normal, unencrypted web traffic)
**Nginx HTTPS**: 

This profile opens only port 443 (TLS/SSL encrypted traffic)

It is recommended that you enable the most restrictive profile that will still allow the traffic you’ve configured. Right now, we will only need to allow traffic on port 80.

You can enable this by typing:

    sudo ufw allow 'Nginx HTTP'

You can verify the change by typing: 

    sudo ufw status

The output will indicate which HTTP traffic is allowed:

    Output
    Status: active
    To                         Action     From
    --                         ------      ----
    OpenSSH                    ALLOW       Anywhere                  
    Nginx HTTP                 ALLOW       Anywhere                  
    OpenSSH (v6)               ALLOW       Anywhere (v6)             
    Nginx HTTP (v6)            ALLOW       Anywhere (v6)
    
**Checking your Web Server**

At the end of the installation process, Ubuntu 20.04 starts Nginx. The web server should already be up and running.

We can check with the systemd init system to make sure the service is running by typing:

    systemctl status nginx

The output:

    Output
    ● nginx.service - A high performance web server and a reverse proxy server
       Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
       Active: active (running) since Fri 2020-04-20 16:08:19 UTC; 3 days ago
         Docs: man:nginx(8)
     Main PID: 2369 (nginx)
        Tasks: 2 (limit: 1153)
       Memory: 3.5M
       CGroup: /system.slice/nginx.service
               ├─2369 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
               └─2380 nginx: worker process

Goto config by typing to see the default configuration

    cd /etc/nginx/sites-availabled

Delete the default config file

    sudo rm -rf default

Create a new config in sites-available (eg. react)

    touch react

Add the new config to the file by typing:

    nano react

Copy and Paste the configuration below into the file

    server {
      listen 80 default_server;
      listen [::]:80 default_server;
      server_name localhost;
    
      location / {
        proxy_set_header HOST $host;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    
        proxy_pass http://127.0.0.1:3000;
      }
    }

Goto:

    cd /etc/nginx/sites-enabled

Delete the default config in sites-enabled by typing:

    sudo rm -rf default
    
Run the command below to symlink the new config file from sites-available to sites-enabled

    sudo ln -s /etc/nginx/sites-available/react /etc/nginx/sites-enabled/

Make sure to add the config file you created in the command to replace `react`

Test your configuration to be sure that it is working fine

    sudo nginx -t

Restart/reload the Nginx configuration

    sudo systemctl restart nginx

Confirm the status of the Nginx configuration
    
    sudo systemctl status nginx

**Create a record set in Route 53**:

Now that your EC2 instance is up and running with nginx, and you have an Elastic IP address associated with it, you can create a record set in Route 53 to associate your domain name with the Elastic IP address.

**To do this, follow these steps**:

In the Route 53 console, select the hosted zone for your domain name.

Click `Create Record Set`.

In the "`Name" field`, enter your domain name (e.g. example.com).

In the `Type` dropdown, select `A - IPv4 address`.

In the `Alias` dropdown, select `Yes`.

In the `Alias Target" field`, select your EC2 instance's Elastic IP address from the dropdown.

Click `Create` to save the record set.

That's it! Once you've completed these steps, your nginx server should be accessible via your domain name. Just enter your domain name in a web browser and you should see the nginx welcome page.