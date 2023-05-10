## CodePipeline


#### Create a Deployment group of EC2 Instance.
Create a CodeDeploy application:

In CodeDeploy, go to Applications and click on 'Create application'.

![Lf2-WLv7WJhRp7KlG0_7xZfssvrS87VHAjuteftPcbg1WVptgysXdSQJlYu8QxQV_Z2FqRCtmUl-UMUt8g0odudrFikji3S2iaBGDw0W](../../../../media/Lf2-WLv7WJhRp7KlG0_7xZfssvrS87VHAjuteftPcbg1WVptgysXdSQJlYu8QxQV_Z2FqRCtmUl-UMUt8g0odudrFikji3S2iaBGDw0W.png)

![rujT-iDpO-j1EnsoKGQdiV5BGc6bw6okoqZeoNKEq1xIDiDw_XzHHMQQA8fDM-UTRDrZWydbkHM7jmaHvUZ3fxCqbDgfKsR-iTere-s](../../../../media/rujT-iDpO-j1EnsoKGQdiV5BGc6bw6okoqZeoNKEq1xIDiDw_XzHHMQQA8fDM-UTRDrZWydbkHM7jmaHvUZ3fxCqbDgfKsR-iTere-s.png)

Application is successfully created.

![80hbLVUtOU8GVbGMwoATxS4Vf5TSbOk0pESLp40ExHCKY5wVyN4kANPQxaisvpxMWzIeFmwn2KTE0907F1_RXJBAXUGod-zHInIxqg-6](../../../../media/80hbLVUtOU8GVbGMwoATxS4Vf5TSbOk0pESLp40ExHCKY5wVyN4kANPQxaisvpxMWzIeFmwn2KTE0907F1_RXJBAXUGod-zHInIxqg-6.png)

Create 'service role' for enabling communication between code deploy and other aws services. 

Create 'code-deploy-service-role' with below permissions.

![u670nnndMlwBJ17kaxbF548pmK7M91UMQtXzRQZIt0Qm8An3RoaEuv2JjzICxR-FFzhyP6coCOwxgOPhEspk8bRgJRUdSEOz-3l7kdpFuw](../../../../media/u670nnndMlwBJ17kaxbF548pmK7M91UMQtXzRQZIt0Qm8An3RoaEuv2JjzICxR-FFzhyP6coCOwxgOPhEspk8bRgJRUdSEOz-3l7kdpFuw.png)

Create an ubuntu EC2 instance:

![LiUEIPbvlhy8yiCFwWKei7mgPZ1u4y9195ahvclrlNwjzhYwOTL10jS879S-C3yq_Hbk_9DUyFxR9dt9kzoBUmC4e2MQdZ00bj0bow8](../../../../media/LiUEIPbvlhy8yiCFwWKei7mgPZ1u4y9195ahvclrlNwjzhYwOTL10jS879S-C3yq_Hbk_9DUyFxR9dt9kzoBUmC4e2MQdZ00bj0bow8.png)

Create a deployment group:

![1Kx5X2qi7acTc8p7eYHx_9bGsEK5rwBB6p1wyzwENv3Y1CC8bXk_Z1RPFDtMMseVdYlzdqdDX9g_QVFtjJSXP4c9x_zsoJrcA_PBZUk](../../../../media/1Kx5X2qi7acTc8p7eYHx_9bGsEK5rwBB6p1wyzwENv3Y1CC8bXk_Z1RPFDtMMseVdYlzdqdDX9g_QVFtjJSXP4c9x_zsoJrcA_PBZUk.png)

Add deployment group name and choose 'Service role'

![3SSf-tNUUGu74-_kEir-A3JPJzygmUV6eE-8Xcsz76CQpJzShGuOkWaCErLy5TG6wi1gxBX8nc53BbzXdqDIz3XFH1C0zVrXHTNBB9yXiA](../../../../media/3SSf-tNUUGu74-_kEir-A3JPJzygmUV6eE-8Xcsz76CQpJzShGuOkWaCErLy5TG6wi1gxBX8nc53BbzXdqDIz3XFH1C0zVrXHTNBB9yXiA.png)

![iaFRyenTGedvzUZdojqDiVkeuaeJ929RrCkdA9-Iyglgmjfw6F1_DRIYLH6hfBR-S2dFQJXDvbUkufo4cQ8uIzlE2_rmIy2jvavqBCo](../../../../media/iaFRyenTGedvzUZdojqDiVkeuaeJ929RrCkdA9-Iyglgmjfw6F1_DRIYLH6hfBR-S2dFQJXDvbUkufo4cQ8uIzlE2_rmIy2jvavqBCo.png)

