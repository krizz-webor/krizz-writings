## How To Set Up Continuous Integration Pipelines in Jenkins on Ubuntu 20.04

**Introduction**

Jenkins is an open source automation server intended to automate repetitive technical tasks involved in the continuous integration and delivery of software. With a robust ecosystem of plugins and broad support, Jenkins can handle a diverse set of workloads to build, test, and deploy applications.

## Add the Jenkins User to the Docker Group

After following the prerequisites, both Jenkins and Docker are installed on your server. However, by default, the Linux user responsible for running the Jenkins process cannot access Docker.

To fix this, we need to add the `jenkins` user to the `docker` group using the `usermod` command:

`sudo usermod -aG docker jenkins`

You can list the members of the `docker` group to confirm that the `jenkins` user has been added successfully:

`grep docker /etc/group`

    Output
    docker:x:999:sammy,jenkins
    
In order for the Jenkins to use its new membership, you need to restart the process:

`sudo systemctl restart jenkins`

If you installed Jenkins with the default plugins, you may need to check to ensure that the `docker` and `docker-pipeline` plugins are also enabled. To do so, click **Manage Jenkins** from the sidebar, and then **Manage Plugins** from the next menu. Click on the **Available** tab of the plugin menu to search for new plugins, and type `docker` into the search bar. If both `Docker Pipeline` and `Docker plugin` are returned as options, and they are unselected, select both, and when prompted, allow Jenkins to restart with the new plugins enabled.
This should take approximately a minute and the page will refresh afterward.

## Create a Personal Access Token in GitHub

In order for Jenkins to watch your GitHub projects, you will need to create a Personal Access Token in our GitHub account.

Begin by visiting GitHub and signing into your account if you haven’t already done so. Afterwards, click on your user icon in the upper-right hand corner and select **Settings** from the drop down menu.

On the page that follows, locate the **Developer settings** section of the left-hand menu and click **Personal access tokens**
Click on **Generate new token** button on the next page.
You will be taken to a page where you can define the scope for your new token.

In the **Token description** box, add a description that will allow you to recognize it later

In the **Select scope**s section, check the **repo:status**, **repo:public_repo** and **admin:org_hook** boxes. These will allow Jenkins to update commit statuses and to create webhooks for the project. If you are using a private repository, you will need to select the general **repo** permission instead of the repo subitems
When you are finished, click **Generate token** at the bottom.

You will be redirected back to the Personal access tokens index page and your new token will displayed.

Copy the token now so that we can reference it later. As the message indicates, there is no way to retrieve the token once you leave this page.
Now that you have a personal access token for your GitHub account, we can configure Jenkins to watch your project’s repository.

## Add the GitHub Personal Access Token to Jenkins

Now that we have a token, we need to add it to our Jenkins server so it can automatically set up webhooks. Log into your Jenkins web interface using the administrative account you configured during installation.

Click on your username in the top-right corner to access your user settings, and from there, click **Credentials** in the left-hand menu.

On the next page, click the arrow next to (**global**) within the **Jenkins** scope. In the box that appears, click **Add credentials**
You will be taken to a form to add new credentials.

Under the **Kind** drop down menu, select **Secret text**. In the **Secret** field, paste your GitHub personal access token. Fill out the **Description** field so that you will be able to identify this entry at a later date. You can leave the Scope as Global and the ID field blank.
Click the **OK** button when you are finished.

You will now be able to reference these credentials from other parts of Jenkins to aid in configuration.

## Set Up Jenkins Access to GitHub

Back in the main Jenkins dashboard, click **Manage Jenkins** in the left hand menu

In the list of links on the following page, click **Configure System**

Scroll through the options on the next page until you find the **GitHub** section. Click the **Add GitHub Server** button and then select **GitHub Server**

The section will expand to prompt for some additional information. In the **Credentials** drop down menu, select your GitHub personal access token that you added in the last section
Click the **Test connection** button. Jenkins will make a test API call to your account and verify connectivity
When you are finished, click the **Save** button to implement your changes