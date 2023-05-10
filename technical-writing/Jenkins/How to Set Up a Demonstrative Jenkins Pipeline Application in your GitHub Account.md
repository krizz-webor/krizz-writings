## How to Set Up a Demonstrative Jenkins Pipeline  Application in your GitHub Account

To demonstrate how to use Jenkins to test an application, we will be using a “[hello world](https://github.com/do-community/hello_hapi)” program created with [Hapi.js](https://hapi.dev/). Because we are setting up Jenkins to react to pushes to the repository, you need to have your own copy of the demonstration code.

Visit the [project repository](https://github.com/do-community/hello_hapi) and click the **Fork** button in the upper-right corner to make a copy of the repository in your account
A copy of the repository will be added to your account.

The repository contains a `package.json` file that defines the runtime and development dependencies, as well as how to run the included test suite. The dependencies can be installed by running `npm install` and the tests can be run using `npm test`.

We’ve added a `Jenkinsfile` to the repo as well. Jenkins reads this file to determine the actions to run against the repository to build, test, or deploy. It is written using the declarative version of the Jenkins Pipeline DSL.

  The `pipeline` contains the entire definition that Jenkins will evaluate. Inside, we have an `agent` section that specifies where the actions in the pipeline will execute. To isolate our environments from the host system, we will be testing in Docker containers, specified by the `docker` agent.

Since Hapi.js is a framework for Node.js, we will be using the `node` Docker image as our base. We specify the `root` user within the container so that the user can simultaneously write to both the attached volume containing the checked out code, and to the volume the script writes its output to.

Next, the file defines two stages, i.e., logical divisions of work. We’ve named the first one “Build” and the second “Test”. The build step prints a diagnostic message and then runs `npm install` to obtain the required dependencies. The test step prints another message and then run the tests as defined in the `package.json` file.

Now that you have a repository with a valid `Jenkinsfile`, we can set up Jenkins to watch this repository and run the file when changes are introduced.

## Create a New Pipeline in Jenkins

Next, we can set up Jenkins to use the GitHub personal access token to watch our repository.

Back in the main Jenkins dashboard, click **New Item** in the left hand menu

Enter a name for your new pipeline in the **Enter an item name** field. Afterwards, select **Pipeline** as the item type.
Click the **OK** button at the bottom to move on.

On the next screen, check the **GitHub project** box. In the **Project url** field that appears, enter your project’s GitHub repository URL.

Next, in the **Build Triggers** section, check the **GitHub hook trigger for GITScm polling** box
In the **Pipeline** section, we need to tell Jenkins to run the pipeline defined in the `Jenkinsfile` in our repository. Change the **Definition** type to **Pipeline script from SCM**.

In the new section that appears, choose **Git** in the **SCM** menu. In the **Repository URL** field that appears, enter the URL to your fork of the repository again

**Note**: Our example references a `Jenkinsfile` available within a public repository. If your project is not publicly accessible, you will need to use the add credentials button to **add additional** access to the repository. You can add a personal access token as we did with the hooks configuration earlier.
When you are finished, click the **Save** button at the bottom of the page.

## Performing an Initial Build and Configuring the Webhooks

Jenkins does not automatically configure webhooks when you define the pipeline for the repository in the interface. In order to trigger Jenkins to set up the appropriate hooks, we need to perform a manual build the first time.

In your pipeline’s main page, click **Build Now** in the left hand menu

A new build will be scheduled. In the **Build History** box in the lower left corner, a new build should appear in a moment. Additionally, a **Stage View** will begin to be drawn in the main area of the interface. This will track the progress of your testing run as the different stages are completed.

In the **Build Histor**y box, click on the number associated with the build to go to the build detail page. From here, you can click the **Console Output** button in the left hand menu to see details of the steps that were run
Click the **Back to Project** item in the left hand menu when you are finished in order to return to the main pipeline view.

Now that we’ve built the project once, we can have Jenkins create the webhooks for our project. Click **Configure** in the left hand menu of the pipeline

No changes are necessary on this screen, just click the **Save** button at the bottom. Now that the Jenkins has information about the project from the initial build process, it will register a webhook with our GitHub project when you save the page.

You can verify this by going to your GitHub repository and clicking the **Settings** button. On the next page, click **Webhooks** from the side menu. You should see your Jenkins server webhook in the main interface

**Note**:If for any reason Jenkins failed to register the hook (for example, due to upstream API changes or outages between Jenkins and Github), you can quickly add one yourself by clicking **Add webhook** and ensuring that the **Payload URL** is set to` https://my-jenkins-server:8080/github-webhook` and the **Content type** is set to `application/json`, then clicking **Add webhook** again at the bottom of the prompt

Now, when you push new changes to your repository, Jenkins will be notified. It will then pull the new code and retest it using the same procedure.

To approximate this, in our repository page on GitHub, you can click the **Create new file** button to the left of the green **Clone or download button**

On the next page, choose a filename and some dummy contents
Click the **Commit new file** button at the bottom when you are finished.

If you return to your Jenkins interface, you will see a new build automatically started.

You can kick off additional builds by making commits to a local copy of the repository and pushing it back up to GitHub