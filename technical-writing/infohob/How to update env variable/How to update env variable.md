## How to update env variable
* Open the Jenkinsenv file.
* Replace the files necessary and save it.
* Goto your Jenkins.
* Goto `Manage jenkins`.
* Goto `Manage credentials`.
* Click on `Jenkinsenv (Infohob Backend Jenkinsenv file for environment variables. Always update the file locally and upload to Jenkins when you want to add new environment variables)`.
* Click on `Update`.
* Tick `Replace`.
* Below the **File**, Click on `Choose File`.
* Select the Jenkinsenv file that you updated.
* Click `Save`.
* Go back to Dashboard.
* Click on `infohob-job-seek-backend`.
* Click `Build Now` to update the updated env variable file.