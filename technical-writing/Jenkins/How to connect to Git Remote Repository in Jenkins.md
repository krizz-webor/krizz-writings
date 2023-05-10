## How to connect to Git Remote Repository in Jenkins
Goto `GitHub`, 

Create a repository. After creating the repository

Click on `creating a new file` still on that repository, which is under the **Quick setup**. 

Give the file a name, and write your code in the code prompt area. Click on `Commit new file` below.

Open your Jenkins, make sure the Git plugins has already been downloaded/installed.

Create a new job by ckicking on `New Item`, give a name on the `Enter an item name`.

Click on `Freestyle project` and click `OK`. This will take you to another page. 

At the top, Click on `Source Code Management`, tick `Git`. 

Goto the repository you created on `GitHub`, copy the `URL` by clicking on Code and copying the `URL`.

Goto your Jenkins, paste the `GitHub URL` you copied inside the Repository URL. If you have a credential already on the Jenkins machine, click on the open space which has an arrow opposite the `Add` tab, your key will be displayed and you select it. 

Also, goto your repository and check the branch if it's same with the `Branch specifier` on your Jenkins. If it's not, change it and click `Apply `and then `Save`. 

Click on `Build Now` at the left corner of the page to build the job to know if the code is working.