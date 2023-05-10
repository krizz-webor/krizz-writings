## Set up ECS (Elastic Container Service) by setting up Nginx on ECS.
#### Create an ECS cluster:

In the ECS service, click on `Create Cluster`.

![IHJSylxNjtSUpYBK6BGUumZfMZZGxrRfN-wjuBnMP_IHgVDu7ye_fBto1iqj_AY2ngZz8Bbj_9Qxa_Q95Jc-hPOUpfa5bHorZ3OMu8dKog](../../../../media/IHJSylxNjtSUpYBK6BGUumZfMZZGxrRfN-wjuBnMP_IHgVDu7ye_fBto1iqj_AY2ngZz8Bbj_9Qxa_Q95Jc-hPOUpfa5bHorZ3OMu8dKog.png)

Configure the cluster settings, such as the cluster name, VPC, subnet.

![cswJtOMp5Qva1F683trLNnsZ1uNPmluCsWiE_3QQEHfEMEebB8Xsvitlk8lpiXh_l-13VQ5B4tzcwrF0v7HmVfL7h5mfNV1aYD0FKpAQJg](../../../../media/cswJtOMp5Qva1F683trLNnsZ1uNPmluCsWiE_3QQEHfEMEebB8Xsvitlk8lpiXh_l-13VQ5B4tzcwrF0v7HmVfL7h5mfNV1aYD0FKpAQJg.png)

Click on `Create`

![8JmnD8ZWtKo0D8auvXb1mUojvAyFoOmj4NtEsf2fEPwoWzDYdtjfBu1zzJO_yZJhana6dJP0NkViMmsbklzC9-jFz8HDpM75Ta_Hi0xU](../../../../media/8JmnD8ZWtKo0D8auvXb1mUojvAyFoOmj4NtEsf2fEPwoWzDYdtjfBu1zzJO_yZJhana6dJP0NkViMmsbklzC9-jFz8HDpM75Ta_Hi0xU.png)

Cluster is successfully created.

![d6ynm035AD9JjVf73XySkvFTVDxd95z2laX92ie-DnQlChVEFdvUE4bO4YYez4oWyP1D64sXxJno5bTlgTkMSoVJY679sLkdvpHo2X2N](../../../../media/d6ynm035AD9JjVf73XySkvFTVDxd95z2laX92ie-DnQlChVEFdvUE4bO4YYez4oWyP1D64sXxJno5bTlgTkMSoVJY679sLkdvpHo2X2N.png)

#### Create a task definition:
In the ECS service, click on `Task Definitions`, and then click on `Create new Task Definition`.

![L-l3DslzoFvXpABZ7vw1FevnAMlb9bX4p7QJ-OqUz4ngjoU2XSp_RzLUiSU5kcIVQ-hJLBpYypJSqd8x-Og58RAYzZKcQmpmyIpMtc7u](../../../../media/L-l3DslzoFvXpABZ7vw1FevnAMlb9bX4p7QJ-OqUz4ngjoU2XSp_RzLUiSU5kcIVQ-hJLBpYypJSqd8x-Og58RAYzZKcQmpmyIpMtc7u.png)

Give the task definition a name

Browse `Amazon ECR public gallery` and search for `nginx image`  choose `alpine` and copy that image url.

![Y1SIeMUPitS_bsSw-WpZ_hIi281nITSROPMS5de1rLqr6edK9TI62iNT-5VpEUZ5q9gFKbiaIdGERof5QqWTRU1e3LrRrBsYq_3rh_EL](../../../../media/Y1SIeMUPitS_bsSw-WpZ_hIi281nITSROPMS5de1rLqr6edK9TI62iNT-5VpEUZ5q9gFKbiaIdGERof5QqWTRU1e3LrRrBsYq_3rh_EL.png)

Back to task definition, Set the container name to "nginx", paste Image url from 'Amazon ECR public gallery' site. Specify the port mappings for HTTP , by setting the "Container port" to 80.
* Protocol: TCP
* Port name: nginx:80tcp
* App protocol: HTTP

![nuZGRceI-e7Q8yCGWSKyq3QI4_MzHk9NW64HfFagVgLnAk9cNy1jz1xk_Y2w3sLkgwW8Jl6QFFsuBGGrDMLzv8yMN4k_dgz_jzjOQmlmbg](../../../../media/nuZGRceI-e7Q8yCGWSKyq3QI4_MzHk9NW64HfFagVgLnAk9cNy1jz1xk_Y2w3sLkgwW8Jl6QFFsuBGGrDMLzv8yMN4k_dgz_jzjOQmlmbg.png)

Click on `Next`

