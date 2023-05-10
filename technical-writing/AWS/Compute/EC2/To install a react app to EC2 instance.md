## To install a react app to EC2 instance
Create an EC2 intance and launch.

Wait till it starts running.

Mark it and click on **connect**.

Goto your ternimal and locate the instance key.

On your SSH client in your EC2 instance, copy the "chmod 400" stuff and paste it on your terminal.

Also copy the "ssh -i" stuff and paste it on your terminal to get access to your EC2 instance on your terminal.

Install Node.js environmemt in your EC2 instance, goto your browser and search for "EC2 node setup".

When it opens, click on the "docs.aws.amazon.com" page and follow the command prompt.

Goto the repo. on your Github, click on the "code" with a green background. it will open a clone stuff.

Copy the address and goto to your terminal. Type `git clone` make a space and paste the address you copied.

Change directory to the react app you want to install. (cd into the directory), by typing `ls` and then `cd` into the directory

Install Nginx by typing `sudo apt install nginx`

Type `npm install -g npm@8.16.0`

Type `npm start` to get the address to the instance on a browser.

The address is shown as localhost. copy the "3000" or whatever number it gives.

Goto your EC2 instance, click on the `instance id`, click on `security`. Click on the link in the "security groups".

Click on `Edit inbound rules`, click on `Add rule` and on the port range, type the number given the terninal.

On the `Source info`, give the `0.0.0.0/0`.

Add another rule with same number given but on the Source info, give the `::/0` and save rules.

Copy the `Public IPv4 address`, goto your browser, paste the address there, add "`:`" and the number given in the terminal and press enter.

If you're faced with npm i react-scripts

npm install -g npm@8.16.0

sudo netstat -tulpn