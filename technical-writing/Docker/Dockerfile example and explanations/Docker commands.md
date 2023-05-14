## Dockerfile commands
### Docker Commands
1. **docker --version**

This command is used to get the currently installed version of docker
![Docker_Version-Docker-Commands-Edureka-3-e1510653973130](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/Docker_Version-Docker-Commands-Edureka-3-e1510653973130.png)

2. **docker pull**

Usage: **docker pull < image name >**
Let’s say you need to pull the docker image from dockerhub
This command is used to pull images from the docker repository(hub.docker.com)
The following example of pulling an Ubuntu image.
![Docker_Pull-Docker-Commands-Edureka-2-e1510653950923](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/Docker_Pull-Docker-Commands-Edureka-2-e1510653950923.png)

3. **docker run**

Usage: **docker run -it -d < image name >**
This command is used to create a container from an image.
This command is going to run the container in an interactive mode and a detached mood. That means that the process would run in the background and not be seen.
![docker_run-Docker-Commands-Edureka-e1510653910376](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/docker_run-Docker-Commands-Edureka-e1510653910376.png)

4. **docker ps**

This command is used to list the running containers with container details.
![docker_ps-Docker-Commands-Edureka-e1510653881541](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/docker_ps-Docker-Commands-Edureka-e1510653881541.png)

5. **docker ps -a**

This command is used to show all the running/stopped and exited containers with container details.
![docker_psa-Docker-Commands-Edureka-e1510653854892](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/docker_psa-Docker-Commands-Edureka-e1510653854892.png)

6. **docker exec**

Usage: **docker exec -it < container id> bash**

This command is used to access the running container and run commands inside the container.

![docker_exec-Docker-Commands-Edureka-e1510653829237](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/docker_exec-Docker-Commands-Edureka-e1510653829237.png)

7. **docker stop**

Usage: **docker stop < container id>**

This command stops a running container

![docker_stop-Docker-Commands-Edureka-e1510653793521](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/docker_stop-Docker-Commands-Edureka-e1510653793521.png)

8. **docker kill**

Usage: **docker kill < container id>**

This command kills the container by stopping its execution immediately. The difference between ‘`docker kill`’ and ‘`docker stop`’ is that ‘`docker stop`’ gives the container time to shutdown gracefully, in situations when it is taking too much time for getting the container to stop, one can opt to kill it
![docker_kill-Docker-Commands-Edureka-e1510653772661](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/docker_kill-Docker-Commands-Edureka-e1510653772661.png)

9. **docker commit**

Usage: **docker commit < conatainer id> < username/imagename >**

This command creates a new image of an edited container on the local system
![docker_commit-Docker-Commands-Edureka-e1510653734760](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/docker_commit-Docker-Commands-Edureka-e1510653734760.png)

10. **docker login**

This command is used to login to the docker hub repository![docker_login-Docker-Commands-Edureka-1-e1510653706645](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/docker_login-Docker-Commands-Edureka-1-e1510653706645.png)

11. **docker push**

Usage: **docker push < username/image name >**

This command is used to push an image to the docker hub repository
![docker_push-Docker-Commands-Edureka-e1510653678749](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/docker_push-Docker-Commands-Edureka-e1510653678749.png)

12. **docker images**

This command lists all the locally stored docker images
![docker_images-Docker-Commands-Edureka-e1510653647888](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/docker_images-Docker-Commands-Edureka-e1510653647888.png)

13. **docker rm**

Usage: **docker rm < container id >**

This command is used to delete a stopped container
![docker_rm-Docker-Commands-Edureka-e1510653622699](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/docker_rm-Docker-Commands-Edureka-e1510653622699.png)

14. **docker rmi**

Usage: **docker rmi < image-id >**

This command is used to delete an image from local storage
![docker_rmi-Docker-Commands-Edureka-e1510653592230](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/11/docker_rmi-Docker-Commands-Edureka-e1510653592230.png)

15. **docker build**

Usage: **docker build -t < name:tag > .**
This command is used to biuld an image(customize) by giving it a name, which is very important so that you can be able to differentiate your images.