Add instance name.

![kzMyz8Lu8wJhEQHe1TsMsKgX6IPje--X503C_9uocHtm4YP8mhty1SUZkguFDnH8_rM16ix2B7uDWxw3-Bqzl9lgihIZBYmDrytAvI0Q](../../../../media/kzMyz8Lu8wJhEQHe1TsMsKgX6IPje--X503C_9uocHtm4YP8mhty1SUZkguFDnH8_rM16ix2B7uDWxw3-Bqzl9lgihIZBYmDrytAvI0Q.png)

![jTgpsIhDbqeNX95lAA7IVZSMMVvMdnZuvfyTTVBxrBOtHVRKiAlsU1CNqtiKrcucUdNsqXOBUHAjdRC3WeqcRtzF-1Exs80tqfaFwee-](../../../../media/jTgpsIhDbqeNX95lAA7IVZSMMVvMdnZuvfyTTVBxrBOtHVRKiAlsU1CNqtiKrcucUdNsqXOBUHAjdRC3WeqcRtzF-1Exs80tqfaFwee-.png)

![gpJjn6hKeFhn0FfeBd_DuXGlOnGZXjlZvSDIT7TEC2aTlGT278g9FQUfRnBmKvjIvn2N8vLEvklDPtt6Spu_UEGSjRtvJYTuHiNWRgLi](../../../../media/gpJjn6hKeFhn0FfeBd_DuXGlOnGZXjlZvSDIT7TEC2aTlGT278g9FQUfRnBmKvjIvn2N8vLEvklDPtt6Spu_UEGSjRtvJYTuHiNWRgLi.png)

Deployment group is created.

![FV0GGVtuKzXnxStqtNn9eW9s4kIJeZHX8PtMhETTF1IcNSmPVyKRdggcjsYMrt5piQRwcHsNl7VK-8WHBdJQwvk8pumfOEoVJIo--Tw](../../../../media/FV0GGVtuKzXnxStqtNn9eW9s4kIJeZHX8PtMhETTF1IcNSmPVyKRdggcjsYMrt5piQRwcHsNl7VK-8WHBdJQwvk8pumfOEoVJIo--Tw.png)

#### Install the CodeDeploy agent in ec2 insatnce:
You can install the CodeDeploy agent by running the following script on your EC2 instance:

![Icarm__hOOAPELz8t3ogAC4Zo-2E-JF6Yad8ThCGqg8vM36roH9VwXpPVSi6gzXQ4EHLpQuDyu-bGj8kVsSdnRdBN-gWoNI2jR2jxxBE](../../../../media/Icarm__hOOAPELz8t3ogAC4Zo-2E-JF6Yad8ThCGqg8vM36roH9VwXpPVSi6gzXQ4EHLpQuDyu-bGj8kVsSdnRdBN-gWoNI2jR2jxxBE.png)

Code agent is running.

![3lSRnHpV508pNBU_HXKm9RStiNJN9knMuBPjw_kBgza3I7wq6t9BwzrKJRuz_i67TwfIKhjN4EbiOsqhfVWkgDlYxarpauAgVgLyRi8](../../../../media/3lSRnHpV508pNBU_HXKm9RStiNJN9knMuBPjw_kBgza3I7wq6t9BwzrKJRuz_i67TwfIKhjN4EbiOsqhfVWkgDlYxarpauAgVgLyRi8.png)

![-MbRw8uY6ctUs-Qc_s-JjlSf44SZ_Pu4tai-Odflqn0J33erYjt7nLgmPWmbn4sikOGnea6ekixZiv3_FcdlOKj0tKlJzufI3ltqvCRe](../../../../media/-MbRw8uY6ctUs-Qc_s-JjlSf44SZ_Pu4tai-Odflqn0J33erYjt7nLgmPWmbn4sikOGnea6ekixZiv3_FcdlOKj0tKlJzufI3ltqvCRe.png)

#### Create a CodePipeline that gets the code from CodeCommit, Builds the code using CodeBuild and deploys it to a Deployment Group.
Go to the CodePipeline console. Click "Create pipeline."

![rx0VJ6BUvYPnIvqMUAalfaCwSTeJtSwL0U9yOgOTimg24Z_TMNdKnDXvES5WUbDe6I7Y0c396vHWN-_Hbcc0T1dSsdFNEkjMOIgjw26D](../../../../media/rx0VJ6BUvYPnIvqMUAalfaCwSTeJtSwL0U9yOgOTimg24Z_TMNdKnDXvES5WUbDe6I7Y0c396vHWN-_Hbcc0T1dSsdFNEkjMOIgjw26D.png)

