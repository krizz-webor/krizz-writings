## CodeDeploy

### Deploy index.html file on EC2 machine using nginx
#### Create a CodeDeploy application:

You need to create a CodeDeploy application to deploy your index.html file. You can do this in the AWS Management Console.

In CodeDeploy, go to Applications and click on `Create application`.

![tYJUA9Z-85c4zdZSrHz0bEMz0PqWoSgO3RfhgUycsud7flEsrVJmP_d--6quYmLpYGPsqr4hWOD_Id5gZfP_31MpnkE-v96ohPwm1fQw](../../../../media/tYJUA9Z-85c4zdZSrHz0bEMz0PqWoSgO3RfhgUycsud7flEsrVJmP_d--6quYmLpYGPsqr4hWOD_Id5gZfP_31MpnkE-v96ohPwm1fQw.png)

Select compute platform `EC2/on premises` and click on `Create application`.

![Rw_xpNJ8kDkJ9_rzIcfX2Ua8FfPSO9PbieHpB2DG4gwF_kMhTn2rpH-DJdexbVd8bb4e3-45lnFtwmwcFRD7ktqOI1gc5b80qVZh5Fqj](../../../../media/Rw_xpNJ8kDkJ9_rzIcfX2Ua8FfPSO9PbieHpB2DG4gwF_kMhTn2rpH-DJdexbVd8bb4e3-45lnFtwmwcFRD7ktqOI1gc5b80qVZh5Fqj.png)

Application is successfully created.

![zWwY_HL6bRnPXhwSy6cpE6JkHykajEtDfLTmL-5QKQKQ5MmFZOD79wlm8z0k95sSHYpZelRG4SphD7DpKJ3uteaCtX7d_KMc8UFw1SxPrw](../../../../media/zWwY_HL6bRnPXhwSy6cpE6JkHykajEtDfLTmL-5QKQKQ5MmFZOD79wlm8z0k95sSHYpZelRG4SphD7DpKJ3uteaCtX7d_KMc8UFw1SxPrw.png)

Create `service role` for enabling communication between code deploy and other aws services.

Go to IAM service and create `code-deploy-service-role` with below permissions.

![aJX7hD-hJNsaTJnotZtZxD-JB8N_6i9EefaMiINzWtdfYx1CFk2I--408zBD_zCZPp-u7kWOuvItIVxQcGNWRPqjSHgrdiNxsdcMii2Uug](../../../../media/aJX7hD-hJNsaTJnotZtZxD-JB8N_6i9EefaMiINzWtdfYx1CFk2I--408zBD_zCZPp-u7kWOuvItIVxQcGNWRPqjSHgrdiNxsdcMii2Uug.png)

#### Set up an EC2 instance:
You will need to create an EC2 instance on which you want to deploy the index.html file.

Create a ubuntu EC2 instance

![NIyMTWxhkyQ4mCyFP2d0-hX8zSlA16POB-tH74sl2LdvwDjOOs_M7lQOY0jHDnzZ6BQZ9ThNu4F4s0_4RlzYVF83WHof8wTZQY4e_R0](../../../../media/NIyMTWxhkyQ4mCyFP2d0-hX8zSlA16POB-tH74sl2LdvwDjOOs_M7lQOY0jHDnzZ6BQZ9ThNu4F4s0_4RlzYVF83WHof8wTZQY4e_R0.png)

#### Create a deployment group:
Once you have created a CodeDeploy application, you need to create a deployment group. A deployment group is a set of EC2 instances where you want to deploy your application.

![z_KnjiKvCPxPm3iES8AnJ3W2nOcUoznIbCubEpBaTBv7QcG0cVAxDW1HfMIfOv_A5KnWlO3xRyR6ilk2pCRXt7YjZ15lmZPqRNDx8qQIpw](../../../../media/z_KnjiKvCPxPm3iES8AnJ3W2nOcUoznIbCubEpBaTBv7QcG0cVAxDW1HfMIfOv_A5KnWlO3xRyR6ilk2pCRXt7YjZ15lmZPqRNDx8qQIpw.png)

Add deployment group name and choose `Service role`.

![u44j4Lao0epopbFP4MV_0ZjqsaNI0n2DwQMGalBqlC5cu3eO6a6QiAbAew3vRtpPQDmdctNx6DMuJKSzOgZ07Qwppp8PoLliA_Whniw4](../../../../media/u44j4Lao0epopbFP4MV_0ZjqsaNI0n2DwQMGalBqlC5cu3eO6a6QiAbAew3vRtpPQDmdctNx6DMuJKSzOgZ07Qwppp8PoLliA_Whniw4.png)

