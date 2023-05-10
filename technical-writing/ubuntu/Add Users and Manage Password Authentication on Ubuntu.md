## Add Users and Manage Password Authentication on Ubuntu
Ubuntu, like any other Linux distribution, is a multi-user operating system. Each user can have different permission levels and specific settings for various command-line and GUI applications.
Knowing how to add and remove users is one of the basic skills a Linux user should know.
In this tutorial, we will show you how to add and remove users on Ubuntu 20.04.
## Prerequisites
To be able to create and remove users, you need to be logged in as root or user with sudo privileges .

**How To Add User in Ubuntu**

One can create a new user account in Ubuntu in two ways:
From the command line.
Through the GUI.
### Add a New User from the Command Line
In Ubuntu, there are two command-line tools that you can use to create a new user account: useradd and adduser.
useradd is a low-level utility for adding users, while the adduser a friendly interactive frontend to useradd written in Perl.
To create a new user account named username using the adduser command you would run:

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
    PasswordAuthentication yes
After making that change, restart the SSH service by running the following command as root:

`sudo service ssh restart`

## Enable Logging In as root
Some providers also disable the ability to SSH in directly as root. In those cases, they created a different user for you that has sudo privileges (often named ubuntu). With that user, you can get a root shell by running the command:

`sudo -i`

If you instead want to be able to directly SSH in as root, again edit this file:

`/etc/ssh/sshd_config`

And change the line
    PermitRootLogin no
to
    PermitRootLogin yes
    
After making that change, restart the SSH service by running the following command as root:

`sudo service ssh restart`

If you enable this setting, don’t forget to set a strong password for root by running the command.

`sudo passwd root`
## Resources
1. How to Enable SSH Password Authentication
2. How to Add and Delete Users on Ubuntu 18.04
3.
serverpilot.ioserverpilot.io

**How to Enable SSH Password Authentication - ServerPilot**
Some server providers, such as Amazon EC2 and Google Compute Engine, disable SSH password authentication by default. That is, you can only log in over SSH using public key authentication.