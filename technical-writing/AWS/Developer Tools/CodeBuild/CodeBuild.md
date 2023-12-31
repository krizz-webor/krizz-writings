# CodeBuild

### Create a simple index.html file in CodeCommit Repository.
We would have to build an index.html using nginx server

Create a code commit repository

Copy clone HTTPS url

In git bash, clone the repository to your local machine using the git clone command.

Inside code commit repository create an index.html file

Save the file and commit the changes to the repository using the git add and git commit commands.

    git add <file-name>

    git commit -m "commit message"

Push the changes to the repository using the git push command.

    git push origin master

You have a simple index.html file in your CodeCommit repository

### Add buildspec.yaml file to CodeCommit Repository and complete the build process.
Create a Buildspec file to build the file using an nginx server.

buildspec.yml file

    version: 0.2
    
    phases:
      install:
        commands:
          - echo Installing Nginx
          - sudo apt-get update
          - sudo apt-get install nginx -y
    
      build:
        commands:
          - echo build started on 'date'
          - cp index.html /var/www/html
    
      post_build:
        commands:
          - echo Configuring NGINX
    
    artifacts:
      files:
        - /var/www/html/index.html

### Here's what each step of the build does:
**version**: 0.2 specifies the version of the Buildspec syntax we're using.

**phases** contains the build phases for our project.

**install**: Installs nginx on the build environment using the apt-get package manager.

**build**: Copies the index.html file to the default web root directory for nginx.

**post_build**: Performs any additional configuration for nginx, if necessary.

**artifacts**: Specifies the location of the index.html file to be included in the build artifact.

Save the file and commit the changes to the repository using the git add and git commit commands.

Push the changes to the code commit repository

You have a buildspec.yml and index.html file in your CodeCommit repository

## Create build project:
Go to the CodeBuild service. Click the `Create build project` button.

![1*uqZsBMsnSNAbNZPg4lpjgQ](../../../../media/1%2AuqZsBMsnSNAbNZPg4lpjgQ.png)

Fill in the details of your build project, including the project name, source provider (CodeCommit), repository, and branch.

In source section, select source provider AWS CodeCommit, select Repository that you created earlier and select branch master.

![1*O-WTZhWsBGW0gQ-ovAvmIg](../../../../media/1%2AO-WTZhWsBGW0gQ-ovAvmIg.png)

In Environment section, choose operating system, runtime(standard) and image(aws/codebuild/standard)

![1*Gm_6sMsaeE9KsbxCbZzmNw](../../../../media/1%2AGm_6sMsaeE9KsbxCbZzmNw.png)

Create a new service role and Under the `Buildspec` section, choose `Use a buildspec file`.

Click `Create build project` to create your project.

Successfully build project is created.

Click the `Start build` button to start a new build.

Check status of build which is Succeeded.

### To add artifacts to a CodeBuild project and store them in an S3 bucket.

First create S3 bucket.

Give the bucket a unique name. Bucket is successfully created.

Go back to CodeBuild, In artifact, Click on `edit` and select 'Artifacts'.

In `Edit Artifacts`, select type Amazon S3 and select bucket name that you created in above step.

![1*X4iEI_wZElcneXbhQnUPpQ](../../../../media/1%2AX4iEI_wZElcneXbhQnUPpQ.png)

Click on `Update artifacts`.

After updating artifacts, click the `Start build` button again to start a new build.

After the build process is complete, the artifacts will be uploaded to the specified S3 bucket location.

In buildspec.yml file, inside artifacts phase there is a location of file which is /var/www/html/index.html. you can check that folders and index.html file inside s3 bucket.

Inside bucket, demo_build folder is created.

You can see inside /var/www/html there is index.html file.

Click on `index.html` file, below you can see properties of file.

Click on `open` on right-hand side to view the output of the project
