## CodeCommit

#### Set up a code repository on CodeCommit and clone it on your local.
Log in to the AWS Management Console and navigate to CodeCommit.

Click on `Create repository`.

![g1eP8vQT_3g7ML3CujdG5zs7fwR7hiXd8tkkdd4_dasY7P2R9p69nq-HaUa3qScYhgiCJfOYpQwODqreJuHSAIFLTK5Xwt2jV_AzvlU](../../../../media/g1eP8vQT_3g7ML3CujdG5zs7fwR7hiXd8tkkdd4_dasY7P2R9p69nq-HaUa3qScYhgiCJfOYpQwODqreJuHSAIFLTK5Xwt2jV_AzvlU.png)

Enter a name for your repository and click on `Create`

![Jc4dUO0ETYjwyx5LP8jVSOX6DZgRQiCxkJBAqxXITEVmYxonRpXySXETLK3kdSRttZz0uw8wOIide6DEUmUXi52-zzZ6Fm7hLk4R3eI](../../../../media/Jc4dUO0ETYjwyx5LP8jVSOX6DZgRQiCxkJBAqxXITEVmYxonRpXySXETLK3kdSRttZz0uw8wOIide6DEUmUXi52-zzZ6Fm7hLk4R3eI.png)

![23cTBjWN6ghdefUdfLIyKaJmbqfeyM_vQvfYl25dE77CZT420i8Pkr7ZYIXv3-WcjxP2--jrcGAsrYUKlQdo9NmdGMRXnVIqfr6VGd_Vhg](../../../../media/23cTBjWN6ghdefUdfLIyKaJmbqfeyM_vQvfYl25dE77CZT420i8Pkr7ZYIXv3-WcjxP2--jrcGAsrYUKlQdo9NmdGMRXnVIqfr6VGd_Vhg.png)

Repository is successfully created

#### You need to setup Git Credentials in your AWS IAM.
Go to IAM console

Click on `Users` in the left-hand menu, and then click on your username.

![Sl__KR79bDBOWFTpPgqaHMSvCCKtepSVuJFxXh-8Wn4k7oWef2SQpsqzvXBrG_lBt3Ca9abZzq3mG3M_LLePCQ-88wodguqefoSJkfQe](../../../../media/Sl__KR79bDBOWFTpPgqaHMSvCCKtepSVuJFxXh-8Wn4k7oWef2SQpsqzvXBrG_lBt3Ca9abZzq3mG3M_LLePCQ-88wodguqefoSJkfQe.png)

Scroll down to the `Security credentials` section.

![jx_HcFk_264CqfUevkVDQ4UeWAEzlUjCpuFL5PBaY1IPtvCto2Ls7rNtRTL8vkFmUvhTMYewJK3pYdZKrN-vfbwymj4sttFt_rJmbiI](../../../../media/jx_HcFk_264CqfUevkVDQ4UeWAEzlUjCpuFL5PBaY1IPtvCto2Ls7rNtRTL8vkFmUvhTMYewJK3pYdZKrN-vfbwymj4sttFt_rJmbiI.png)

In `HTTPS Git credentials for AWS CodeCommit` section, click on `Generate credentials`

![KtAgZ5NZIIKJuXt7F7WWLLWBQaJJwjb6yJBY6d9GeLQ78qWXrAb70ISYu2_98zFPpMPWRLODw6CRLK-oxzBZ92Dt7z-D0hmysVMbUjSpgw](../../../../media/KtAgZ5NZIIKJuXt7F7WWLLWBQaJJwjb6yJBY6d9GeLQ78qWXrAb70ISYu2_98zFPpMPWRLODw6CRLK-oxzBZ92Dt7z-D0hmysVMbUjSpgw.png)

Click on the `Download credentials` button to download your Git credentials and click on `close`.

![HcRhXpykZD8LtIWP6z0133PAsfqXyp3KvZ7iaFsE4KWs18gnb_Qk31rPRCttdaS_68tqUzKBHoUzrXZkVL-QVsHyhFWfA2S1MzmLDpUf](../../../../media/HcRhXpykZD8LtIWP6z0133PAsfqXyp3KvZ7iaFsE4KWs18gnb_Qk31rPRCttdaS_68tqUzKBHoUzrXZkVL-QVsHyhFWfA2S1MzmLDpUf.png)

Git credentials is created.