Enter a name for your pipeline.

![WpAnxM4hBsdgKy3PauUOs5xKkS39B8OKL-5NtDRUl270W8jTPLR77Vg4ahK6hSnYAIFXq8n1rX3t3busO4suH3FEwiTL_264RYAlsvL3](../../../../media/WpAnxM4hBsdgKy3PauUOs5xKkS39B8OKL-5NtDRUl270W8jTPLR77Vg4ahK6hSnYAIFXq8n1rX3t3busO4suH3FEwiTL_264RYAlsvL3.png)

Under "Source provider," choose "AWS CodeCommit."

Select the repository and branch you want to deploy.

Click "Next."

![9g67X4e2lkKKNGNkjkSDowBD8mll-sPjLwIr9MExRuU_kJ1TuLUYF2dRzwEAcfZECUzsSCkwyPsRTYtdmKNwz7YV_U1K3dlr_ZqlZLU](../../../../media/9g67X4e2lkKKNGNkjkSDowBD8mll-sPjLwIr9MExRuU_kJ1TuLUYF2dRzwEAcfZECUzsSCkwyPsRTYtdmKNwz7YV_U1K3dlr_ZqlZLU.png)

Under "Build provider," choose "AWS CodeBuild."

Select "build project name."

Click "Next."

![-VsHE89Kci4QfggYOJZ2h85und48nB6Jypr9Fvyfw5BeeNIRIjCoBsdNiF6PBYrF0INDM9SPM9eUdMzzsY51Pi0vnsSx2HwgAfBh_CF4](../../../../media/-VsHE89Kci4QfggYOJZ2h85und48nB6Jypr9Fvyfw5BeeNIRIjCoBsdNiF6PBYrF0INDM9SPM9eUdMzzsY51Pi0vnsSx2HwgAfBh_CF4.png)

Under "Deploy provider," choose "AWS CodeDeploy."

Select the deployment group you created earlier.

Click "Next."

![baU8fr9CUb3Zdrybge0kurPcpVmuZtbss6ckfKLUGqiPjuMLF_EgTFyJeqAxEuFJrWt0Ah-T7FYX_NFqraFrc7GQM49TWX07CYpdGtPN8w](../../../../media/baU8fr9CUb3Zdrybge0kurPcpVmuZtbss6ckfKLUGqiPjuMLF_EgTFyJeqAxEuFJrWt0Ah-T7FYX_NFqraFrc7GQM49TWX07CYpdGtPN8w.png)

Review the pipeline settings and click "Create pipeline."

![eInmAjoMiApgbJ1ePsrtV6rUNfR1v7q8XP6FTaHFoKo4DQ6zewYwyURBvdcIMOJusGwmy1CZcM8_j8FDkvXGBl7YlHfSUeUP-K4U3HQ](../../../../media/eInmAjoMiApgbJ1ePsrtV6rUNfR1v7q8XP6FTaHFoKo4DQ6zewYwyURBvdcIMOJusGwmy1CZcM8_j8FDkvXGBl7YlHfSUeUP-K4U3HQ.png)

The pipeline will automatically trigger a build and deploy the new code to the EC2 instance.

Successfully created a CodePipeline that automates the deployment process.

![nH8eM3t3kuo_Js-D0y8-xEgRY1jmn6sP6jySKJlG9p2Vorsu8oXdPs-uS-DyIIYsKRSA6xCaOiMcJ691I5mHNM2D4zDND6kMRYQ97fnk](../../../../media/nH8eM3t3kuo_Js-D0y8-xEgRY1jmn6sP6jySKJlG9p2Vorsu8oXdPs-uS-DyIIYsKRSA6xCaOiMcJ691I5mHNM2D4zDND6kMRYQ97fnk.png)

Browse your instance public-ip address, you can see final output of index.html


![ckBV8_ATxtz5uvN2X1IQPra_BJSyvXOEQunmyq0l8gYD7l8qcu8bRCfvGtQU-xH28z9bWDmkYpl-wwsxMgspNt8xDnqW_bikA5-j3MfD](../../../../media/ckBV8_ATxtz5uvN2X1IQPra_BJSyvXOEQunmyq0l8gYD7l8qcu8bRCfvGtQU-xH28z9bWDmkYpl-wwsxMgspNt8xDnqW_bikA5-j3MfD.png)