![SEgO4koASJD55YiH7cHiDd1G8JxhFy_xk_PHusfmkIKnBEnIHIkv7Aywseb-n0yyTF8bimvdjVNv5S0-aXPrfigzdhd7eQBUNX8YZHQS](../../../../media/SEgO4koASJD55YiH7cHiDd1G8JxhFy_xk_PHusfmkIKnBEnIHIkv7Aywseb-n0yyTF8bimvdjVNv5S0-aXPrfigzdhd7eQBUNX8YZHQS.png)

Add instance name.

![BeO_DNbIr-oeyEx4JHkxWVdGFZRK6FRTEWdDvHZOFn7mQ7n-dRu-iGOG_2YJymaI8UDXx2gwH2vdxkkfzoCUKmxa9gsj16vb2GIKw40h](../../../../media/BeO_DNbIr-oeyEx4JHkxWVdGFZRK6FRTEWdDvHZOFn7mQ7n-dRu-iGOG_2YJymaI8UDXx2gwH2vdxkkfzoCUKmxa9gsj16vb2GIKw40h.png)

![sTxcaZiHfysMhxgO6m4VF0ShFC9_0E_hEEwyEI9Udh5HPJKsFgTMF2JjPFM2UEtsTNtleJ7BGsogjpP6bGOilllUXvXnCuXL3VgFmYNs](../../../../media/sTxcaZiHfysMhxgO6m4VF0ShFC9_0E_hEEwyEI9Udh5HPJKsFgTMF2JjPFM2UEtsTNtleJ7BGsogjpP6bGOilllUXvXnCuXL3VgFmYNs.png)

Click on `Create deployment group`.

![NKRC1iMJxW0h65TS4lskHOzZrVKzRiWhuNVgYE8yKTCzq7WR7rrGGaV3i1CjWPWgY3c-GqSk9NE7z3q4UVePC4xqy9-GfzSsXaunm-U](../../../../media/NKRC1iMJxW0h65TS4lskHOzZrVKzRiWhuNVgYE8yKTCzq7WR7rrGGaV3i1CjWPWgY3c-GqSk9NE7z3q4UVePC4xqy9-GfzSsXaunm-U.png)

Deployment group is created.

![i6v3zEToxww9nxmoXcPbOc4Mi4l2-QLgbkizAvPCe5IlbToMbOHWAlw0h_WnZ7F_SqV6lLnBgy6_VDxG-L5fU_FsMqwaOUSJd8taMLg](../../../../media/i6v3zEToxww9nxmoXcPbOc4Mi4l2-QLgbkizAvPCe5IlbToMbOHWAlw0h_WnZ7F_SqV6lLnBgy6_VDxG-L5fU_FsMqwaOUSJd8taMLg.png)

You have to setup a CodeDeploy agent in order to deploy code on EC2.

#### Install the CodeDeploy agent:
You need to install the CodeDeploy agent on your Ubuntu EC2 instance. The CodeDeploy agent is a software package that runs on your instance and interacts with CodeDeploy to deploy your application. 

You can install the CodeDeploy agent by running the following script on your EC2 instance:

![wmfdYSmTu4Br5OPvT5098rdHIsNxlGg8TKyjaGK83CEGYGr3MJj9slTfXPAU4LdZi0sRtGYOuCWCqXpg-QDjGZZFNy7CIUi8Wg6Q_GA](../../../../media/wmfdYSmTu4Br5OPvT5098rdHIsNxlGg8TKyjaGK83CEGYGr3MJj9slTfXPAU4LdZi0sRtGYOuCWCqXpg-QDjGZZFNy7CIUi8Wg6Q_GA.png)

Run the script using command bash install.sh

![J99g_MCJmgCqlPO96Jmvi97bDIfphC_NDt1dkgyhjGMFFoImRcVHVr6s5gTKtCTLIbhk2kBP7USbrlIrDOg-21SG7urbWrFYRPu6mLEd](../../../../media/J99g_MCJmgCqlPO96Jmvi97bDIfphC_NDt1dkgyhjGMFFoImRcVHVr6s5gTKtCTLIbhk2kBP7USbrlIrDOg-21SG7urbWrFYRPu6mLEd.png)

Code agent is running.

![0bPhXNYmbm1w7MHUuTh342m6Su7YyVSMWgwYmMnHwSsBqYuWivVNd3YiK9TbfUuK8huzwlCXkHJ086nOchZOQvRzQQYNxg8KJws-To3v](../../../../media/0bPhXNYmbm1w7MHUuTh342m6Su7YyVSMWgwYmMnHwSsBqYuWivVNd3YiK9TbfUuK8huzwlCXkHJ086nOchZOQvRzQQYNxg8KJws-To3v.png)

