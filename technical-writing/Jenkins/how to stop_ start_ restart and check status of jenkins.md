## How to stop, start, restart and check status of Jenkins

Jenkins by default starts running when installed. Here are the commands to start, stop, restart, and check the status of the Jenkins service:

1. To start Jenkins, use the following command:

        sudo systemctl start jenkins 
    
2. Similarly, to stop Jenkins, use the following command:

        sudo systemctl stop jenkins 

3. To restart Jenkins, use the following command:

        sudo systemctl restart jenkins 

4. To check the status of the Jenkins service, use the following systemctl command:

        sudo systemctl status jenkins 

You should see the following output:

     ● jenkins.service - LSB: Start Jenkins at boot time Loaded: loaded (/etc/init.d/jenkins; bad; vendor preset: enabled) Active: active (exited) since Wed ...