# Steps to configure an Application load balancer in AWS for multiple EC2 instances

### Task 1

Launch 2 EC2 instances with an Ubuntu AMI and use user data to install the Apache Web Server.
* Go to the EC2 dashboard after logging in to your Amazon Console.
* Then, choose "Ubuntu Server" by clicking the "Launch Instance" button.
* Choose an instance type, set up the instance's specifics, add storage, and set up security groups as necessary.
* Expand the "User data" column on the "Configure Instance Details" page by scrolling down to the "Advanced Details" section.
* Enter the following commands to install and launch the Apache web server in the "User Data" field:

      #!/bin/bash
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo sysyemctl start apache2
      sudo sysyemctl begin apache2

* Do same for the second instance
* Connect your ec2 instance with SSH

**Use the command below to check the status of Apache 2:**

    sudo systemctl status apache2

* Go inside /var/www/html path and edit index.html file

      cd /var/www/html
      
      # To view the file inside the html folder
      ls
      
      # To edit the content of the file
      nano index.html

* Change the paragraph statement to your desired choice
* To save the configuration, press

      ctrl X
      Y
      Enter

* Do same for the other instance

N/B: The paragraph change, does not have to be the same so that we can differentiate between traffics on both servers

* Copy the public IP address and paste it into the address bar of a web browser.
* A webpage with details about your PHP installation ought to appear.

### Task 2

Create an Application Load Balancer (ALB) in EC2 using the AWS Management Console.

We will first construct the Target group that needs to be connected to the load balancer before creating the load balancer.
* Go to the `Target group`
* Choose `instance` as the target
* Select the traffic routing protocol", leaving it at HTTP Port 80
* Hit on the `create target group`
* Add the two instances in the target group
* Click `Create target group`

### Now we will create the load balancer
* Click on `Load Balancers` in the left-hand navigation menu and then click the `Create Load Balancer` button
* Select `Application Load Balancer` as the load balancer type and click `Create`.
* Please provide the necessary information, such as the load balancer name, IPv4 protocol, and internet-facing, as we are not currently using SSL certificates to encrypt our communication.
* Select the AZ for your EC2 instance for high availability
* Choose security group if you specified any
* In the listener, section attaches the target group that you have created previously

You can now copy the DNS of your load balancer and paste it into your browser to see different webpages when you repeatedly refresh the page, which indicates that your target audience is sending traffic to your EC2 instances.