![dsTISASXV7oshDsLbWtuMHQUtXLeHCRa1UtusMfHwf2E4j5ZJds4KaNEsoWpXuKe0OP70zg-6sI3LbNw7ifbML-KkRUH-_o_6k1w_4k](../../../../media/dsTISASXV7oshDsLbWtuMHQUtXLeHCRa1UtusMfHwf2E4j5ZJds4KaNEsoWpXuKe0OP70zg-6sI3LbNw7ifbML-KkRUH-_o_6k1w_4k.png)

Choose the `AWS Fargate(serverless)` on `App Environment`, Choose your Operating system 

Configure the task settings, such as the task memory and CPU limits, here CPU is .5vCPU and memory is 1GB.

![IRSx7lUcVxVhvMvSAsuDsTn5EtQRz39Bhfcju6eXXL2U197LLNkLxtgwyUmFQl9-9dB8DgfJaKMKw7D7y0N75clDv09lnMTssrveqFkn4g](../../../../media/IRSx7lUcVxVhvMvSAsuDsTn5EtQRz39Bhfcju6eXXL2U197LLNkLxtgwyUmFQl9-9dB8DgfJaKMKw7D7y0N75clDv09lnMTssrveqFkn4g.png)

![qM93UHFSCdsZALcOgKx5Iw-WE2kUVxoANm8WFoCFiqpXq0Y3T5XHVWuMvq4ZegWvotPRroQvp7uBRGR0kHnhFLN0P11uGpa33aQpo-fe](../../../../media/qM93UHFSCdsZALcOgKx5Iw-WE2kUVxoANm8WFoCFiqpXq0Y3T5XHVWuMvq4ZegWvotPRroQvp7uBRGR0kHnhFLN0P11uGpa33aQpo-fe.png)

Click on `Next` and then Click on `Create`

![nEyaYDpdE58-6I2XAXP53nPyUaJua7FzkbkKEmyhWhEhuCqDTDZp4Uv8ZR1RCSUhkOXAYMJKhQK5RnQun6HYlfaNJzmANBOcr_SA7O1A](../../../../media/nEyaYDpdE58-6I2XAXP53nPyUaJua7FzkbkKEmyhWhEhuCqDTDZp4Uv8ZR1RCSUhkOXAYMJKhQK5RnQun6HYlfaNJzmANBOcr_SA7O1A.png)

Task is successfully created.

![7QMieMK4B6V881DxKAEc_oSohho4XSH-kVkJ9cyFZNWwkZCHxUgB6xnQrjUB_snMPdHNlhJKMtqYKBfxu-DhhCYuOHGh9aq1BEqKDQVZuw](../../../../media/7QMieMK4B6V881DxKAEc_oSohho4XSH-kVkJ9cyFZNWwkZCHxUgB6xnQrjUB_snMPdHNlhJKMtqYKBfxu-DhhCYuOHGh9aq1BEqKDQVZuw.png)

#### Create a service:
In the ECS, click on `Clusters`, and select the cluster that you created.

![0djv7OqFdaekuxlP6fh4OqLnpDFlW28_bT5ra3-jELqEz8xuXt5_5SkzYptzG98ilgQx4oWdl0xYNZHaawSkAwL-2a7iaMEEqdKySEy1](../../../../media/0djv7OqFdaekuxlP6fh4OqLnpDFlW28_bT5ra3-jELqEz8xuXt5_5SkzYptzG98ilgQx4oWdl0xYNZHaawSkAwL-2a7iaMEEqdKySEy1.png)

Click on `Create Service`.

![dQfpfHa_MSKG8H3I-u5IRr7wWyvhz6mhG0KrFwiauKU3SH1r7pYq_d-nHC70fcJoaQRq8wx4LcHCRFCOt0MijXfqLatplt-RRNHIhJh6LQ](../../../../media/dQfpfHa_MSKG8H3I-u5IRr7wWyvhz6mhG0KrFwiauKU3SH1r7pYq_d-nHC70fcJoaQRq8wx4LcHCRFCOt0MijXfqLatplt-RRNHIhJh6LQ.png)

Choose the task definition that you created in above steps.

![KekJ3EFvtQj3bkZl2lEh-tCsoGnZl0WgzHJR-p-hdvHDpnLYXVNySQ30c6e68veXlRXRuhvooYgpJVG-X5YJ95svbdXxEtKBRdp9VfDH](../../../../media/KekJ3EFvtQj3bkZl2lEh-tCsoGnZl0WgzHJR-p-hdvHDpnLYXVNySQ30c6e68veXlRXRuhvooYgpJVG-X5YJ95svbdXxEtKBRdp9VfDH.png)

![0kae0-Fkr_BMUJYIEHkroTx_UvqBvSVyd1fNlmEBey-XGhmSqTRcUWtviKl5rjGkXCi3hOVKaWRrp0FS5f8VtxLZwOzc6Aez_kDe57s](../../../../media/0kae0-Fkr_BMUJYIEHkroTx_UvqBvSVyd1fNlmEBey-XGhmSqTRcUWtviKl5rjGkXCi3hOVKaWRrp0FS5f8VtxLZwOzc6Aez_kDe57s.png)