#### Create an index.html file:
you need to create an index.html file that you want to deploy. You can create a simple HTML file using any text editor.

![PPcRSswkaIJuHZKcVg187eDjtyhA6jIY4Tw57i5u04rfBX52LAK5KNPECIx4e8dQjvDiGa1h4aa0iuMipH-NEU1Kcp_MWFGbH3OgiegK](../../../../media/PPcRSswkaIJuHZKcVg187eDjtyhA6jIY4Tw57i5u04rfBX52LAK5KNPECIx4e8dQjvDiGa1h4aa0iuMipH-NEU1Kcp_MWFGbH3OgiegK.png)

#### Task-02 :
Add appspec.yaml file to CodeCommit Repository and complete the deployment process.

#### Create an appspec.yaml file:
You need to create an appspec.yaml file that tells CodeDeploy what to do with your application.

Here is an appspec.yaml file that deploys the index.html file on nginx. also create 2 scripts for installing nginx and starting nginx.

![6ERaiGEWA7aq5QdTPnI3XevEkb9HYeTTUeIu5qwbZZkMkQOSJ4hR37UxsjUo7BiBjJkP3CzRbrTFTP4udpIdAZoY6XFOlLBCE4q-HfM0](../../../../media/6ERaiGEWA7aq5QdTPnI3XevEkb9HYeTTUeIu5qwbZZkMkQOSJ4hR37UxsjUo7BiBjJkP3CzRbrTFTP4udpIdAZoY6XFOlLBCE4q-HfM0.png)

Push all the files to code commit using `git add` and `git commit` commands.

![4tC54TUGgb-v2k2rToSj84yKJZ3euYYPDiFbzQvrZX9oTlR3WE74vlFQNK-chv-lJ1An02Uo9wKIrU3uEqGXCqGmK6evV2Q-Kb9u9y0](../../../../media/4tC54TUGgb-v2k2rToSj84yKJZ3euYYPDiFbzQvrZX9oTlR3WE74vlFQNK-chv-lJ1An02Uo9wKIrU3uEqGXCqGmK6evV2Q-Kb9u9y0.png)

All the files updated in code commit.

![9AYUvUFvJhgsfj2YI4qvAFoL-QD5XoiK9bqZEkkkMUh-1dU5eqJ5rwD-QQf1cR747FwnUduAy5MTn9t4Tnl-FDA8qensFaPVeiaPmHt8](../../../../media/9AYUvUFvJhgsfj2YI4qvAFoL-QD5XoiK9bqZEkkkMUh-1dU5eqJ5rwD-QQf1cR747FwnUduAy5MTn9t4Tnl-FDA8qensFaPVeiaPmHt8.png)

Add changes to buildspec.yml file

![4o7xM6srX0gkFmrmS_risHgIr7rx8SzOMm5bC3raY5YVefBBxcaX47SO_SxOoIfyj4fbciMwgiT71a1FsXNdRNhM-6aQ-5GoI2Vf7rhr](../../../../media/4o7xM6srX0gkFmrmS_risHgIr7rx8SzOMm5bC3raY5YVefBBxcaX47SO_SxOoIfyj4fbciMwgiT71a1FsXNdRNhM-6aQ-5GoI2Vf7rhr.png)

In build projects, Edit and choose `Artifacts`.

![KaCIF4DsQh2H4CD2qZNHuaT9lkVWbMD8i7oCCliswVSqRlrZWFout8MxqoaKwgJjB3uLrpCJpWyUT_xb_jPK1odUvu2yFs3G2OlOOJ4](../../../../media/KaCIF4DsQh2H4CD2qZNHuaT9lkVWbMD8i7oCCliswVSqRlrZWFout8MxqoaKwgJjB3uLrpCJpWyUT_xb_jPK1odUvu2yFs3G2OlOOJ4.png)

first create `S3 bucket`.

![m1UF3vucxCL3Cn5R39j8oZb-fhvXVpIdsxnJ4CQqo9sadthTLh3Q_wo-VfZdNhuOk3A6UOp58xn0PUxyfkQQG-pNw44AcU7Oc6mLs9BGSQ](../../../../media/m1UF3vucxCL3Cn5R39j8oZb-fhvXVpIdsxnJ4CQqo9sadthTLh3Q_wo-VfZdNhuOk3A6UOp58xn0PUxyfkQQG-pNw44AcU7Oc6mLs9BGSQ.png)

In Artifacts, select artifact type as Amazon S3 and choose bucket name.

