 ## How to use the command line in Jenkins CLI
CLI means Command Line Interface.

To get to the `CLI`, 
Firstly, start Jenkins, click on `Manage Jenkins`.

Click on `Configure Global Security` on the `Security` section. It will take you to another page.

On the `Authentification` section, check if the `Disable remember me` is unchecked, if yes, click on `Apply` and then `Save`.

Next, goto the top of your browser, making sure that your Jenkins is still open,click on the link and add `/cli` to it and tap `ENTER` key.

It will take you to the `CLI` page where you would see documentation and` Available Commands`. At the top, click on the link `Jenkins-cli.jar` to download the Jenkins `CLI`. 

After downloading the file, goto your terminal, `cd` into the directory where the Jenkins `CLI` was downloaded which is the Download folder.

Go back to your Jenkin `CLI` page, copy the link at the top which is in a black background, go back to your terminal, paste the code you just copied on your Jenkins `CLI` and hit `ENTER` key.

If your are having an error issue, goto your Jenkins `Dashboard`, click on `Manage Jenkins`, goto `Configure Global Security` and click. Scroll down to `Authorisation` and tick on `Anyone can do anything` ( Later, change it back to Logged-in users can do anything.

Click on `Apply` and then `Save`. Go back to your Terminal and run the code again and this time it has to run.

Another way to goto your Jenkins `CLI`, is to goto your `Dashboard`, click on `Manage Jenkins`, scroll down to the `Tools and Actions` section, there, you would see the `CLI` tab.
 