Configure the service settings, such as the VPC, subnet, and security group settings. Create a new security group.

![fwjWFN9YQm4L_g8E_w2nxbYUrOKM53CS2Tw4fYAwNEIll5fz3jAZ8o4UBlyhAAXbfZapasIrtp0Bz3gquYsXylcme8uJPZokaZ-Luiw](../../../../media/fwjWFN9YQm4L_g8E_w2nxbYUrOKM53CS2Tw4fYAwNEIll5fz3jAZ8o4UBlyhAAXbfZapasIrtp0Bz3gquYsXylcme8uJPZokaZ-Luiw.png)

Specify the port mappings for HTTP with port 80.

![jNWX8r7r8o4ZUH19v37rwQWdw28ZaQgCXW9sY6BR8IQqXOjQQheJJl-Iy6GClKuOw6hrHjV_aqvzJp6kZUkPyLjYLoThokFBbjvccrt5](../../../../media/jNWX8r7r8o4ZUH19v37rwQWdw28ZaQgCXW9sY6BR8IQqXOjQQheJJl-Iy6GClKuOw6hrHjV_aqvzJp6kZUkPyLjYLoThokFBbjvccrt5.png)

Click on 'Create'.

![DVA6syE3Bvn-BPt6UfCoY-Io8f6-qH6iRhn0-Gkg9_3UN7cgO2xfOOAMHz0hzDqASxtd8yHiv2bRqSkQiIYVkG9YjuX_Z7rsBxMnnOho](../../../../media/DVA6syE3Bvn-BPt6UfCoY-Io8f6-qH6iRhn0-Gkg9_3UN7cgO2xfOOAMHz0hzDqASxtd8yHiv2bRqSkQiIYVkG9YjuX_Z7rsBxMnnOho.png)

Service is successfully created.

![QDMCxfBrlYEbbBM5mKBccVzfMtflNHJg1ZpRGW0Trj8eCD79ylowFUXc7crqFoZjm65inACsjUsCpduZnfa74YldgTch62WRo_98uqS8BA](../../../../media/QDMCxfBrlYEbbBM5mKBccVzfMtflNHJg1ZpRGW0Trj8eCD79ylowFUXc7crqFoZjm65inACsjUsCpduZnfa74YldgTch62WRo_98uqS8BA.png)

Once the ECS service is running, test the Nginx container by accessing the public IP address of the Fargate task in a web browser. You can find the public IP address in the `Tasks` tab of the ECS service, under the `Configuration` section.

#### Test the Nginx container:
Click on `Cluster` that you created.

![rVJQkXaHdBbaDzng1J53ZAEq4FaUTEss4sS4frtPjBpUasHvMVCAorvoWIspN3-3dY8UmAeokxdS4pW_aGs2WJ-Dv77aLzt23_0DfuU](../../../../media/rVJQkXaHdBbaDzng1J53ZAEq4FaUTEss4sS4frtPjBpUasHvMVCAorvoWIspN3-3dY8UmAeokxdS4pW_aGs2WJ-Dv77aLzt23_0DfuU.png)

Click on `Task`.

![JHcB508b9nMTKL6XOgyLVpAT95qYNU7rSl9pJJ-nzcd7Gn6hqAjkpq_vMR7iV0L_7OVP79EImabruZ01_8qusJMu8jfExqcA4tz7NaSl](../../../../media/JHcB508b9nMTKL6XOgyLVpAT95qYNU7rSl9pJJ-nzcd7Gn6hqAjkpq_vMR7iV0L_7OVP79EImabruZ01_8qusJMu8jfExqcA4tz7NaSl.png)

In task, go to `configuration` section, there you can find public ip.

![hAk5L_apvpmIk3-LaW4qhYpukK-LybOPQAy-lw02X-KRTkAuvtka8NlbZFqFAYkaKGitDVNN5na194BNeDhYIfRT18kUEj4cTAxUxN1S](../../../../media/hAk5L_apvpmIk3-LaW4qhYpukK-LybOPQAy-lw02X-KRTkAuvtka8NlbZFqFAYkaKGitDVNN5na194BNeDhYIfRT18kUEj4cTAxUxN1S.png)

Browse Public IP address, you can see the default Nginx welcome page.

![wEZ8Tkfct6WiFk_XI0uFw4VUSSbs2zbXc9LCmDTyADmAueIIrrZN3Tk9YBmCLLuXYJja9drtRj_hsmSykeMpP_THVFVk9vTO6QVuq4uv](../../../../media/wEZ8Tkfct6WiFk_XI0uFw4VUSSbs2zbXc9LCmDTyADmAueIIrrZN3Tk9YBmCLLuXYJja9drtRj_hsmSykeMpP_THVFVk9vTO6QVuq4uv.png)


