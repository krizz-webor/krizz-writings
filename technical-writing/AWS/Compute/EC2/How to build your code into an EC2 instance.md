## How to build your code into an EC2 instance
Setup EC2 instance.
* Connect to the EC2 instance.
* Goto your github to generate a deploy key, goto the project, click on **Settings** on the project.
* Click on **Deploy keys**.
* Goto your terminal, type: `cd .ssh`
* Paste: `ssh-keygen -t ed25519 -C "<your email address.>"`. Press **Enter** button.
* Enter a file name to save the key and remember the file name too.
* Type: `ls`, to view the list and type: `sudo vim <filekey with .pub>`. Copy the entire key and exit by typing `:q`
* Go back to github, click **Add deploy key**, give a title and paste the key copied on your terminal on the key and click **Add key** below.
* Go back to your code on github, click on **Code**, copy the url to clone it in your terminal.
* Type `cd ..` to exit the ssh folder.
* Type `git clone <paste the url of the github project> <a folder name>`.
* Type `ls` and cd into the folder.

**Install node.js**
    
* Goto google and  type: `node js nodesource`. scroll down to choose the appropriate version you want.
* Copy and paste the codes on your terminal
* Type: `npm install`. to install all the dependencies needed.
* Type: `cd src`.To cd into source and run npm install too. Then type `cd ..` to exit src
   
 **Install Nginx**

* Type: `sudo apt install nginx`
* Type `cd src`, type `npm run build` to build the front end app
* Create a new directory by typing `sudo mkdir /var/www/<folder name>`.
* Type  `sudo chown -R $USER:$USER /var/www/<folder name>` to own that directory.
* Type `cd ..` to exit src. Type `cp -r build/* /var/www/<folder name>` 
* Type `cd /etc/nginx`. Then type `ls`. Then type `cd sites-available/`. then type `ls`.
* Type `sudo vim default` to edit the default file
* Scroll down to **root /var/www/html**; and add your file as **root /var/www/<file name>**;
* Scroll down again to 

      location / {
                      # First attempt to serve request as file, then
                      # as directory, then fall back to displaying a 404.
                      try_files $uri /index.html; 

then press **esc** button, type `:x` to save the default file.
* Type `sudo systemctl restart nginx` to restart nginx.
* Goto your AWS instance, copy the public address and paste it on new tab to display the app.