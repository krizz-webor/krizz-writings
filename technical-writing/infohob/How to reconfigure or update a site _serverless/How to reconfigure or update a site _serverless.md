## How to reconfigure or update a site (serverless)
Things to do

1. Clone the project in the Github repository
2. Copy and paste the Docker and Jenkinsfile into the project that was cloned
3. Since the Jenkinsfile has conf. files, copy and paste the conf. folder into the cloned project
4. Create a job for the project in Jenkins and configure it using an existing credential
5. Goto Github and create a webhook for the project and Jenkins
6. Allow just `push` and `pull` request for auto-deployment
7. Check the jenkinsfile to know if the port assigned is free to use
8. Deploy the project to Github and check in Jenkins to see if the project was successfully deployed else, check the problem
9. Goto AWS EC2 and check the server that has Nginx installed in it
10. Goto Route 53 and configure the IP and record set of the server that you want to use for the project
11. SSH into the server with the Nginx configuration, create a file in the Nginx sites-available and create an Nginx configuration without the letsencript configuration
12. Symlink the file to sites-enabled
13. Check if the configutation is correct using

        sudo nginx -t

14. Restart Nginx
15. Goto EC2 and add security group for the project
16. Check the site connection using `curl`
17. If the result was positive, check the site using the domain name you created in Route 53
18. Install letsencript and check the URL for the secure site