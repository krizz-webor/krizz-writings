## Basics
Docker­-Co­mpose: is a tool for defining and running multi-­con­tainer Docker applic­ations. With Compose, you use a YAML file to configure your applic­ation’s services. Then, with a single command, you create and start all the services from your config­ura­tion.
Need to good to yml file directory to succes­sfully run the docker­-co­mpose commands.


    docker­-co­mpose start wordpr­ess_db

it will only start 1 service
but

    docker­-co­mpose start
    
will start all the services. Similar is the case with other commands.

**Start an existing service container.**

    docker­-co­mpose start

**Stop an existing service container**

    docker­-co­mpose stop
    
    -t, --timeout
    specify a shutdown timeout in second­s
    
Stops running containers without removing them. They can be started again with docker­-co­mpose start.

**Pause running containers of a service**

    docker­-co­mpose pause

**Unpause paused containers of a service**

    docker­-co­mpose unpause

**Restart all stopped and running services**

    docker­-co­mpose restart

**Show list of containers for a service**

    docker­-co­mpose ps

     -q, --quiet
    Only display IDs

**Displays log output from services**

    docker­-co­mpose logs

    -f, --follow
    Follow log output.

**View the processes running within each service container**

    docker­-co­mpose top

**Remove stopped service contai­ners**

By default, anonymous volumes attached to containers are not removed. You can override this with `-v`.

To list all volumes, use `docker volume ls`.
-f, --force – Don’t ask to confirm the removal
-s, --stop – Stop the contai­ners, if required, before removing
-v – Remove any anonymous volumes attached to containers

    docker­-co­mpose rm

**Prints the version of docker­-co­mpose**

    docker­-co­mpose version

**Push images for services to their respective regist­ry/­rep­ository**

    docker­-co­mpose push

**Validate and view the Compose file**

    docker­-co­mpose config

**Forces running containers to stop by sending a SIGKILL signal**

    docker­-co­mpose kill

**Only builds the images, does not start the contai­ners**

    docker­-co­mpose build

## docker­-co­mpo­se.yml file

    version: "3.7"
    services:
      wordpress_db:
        container_name: "wordpress_db"
        image: "mysql:5.7"
        volumes:
          - ~/dockers/wordpress/.data/wordpress_db:/var/lib/mysql
        environment:
          MYSQL_USER: gaurav
          MYSQL_PASSWORD: victory
          MYSQL_DATABASE: db
          MYSQL_RANDOM_ROOT_PASSWORD: '1'
        networks:
          - wordpress_network
        ports:
          - 3307:3306
      wordpress_web:
        container_name: "wordpress_web"
        image: "wordpress"
        volumes:
          - ~/dockers/wordpress/.data/wordpress_web:/var/www/html
        environment:
          WORDPRESS_DB_HOST: wordpress_db
          WORDPRESS_DB_USER: gaurav
          WORDPRESS_DB_PASSWORD: victory
          WORDPRESS_DB_NAME: db
        networks:
          - wordpress_network
        ports:
          - 8080:80
        depends_on:
          - wordpress_db
    networks:
      wordpress_network:


**docker­-co­mpose up** is used to start a project. It tries to automate a series of operations including building a mirror, (re)cr­eating a service, starting a service, and associ­ating a servic­e-r­elated container.
It also builds the images if the images do not exist and starts the contai­ners:

    docker­-co­mpose up                     use docker­-co­mpo­se.yml
    docker­-co­mpose -f <fi­len­ame.ym­l> -f   use custom yml files
    <fi­len­ame­loc­al.y­ml> up
              
    -d, --detach                          background detached mode
    --build                               forcefully Build images before starting contai­ners.
    --no-build                            skips the image build process
    --forc­e-r­ecreate                      Recreate containers even if their config­uration and image haven’t changed.
    --no-color                            Produce monochrome output.
    --scale SERVIC­E=NUM                   Scale SERVICE to NUM instances. Overrides the scale setting in the Compose file if present.