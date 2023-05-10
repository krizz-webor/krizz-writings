# Infohob Documentation
​
## Team Members
​
Below are the current team members as at the time of this documentation:
​
* Tony Ayabam - Chief Executive Officer (CEO)
* Anande Theophilus - Project Manager
* Promise Chukwuenyem - DevOps Engineer
* Mamunur Rashid - Frontend Developer
* Hasinoor Rahman - Backend Developer
* Ukange Ushahemba - Tech Lead (Observer)
* Jasper Chukwuenyem - Junior DevOps Engineer
​
## GitHub
​
The organization account is **Infohob Technology Limited** which can be found here. However, the organization account is not very active, also, the repositories/projects within the organization account are no longer actively contributed to.
​
Active projects can be found under the **infohobtech** user account which can be accessed here - https://github.com/infohobtech?tab=repositories. Contributors are granted individual access to the projects. These are the list of active projects as at the time of this documentation:
​
* admin-recruiter-frontend - https://github.com/infohobtech/admin-recruiter-frontend
* infohob_frontend - https://github.com/infohobtech/infohob_frontend
* infohob_job_seeker - https://github.com/infohobtech/infohob_job_seeker
​
To add a collaborator to a repository simply login using the **webmaster** github credentials (do not use your personal account credentials since it's only **webmaster** that is the owner of the repositories).
​
Next:
* Go to the URL https://github.com/infohobtech?tab=repositories
* Select the repository that you want to add the collaborator/user to 
* When the repository opens, select **Settings*
* And then **Collaborators**
* Click on **Add people*
* And search the collaborator/user using their full name or username
* Invite the user and the when the user accepts the invitation they will added to the repository.
​
## Projects
​
We have 3 projects as at the time of this documentation:
​
* **admin-recruiter-frontend** - Admin Recruiter Dashboard (https://dashboard.infohob.com)
* **infohob_frontend** - Recruiter Frontend (https://infohob.com and https://www.infohob.com)
* **infohob_job_seeker** - Recruiter Backend (https://api.infohob.com)
​
## Servers
​
The AWS region in use is Europe (Frankfurt) [**eu-central-1**] and they can all be accessed using this URL: https://eu-central-1.console.aws.amazon.com/ec2/home?region=eu-central-1#Instances:instanceState=running
​
At the moment we are running 2 servers on the public subnet:
​
* **jenkins/jump** - Public IP (52.58.254.233)
* **infohob-app-server** - Public IP (3.127.104.45)
​
## SSL Certificates
​
At the moment we are using Letsencrypt for the Infohob.com SSL configuration. The service is free of charge.
​
It was installed on the app server (`3.127.104.45`) and is used by the Nginx web server for the SSL configuration.
​
The email address (used for urgent renewal and security notices) is webmaster@infohob.com.
​
The domain names that were setup for the SSL are:
* infohob.com
* www.infohob.com
* dashboard.infohob.com
​
The SSL certificate auto-renews using the Letsencrypt bot, so nothing needs to be to auto-renew the SSL certificates. However, you can confirm the status of the certificates by running the below command on the app server:
​
    sudo systemctl status certbot.timer
​
## DNS Configurations
​
Most of the DNS configurations are managed using **AWS Route 53** and can be accessed here - https://us-east-1.console.aws.amazon.com/route53/v2/hostedzones#
​
As at the time of this documentation the only hosted zones managed by **AWS Roue 53** is **infohob.com** and it's DNS records can be found here - https://us-east-1.console.aws.amazon.com/route53/v2/hostedzones#ListRecordSets/Z00447966CPLZNI7E3PL.
​
However, we also manage other DNS resources using:
* **Enom** - https://www.enom.com/
* **EUK Host** - https://eukhost.com/
​
The credentials can be gotten from Mr. Tony or the DevOps Engineer if need be.
​
## Email Server
​
The email server is managed by Google as we are using Google Suite email service which can be accessed here - https://admin.google.com
​
The credentials can be gotten from Mr. Tony or the DevOps Engineer if need be.