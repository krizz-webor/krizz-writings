## How to connect to Git repository using the pipeline script
Open your Jenkins, On your `Dashboard`,

Click on `Manage Jenkins`,

Goto `Manage Plugins`,


Click on `Installed` to check if pipeline has already beebn installed on your machine. 

If no, click on `Available` to search for pipeline. If not there,

Goto back to your `Dashboard`, click on `New Item` to create a job. Put a job name in the `Enter an item name` 

There, you would see the `pipeline`,

Click on the `pipeline` and click `OK`.

Maybe enter a description on the `Description` under the `General` prompt.

Click on `Pipeline` at the top, make the `Pipeline Definition` to be at `pipeline script`.

A Jenkins pipeline code will appear like this:

    pipeline {
        agent any
    
        stages {
            stage('Hello') {
                steps {
                    echo 'Hello World'
                }
            }
        }
    }
Click on `pipeline syntax` below the `Save` button.

It will take you to another page.

On the `Sample steps`, click on the input, scroll down to look for `git:Git`.

Click on `git:Git`, goto your github repository you want to use, copy the `URL` and paste in the `Repository URL` in your Jenkins.

Check the `Branch` on your github repository if it matches with your Jenkins `Branch`, else, change it.

Add your `Credentials` and click `Generate Pipeline Script`.

Copy the `URL` and go back to your pipeline by switching back to the tab at the top of your browser.

Paste the URL in the script like this:

    pipeline {
        agent any
    
        stages {
            stage('Hello') {
                steps {
                    echo 'Hello World'
                    http://github.com/
                }
            }
        }
    }
Click on `Apply` and the `Save`.
Next, click on `Build Now` to build the job. 