![RHZ-PTS-9asLt3JLWS6HDSjymOapKqAjZNwEZsyrxCI-0pcF4uOdBcAq1DRwHu8Xy0PBrp7CUq0VyWfIsH0Jj2P9SAg0K2aYSJ7hgf9ttA](../../../../media/RHZ-PTS-9asLt3JLWS6HDSjymOapKqAjZNwEZsyrxCI-0pcF4uOdBcAq1DRwHu8Xy0PBrp7CUq0VyWfIsH0Jj2P9SAg0K2aYSJ7hgf9ttA.png)

Click on `Update artifacts`.

![gO2i4Aou-GQNWHr3VPj55HXAwEjcdR0VqFifeZcwa8jxHXEPNpdVTQCPwlz_ewZr7mPMel-Mq1aRRkdMROWNfSlskOAidoPkqkaIlnjNVg](../../../../media/gO2i4Aou-GQNWHr3VPj55HXAwEjcdR0VqFifeZcwa8jxHXEPNpdVTQCPwlz_ewZr7mPMel-Mq1aRRkdMROWNfSlskOAidoPkqkaIlnjNVg.png)

Artifact upload location successfully added. Click on `Start build`.

![viYIdFI3ZATaa4ErshahHhIh9yWpHfcDUPVlLlYKS5Dp8JkHrRw8zZPcx34ESO5LLC7LP2DY8SYXlNzvLXuNLdQz24Swd5JdQeh4bvL9](../../../../media/viYIdFI3ZATaa4ErshahHhIh9yWpHfcDUPVlLlYKS5Dp8JkHrRw8zZPcx34ESO5LLC7LP2DY8SYXlNzvLXuNLdQz24Swd5JdQeh4bvL9.png)

Build is Succeeded.

![yafiJxLbh6UIQCzkwDzo3Y8fpuYaYSbdPsFcA96_AhFa5Nsl2Jc3q26w1ptrjG_Zs8BnTgar_11OiT5MV2nEjMIO7DxKLGqy2Ms5dEIaNw](../../../../media/yafiJxLbh6UIQCzkwDzo3Y8fpuYaYSbdPsFcA96_AhFa5Nsl2Jc3q26w1ptrjG_Zs8BnTgar_11OiT5MV2nEjMIO7DxKLGqy2Ms5dEIaNw.png)

After build completion, go to S3 bucket and copy S3 url of nginx_code_output zip file.

![yPkCdkh4lvJ3FWOh6q_twHfa6TDegggjMCLhDPcfe28RGFVS9BRGmHB7N7jsTfgKr9Sx6upezDWe8tqvzO33GAIBLnNCC4a6qDBtt8CRfg](../../../../media/yPkCdkh4lvJ3FWOh6q_twHfa6TDegggjMCLhDPcfe28RGFVS9BRGmHB7N7jsTfgKr9Sx6upezDWe8tqvzO33GAIBLnNCC4a6qDBtt8CRfg.png)

#### Create deployment:
In Application, Go to Deployments and click on `Create deployment`

![rKlkcFJB87etLuXjEyudNk5_ALNg5IsNCQRmFO10DhXrBm4qIYn1Dqzq2zaXGdJz2XeKi03gdAjZG8kzRzQSgrzV7sXYepX3yDKUI9KH](../../../../media/rKlkcFJB87etLuXjEyudNk5_ALNg5IsNCQRmFO10DhXrBm4qIYn1Dqzq2zaXGdJz2XeKi03gdAjZG8kzRzQSgrzV7sXYepX3yDKUI9KH.png)

In revision type, select amazon S3 and paste above copied S3 url to revision location.

![oAfoTlWjM6QKGJCJPLOzzAiiTSWUMbwLPAMa3J2pk7si36TzYvBsvzWF6p1ugfrj0NobWJX7Rx1aLtwp5mxxf4T5QXbhUzd1liUbY444Dg](../../../../media/oAfoTlWjM6QKGJCJPLOzzAiiTSWUMbwLPAMa3J2pk7si36TzYvBsvzWF6p1ugfrj0NobWJX7Rx1aLtwp5mxxf4T5QXbhUzd1liUbY444Dg.png)

Click on `Create deployment`.

![xDbWODuchElEtplcPXNsu4FosXNFNeLo6G38aaxR-knPfkIgXhedhOmDcGMMLHMThF8ntS6Ksdqk24zMRYp-W4lLkz-G5cYZrKTC_pQ](../../../../media/xDbWODuchElEtplcPXNsu4FosXNFNeLo6G38aaxR-knPfkIgXhedhOmDcGMMLHMThF8ntS6Ksdqk24zMRYp-W4lLkz-G5cYZrKTC_pQ.png)

Deployment is created. but events are in pending state.