![3uGaJTJeqh9qSrynOYfbCeiDs9whCO5VVYS0sSOCIiB7YKmN___j6aT2wYqLY7wruXC2aosqPSZPAqYx0TK1QMLwaJ_eQ5WFSe5bibI](../../../../media/3uGaJTJeqh9qSrynOYfbCeiDs9whCO5VVYS0sSOCIiB7YKmN___j6aT2wYqLY7wruXC2aosqPSZPAqYx0TK1QMLwaJ_eQ5WFSe5bibI.png)

#### Use those credentials in your local and then clone the repository from CodeCommit

In Code Commit, Go inside your repository that you created in above steps, in right-hand side click on `Clone URL` and choose `Clone HTTPS`.

![9450Z4o4o5UrjHn75dnV6PWrIhB9FHSgb-y8lYGemt63wE2RmpAf6wekq6_1RhdSPnuK6unPV1acComV3C_nmIGbHUMIKKSym7pROa4](../../../../media/9450Z4o4o5UrjHn75dnV6PWrIhB9FHSgb-y8lYGemt63wE2RmpAf6wekq6_1RhdSPnuK6unPV1acComV3C_nmIGbHUMIKKSym7pROa4.png)

Open a terminal on your local machine.

Navigate to the directory where you want to clone the repository.

Run the following command:

    git clone <your-codecommit-repo-clone-https-url>

You will be prompted to enter your Git credentials. Enter the username and password that you downloaded earlier.

![rw1Q6WJtpqbCJpFXlcseN3oo9rnptUzgfYlmbli6AY0Q_RX7iL3I0dzT0mNmAiAHzcemXqaGZOodPs56jvOkE1KgS4EQyi5PuCOEsCU](../../../../media/rw1Q6WJtpqbCJpFXlcseN3oo9rnptUzgfYlmbli6AY0Q_RX7iL3I0dzT0mNmAiAHzcemXqaGZOodPs56jvOkE1KgS4EQyi5PuCOEsCU.png)

You have now set up a CodeCommit repository and cloned it on your local machine using Git Credentials in AWS IAM.

![nDSBGTqotvh-qijSWSPA2tjTTIXgA7QuOfpNndFSDiiXs0y0eG1A0KxQ-7ZeWMI-ZPu7B-OvsdUMQDMC7sQFuZptlwCYSCYzcAuRj1XH](../../../../media/nDSBGTqotvh-qijSWSPA2tjTTIXgA7QuOfpNndFSDiiXs0y0eG1A0KxQ-7ZeWMI-ZPu7B-OvsdUMQDMC7sQFuZptlwCYSCYzcAuRj1XH.png)

#### Add a new file from local and commit to your local branch
Create a new file in the local repository directory.

![uzlvaYuY43SFJ_gWxCbS4D8fWuESorLBzFl15W6oFhA6aQXLLubva1Y2IePUlq6Sc_z_8iD2c5WvEXak61ytMqsw44V5h5HufSTBUg0R](../../../../media/uzlvaYuY43SFJ_gWxCbS4D8fWuESorLBzFl15W6oFhA6aQXLLubva1Y2IePUlq6Sc_z_8iD2c5WvEXak61ytMqsw44V5h5HufSTBUg0R.png)

Check status using command 

    git status

Add the new file to your local branch using the following command:

    git add <filename>

Commit the changes to your local branch using the following command:

    git commit -m "added new file"

#### Push the local changes to CodeCommit repository.
Push the changes from your local branch to the CodeCommit repository using the following command:

    git push origin master

Verify that the changes have been pushed to the CodeCommit repository:

Go to the code commit repository that you created earlier, you should see the new file listed in the repository's files.

![dqh_2MllLHUYKgipqZgFL09wsBYkg0XgAC0EQZBAKYxldbxpYgkCE3pJYoklHaVhJLqUpDn65FA8zd6Vj1shsA-1rZdUENy7GGGet58d](../../../../media/dqh_2MllLHUYKgipqZgFL09wsBYkg0XgAC0EQZBAKYxldbxpYgkCE3pJYoklHaVhJLqUpDn65FA8zd6Vj1shsA-1rZdUENy7GGGet58d.png)

You can see content of the file.

![3n21N8cO2H4pA4vdWfw37LyFOK-g1tlidwtyBsp_pDUvl0qtBRQfrAmiYb7iwmP1f2foZKKWkpFt9onYHABX9zj1QxH8F7_nFyOPl-FoHg](../../../../media/3n21N8cO2H4pA4vdWfw37LyFOK-g1tlidwtyBsp_pDUvl0qtBRQfrAmiYb7iwmP1f2foZKKWkpFt9onYHABX9zj1QxH8F7_nFyOPl-FoHg.png)