# Jenkins: How to create a slave agent

Create an EC2 instance, goto your timline, ssh into the instance. Next step is to create a user in that instance. Type:

`sudo adduser username`

    Output
        Adding user `username’ ...
        Adding new group `username’ (1001) ...
        Adding new user `username’ (1001) with group `username’ ...
        Creating home directory `/home/username’ ...
    Copying files from `/etc/skel’ ...

You will be asked a series of questions. The password is required, and all other fields are optional.

    Output
        Enter new UNIX password:
        Retype new UNIX password:
        passwd: password updated successfully
        Changing the user information for username
        Enter the new value, or press ENTER for the default
            Full Name []:
            Room Number []:
            Work Phone []:
            Home Phone []:
            Other []:
        Is the information correct? [Y/n]
Finally, confirm that the information is correct by entering Y.

The command will create the new user’s home directory, and copy files from /etc/skel directory to the user’s home directory. Within the home directory, the user can write, edit, and delete files and directories.
By default on Ubuntu, members of the group sudo are granted with sudo access.
If you want the newly created user to have administrative rights, add the user to the sudo group :

`sudo usermod -aG sudo username`

## Enable SSH Password Authentication
Some server providers, such as Amazon EC2 and Google Compute Engine, disable SSH password authentication by default. That is, you can only log in over SSH using public key authentication.
* SFTP is a protocol that runs over SSH, so this means SFTP using passwords will not work by default when SSH password authentication is disabled.
To enable SSH password authentication, you must SSH in as root to edit this file - /etc/ssh/sshd_config:

`sudo nano /etc/ssh/sshd_config`

Then, change the line
    PasswordAuthentication no
to
    PasswordAuthentication yes.

  To exit the config zone, press ctrl+X to save, `Y` to confirm save and `ENTER` key to exit.
After making that change, restart the SSH service by running the following command as root:

`sudo service ssh restart`

Grant permission to the remote user to be able to create files and folders

    sudo chmod -R 777 /home/ubuntu

To check if the user was added successfully,

    cat /etc/passwd

In ubuntu terminal check

    service ufw status

if active

    sudo service ufw stop



Next is to install Java and its dependencies on the instance.

## Installing the Default JRE/JDK

The easiest option for installing Java is to use the version packaged with Ubuntu. By default, Ubuntu 20.04 includes Open JDK 11, which is an open-source variant of the JRE and JDK.

To install this version, first update the package index:

    sudo apt update

Next, check if Java is already installed:

    java -version

If Java is not currently installed, you’ll see the following output:

    Output
    Command 'java' not found, but can be installed with:
    
    sudo apt install openjdk-11-jre-headless  # version 11.0.11+9-0ubuntu2~20.04, or
    sudo apt install default-jre              # version 2:1.11-72
    sudo apt install openjdk-13-jre-headless  # version 13.0.7+5-0ubuntu1~20.04
    sudo apt install openjdk-16-jre-headless  # version 16.0.1+9-1~20.04
    sudo apt install openjdk-8-jre-headless   # version 8u292-b10-0ubuntu1~20.04

Execute the following command to install the default Java Runtime Environment (JRE), which will install the JRE from OpenJDK 11:

    sudo apt install openjdk-11-jre

The JRE will allow you to run almost all Java software.

Verify the installation with:

    java -version

You’ll see output similar to the following:

    Output
    openjdk version "11.0.11" 2021-04-20
    OpenJDK Runtime Environment (build 11.0.11+9-Ubuntu-0ubuntu2.20.04)
    OpenJDK 64-Bit Server VM (build 11.0.11+9-Ubuntu-0ubuntu2.20.04, mixed mode, sharing))

You may need the Java Development Kit (JDK) in addition to the JRE in order to compile and run some specific Java-based software. To install the JDK, execute the following command, which will also install the JRE:

    sudo apt install default-jdk

Verify that the JDK is installed by checking the version of javac, the Java compiler:

    javac -version

You’ll see the following output:

    Output
    javac 11.0.11


    curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
      /usr/share/keyrings/jenkins-keyring.asc > /dev/null
      
    echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
      https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
      /etc/apt/sources.list.d/jenkins.list > /dev/null
      
    sudo apt-get update
    
    sudo apt-get install jenkins

You can enable the Jenkins service to start at boot with the command:

    sudo systemctl enable jenkins

You can start the Jenkins service with the command:

    sudo systemctl start jenkins

You can check the status of the Jenkins service using the command:

    sudo systemctl status jenkins

If you encounter

    jenkins.service: Failed with result 'exit-code

Check the server if there is any project running on port 8080

If there is a project running on port 8080, create another port for Jenkins serer and from anywhere

Go back to the terminal and type:

    sudo nano /usr/lib/systemd/system/jenkins.service

Change the jenkins port to the newly created port for the jenkins

Save the editor

Since we made changes on the jenkins configuration, we have to restart the jenkins config, type:

    sudo systemctl deamon-reload

Restart Jenkins

    sudo systemctl restart jenkins

Enable Jenkins

    sudo systemctl enable jenkins

Check Jenkins Status

    sudo systemctl status jenkins


### Unlocking Jenkins
When you first access a new Jenkins instance, you are asked to unlock it using an automatically-generated password.

Browse to http://localhost:8080 (or whichever port you configured for Jenkins when installing it) and wait until the Unlock Jenkins page appears.

Type `sudo cat <the path>`

Copy the code and paste

Install the required requirements

If faced with

    HTTP ERROR 403 No valid crumb was included in the request

Goto `Manage jenkins`

click on `Security`

scroll down to `CSRF Protection`

Tick `Enable proxy compatibility`

Click Apply and then Save

click on `Manage Jenkins`, 

Click on `Manage Nodes and Clouds`.

Then `New node`,

In the `Node name`, give it a name.

On the `Type`, tick `Permanent agent` and click `Create`.

On the `Root remote directory`, goto your 

timeline where your EC2 is still connected and 

type `pwd`.

Copy the root directory and paste it 

on the `Root remote directory` space.

Scroll down, on the` Launch method`, click on the space and select `Launch agent via SSH`.

For `Host`, goto your `EC2 instance`, copy the 
`public IPv4 address` and paste it.

Click on the `Add` on `Credentials`, click on 
`Jenkins`. Click on `Passwword and username` on 
`Kind`. Insert your password and username and 

click `Add`. Below the `Credentials`, click on 

the extension in the tab and select the 

credentials you created.

On `Host Key Verification Strategy`, click to

open and select Manually trustedkey Verification strategy. 

Scroll down and click `save` to complete the creation