![V1DM6f8KDcv44REw3UApFL1IpSiYEYHKzO5OiJDBObhxhmzdI2TSsUT-_G3uQ2amWpj9fWdro-oByR60relKkOh7QerhYKlV4RrAFy8I](../../../../media/V1DM6f8KDcv44REw3UApFL1IpSiYEYHKzO5OiJDBObhxhmzdI2TSsUT-_G3uQ2amWpj9fWdro-oByR60relKkOh7QerhYKlV4RrAFy8I.png)

EC2 doesn't have any role policy to retrieve the data from S3 to CodeDeploy.

So create a new service role for enabling communication between EC2 and S3, code deploy.

![AbnBrUMgHENFNRq-B8DJcgJKdeV21OT7Q_NbVsAK3cZYHELQy7HLCiPKyvoJup3yaqHSZP8m5eqPmzlJp8M_kuEVQaep2zVdE_Z0eIfz](../../../../media/AbnBrUMgHENFNRq-B8DJcgJKdeV21OT7Q_NbVsAK3cZYHELQy7HLCiPKyvoJup3yaqHSZP8m5eqPmzlJp8M_kuEVQaep2zVdE_Z0eIfz.png)

Attach that service role to EC2 instance.
Select EC2 instance, In actions, go to security and click on `Modify IAM role`.

![cLinALi8Yjiwg1jpAx0w94UMjm3cpwX8Rv0Q_9glPXSgojkGMeMu-QHDvtfmWCBoxMNOI4mfIoAfoPyHxu0xhF4l6KgN05JpW3B47MWg](../../../../media/cLinALi8Yjiwg1jpAx0w94UMjm3cpwX8Rv0Q_9glPXSgojkGMeMu-QHDvtfmWCBoxMNOI4mfIoAfoPyHxu0xhF4l6KgN05JpW3B47MWg.png)

Select service role that we created in above steps.

![b0WjFdhTn37e75BjqOV7PPaY8v5TOOajYyzmQOKvRyJj4XtVnG7TUufm4WqdDGuH-L7s-cwdpqmh1f_adnKOdiIUZtY5riEHsyG1WJwi](../../../../media/b0WjFdhTn37e75BjqOV7PPaY8v5TOOajYyzmQOKvRyJj4XtVnG7TUufm4WqdDGuH-L7s-cwdpqmh1f_adnKOdiIUZtY5riEHsyG1WJwi.png)

After updating IAM role, restart code-deploy agent.

![GS_sQR4_prPtAXuWctt2aHQEZe6MVy94MWTwSfGrAun_oOfwQNPYXPvP6uCeUUT-_kDALJReA0FfCZdgMaNtuls17uR9L92N9I_woBs](../../../../media/GS_sQR4_prPtAXuWctt2aHQEZe6MVy94MWTwSfGrAun_oOfwQNPYXPvP6uCeUUT-_kDALJReA0FfCZdgMaNtuls17uR9L92N9I_woBs.png)

Deployment status is Succeeded.

![OPDCa4pb7PpHMD5IRcMQllBJWU3YHwlvkBVILVkdQXE1itM7p6DwN38M7SCBT3vswp-KNtxU4mxCiLYrrySNUCoFEqkuhCLbFomUQfU](../../../../media/OPDCa4pb7PpHMD5IRcMQllBJWU3YHwlvkBVILVkdQXE1itM7p6DwN38M7SCBT3vswp-KNtxU4mxCiLYrrySNUCoFEqkuhCLbFomUQfU.png)

All events Succeeded.

![u-MqeK0PPkAKc3i-cNClscnP7Feph4KqJdwoiCSlmCcJv0ZD_nYXm7kKPy4QnQQaE7dlVvmFMBDSwOz-9qOvnutyc4fv-Nl4bBKYPRN-](../../../../media/u-MqeK0PPkAKc3i-cNClscnP7Feph4KqJdwoiCSlmCcJv0ZD_nYXm7kKPy4QnQQaE7dlVvmFMBDSwOz-9qOvnutyc4fv-Nl4bBKYPRN-.png)

Browse instance public IP address, it will show output of index.html file.

![GmdLzDpsR8ubNSaQVB-xib-5G7kEJRHGSTmUavLmAqPEl4QC1z8Hy-oy-h6RBVfWWC8N8yLAYNsCkaW9Zr_7fd22etPY-JM3m5zlCCjO](../../../../media/GmdLzDpsR8ubNSaQVB-xib-5G7kEJRHGSTmUavLmAqPEl4QC1z8Hy-oy-h6RBVfWWC8N8yLAYNsCkaW9Zr_7fd22etPY-JM3m5zlCCjO.png)