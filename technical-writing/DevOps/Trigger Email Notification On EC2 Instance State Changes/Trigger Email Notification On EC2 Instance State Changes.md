## Trigger Email Notification On EC2 Instance State Changes Using SNS and Cloudwatch
* ### Create an SNS topic

1. Open the Amazon SNS console

![kVO6-VzFt8GmlY458w7IKK5UQxIEzk7r5JR6EDjBMM7SyGLJQAsYr4LQ7AT6G8qP2ait2Ac3WLwOVcRQrnmO3mDs46EEqmyLGIjTAQa-5G_aBpjquoQeU0s_LzP8zAsKqU365Rg](../../../media/kVO6-VzFt8GmlY458w7IKK5UQxIEzk7r5JR6EDjBMM7SyGLJQAsYr4LQ7AT6G8qP2ait2Ac3WLwOVcRQrnmO3mDs46EEqmyLGIjTAQa-5G_aBpjquoQeU0s_LzP8zAsKqU365Rg.png)

![q_W_-3p5ilGCIOpsN3uXXqkMGjSXnwOESv_HUBY4Ovton9EGFZV-tzAX8EGm1hUCtJMTt5X4fia_iO5UoeuxWhiNZI2h7vkz1Bez3MAKKQO89RrKMa6PwDrI3nTHrcJeQEYHqqg](../../../media/q_W_-3p5ilGCIOpsN3uXXqkMGjSXnwOESv_HUBY4Ovton9EGFZV-tzAX8EGm1hUCtJMTt5X4fia_iO5UoeuxWhiNZI2h7vkz1Bez3MAKKQO89RrKMa6PwDrI3nTHrcJeQEYHqqg.png)

2. Select `Topics` from the navigation pane.

![mjFQVTxRTTmYF6Bmdv9YfaM7c-NJwuSlY3pncbEKBVhIqJWQdVqT5ywcvZ2QO7Dyh8VAQj60GQDdXYybrxUB1_2UnLLZxvT0K9uH3jfRnpkjmQ_53IqXDvwyqkGta0u2me3QoFU](../../../media/mjFQVTxRTTmYF6Bmdv9YfaM7c-NJwuSlY3pncbEKBVhIqJWQdVqT5ywcvZ2QO7Dyh8VAQj60GQDdXYybrxUB1_2UnLLZxvT0K9uH3jfRnpkjmQ_53IqXDvwyqkGta0u2me3QoFU.png)
3. Click on `Create topic`.

![PhNALVLfdvZQ4ukSssyEdd27xpDs59HqaUMz64Xei7ltd1hnqCkLNfUpWV8KXGHlEHZ4eLCBnxYWGeVOt0uStJEcCl_YqYCeBcVyCVgHPbmGSxbD8VdVoGO2ik9tdckzwbhOtIo](../../../media/PhNALVLfdvZQ4ukSssyEdd27xpDs59HqaUMz64Xei7ltd1hnqCkLNfUpWV8KXGHlEHZ4eLCBnxYWGeVOt0uStJEcCl_YqYCeBcVyCVgHPbmGSxbD8VdVoGO2ik9tdckzwbhOtIo.png)
![GiE62aHMS8k78AFltVsGkU9190xdzMXjA3Vwa5ePifGYNMMnfQNoXNoU5vcRvZl7oh-LQjnbPBoR-Mwr9z7iToKpf4-GUckT_SfH6Obd2-wjMbmJdX00jxHUhMsSeet-CEf-Gv0](../../../media/GiE62aHMS8k78AFltVsGkU9190xdzMXjA3Vwa5ePifGYNMMnfQNoXNoU5vcRvZl7oh-LQjnbPBoR-Mwr9z7iToKpf4-GUckT_SfH6Obd2-wjMbmJdX00jxHUhMsSeet-CEf-Gv0.png)
4. For `Type`, Select the Standard.
5. For `Name`, enter a name for your topic.
6. For `Display name`, enter a display name for your topic.
7. On the Subscriptions tab, click Create subscription.

![OjFpW3nCV2c-uNKZBnWxrcHV6ConMmbFdi-IUFaJzjU3Zhx7YFQrZXAVbhG7QvoQ-38Ge-BvR1d9EW2cLg8WZ5IBNvtNJiZfVLxVOheoOWDO3xvwrPRi27qKCUuHk51kkAMWDOk](../../../media/OjFpW3nCV2c-uNKZBnWxrcHV6ConMmbFdi-IUFaJzjU3Zhx7YFQrZXAVbhG7QvoQ-38Ge-BvR1d9EW2cLg8WZ5IBNvtNJiZfVLxVOheoOWDO3xvwrPRi27qKCUuHk51kkAMWDOk.png)
8. You select the ARN of the topic that you have just created in Type ARN
9. For Protocol, Select Email.

![U7LuRX2FRffl38_CwFuDPlkvvYEv7lNTWcgdwSPtd4HLuopC_u0TnJwWa4o6SHbDAhVyw9f8AHxulwZarhQKg8CnY6U5ph8XSr_3VWl_WEcfw8PjYEFMqvHSj_Ta6vO12XepZcQ](../../../media/U7LuRX2FRffl38_CwFuDPlkvvYEv7lNTWcgdwSPtd4HLuopC_u0TnJwWa4o6SHbDAhVyw9f8AHxulwZarhQKg8CnY6U5ph8XSr_3VWl_WEcfw8PjYEFMqvHSj_Ta6vO12XepZcQ.png)
10. For Endpoint, enter the email address where you want to receive the notifications.

![kW_mRyLHCoaLqby-oBKDAYT1QKTReevGtj1cY88MtupyX7kn6_CSNWnuytzJe7XELR5yPaiIpaonqSZ90P2Vb-PBt5AMM-TBVkKIw1xYTmJ3tt-jAoHVhXj0JJhQIx3-BLb1kjw](../../../media/kW_mRyLHCoaLqby-oBKDAYT1QKTReevGtj1cY88MtupyX7kn6_CSNWnuytzJe7XELR5yPaiIpaonqSZ90P2Vb-PBt5AMM-TBVkKIw1xYTmJ3tt-jAoHVhXj0JJhQIx3-BLb1kjw.png)
![h5AcvwgCRdHuHsfwIHnlv6u4-mCMCn2bORQrzIuOUFZXwRxHmbwhh10BpwV31Qk7fWNEbIWezlI6iC7eYEPMJbXGOQMSrJevzQmu8_MHwbLag0vP6Ndwk_gZZ1cK3WHaMYvZTYQ](../../../media/h5AcvwgCRdHuHsfwIHnlv6u4-mCMCn2bORQrzIuOUFZXwRxHmbwhh10BpwV31Qk7fWNEbIWezlI6iC7eYEPMJbXGOQMSrJevzQmu8_MHwbLag0vP6Ndwk_gZZ1cK3WHaMYvZTYQ.png)
11. Click on the `Create subscription` tab and it is created.
12. A subscription confirmation email is sent to the address you entered.Click on the confirm link to confirm the subscription.
13. Below is the subscription confirmation page.

![2ms6InuHfYfrA1n32bgUyhnr3QYk8b5VkDVwOy-DKCeK2MNrkrCuhY5KJpkw_vEzlCmOB6_ErkudM6qPStzkgEBuzL69Awl4xJ6ZAut-n4MZKgOfWjrrkYhrFbTL7bMm5V7CiQ8](../../../media/2ms6InuHfYfrA1n32bgUyhnr3QYk8b5VkDVwOy-DKCeK2MNrkrCuhY5KJpkw_vEzlCmOB6_ErkudM6qPStzkgEBuzL69Awl4xJ6ZAut-n4MZKgOfWjrrkYhrFbTL7bMm5V7CiQ8.png)

### Creating a CloudWatch event:
1. Open the CloudWatch Console, and then go to Events > Rules > Create rule

![nV9-T46Ql2PoKTk8P3zgc4Pe00gqOg15hMT0_pYLE-Rs3WBgfJlsyp7jIAzSMceS3zcGGts1lwP0PizFYfiilDayMeM2YVQNOYq82Gxs4ow0l10W-M2qxC3mT2dZ0Z0EiYz69V0](../../../media/nV9-T46Ql2PoKTk8P3zgc4Pe00gqOg15hMT0_pYLE-Rs3WBgfJlsyp7jIAzSMceS3zcGGts1lwP0PizFYfiilDayMeM2YVQNOYq82Gxs4ow0l10W-M2qxC3mT2dZ0Z0EiYz69V0.png)
![5911nGrglRtswaqulX6q9m-fymeOP6TeIU7BXd5COFhaVcJFsnBLa0ThDBP5OxTZqT6TDYrsVUu38WSpjBpriMMqCDpLvX_PqGsXsAXZlDLOHDh5XZH-JplKHQcjt0n9zw6wri4](../../../media/5911nGrglRtswaqulX6q9m-fymeOP6TeIU7BXd5COFhaVcJFsnBLa0ThDBP5OxTZqT6TDYrsVUu38WSpjBpriMMqCDpLvX_PqGsXsAXZlDLOHDh5XZH-JplKHQcjt0n9zw6wri4.png)
![URuUTtVjJ6-XIMD1xPM8g3FfCIIRC61OhhAYs1PddtZcLaq8AnKslhzA93gSt9x7Xn4032Kp5BsdujdLSwVHwJP4YIxQR_r6lRjlZk_YAx3rrN_6mN0tggt8svAbJHm6zJHcI64](../../../media/URuUTtVjJ6-XIMD1xPM8g3FfCIIRC61OhhAYs1PddtZcLaq8AnKslhzA93gSt9x7Xn4032Kp5BsdujdLSwVHwJP4YIxQR_r6lRjlZk_YAx3rrN_6mN0tggt8svAbJHm6zJHcI64.png)
2. Click on `Create Rule`.
3. For Event Source, Click on `Event Pattern`.
4. For Service Name, Select `EC2`.
5. For Event Type, Select  `EC2 Instance State-change Notification`.
6. Tick on  `Any state`.
7. Tick on `Any instance`.

![I3efxT9q_tDfUmgDLyKQWLvHYtK-mmSN_837DrpgbmnSSXXA3kz_8wdTiBg7FBOq0t9JbfhXPkf1q50acn8-ZZgwDsVxe8Kw1KRxU2nTN2MsUAt9YhfCB7GYJgG5sgDZfM8RNWA](../../../media/I3efxT9q_tDfUmgDLyKQWLvHYtK-mmSN_837DrpgbmnSSXXA3kz_8wdTiBg7FBOq0t9JbfhXPkf1q50acn8-ZZgwDsVxe8Kw1KRxU2nTN2MsUAt9YhfCB7GYJgG5sgDZfM8RNWA.png)
![5L3Qem39EBDe6ktGhgETJW4nopYUGaNaWBD5i6weXIPPNtceKFz_j2ho4XG0Fpff5-VwVAZNc026JEbDSIbnGXeFT7YU48LliC5XuMptiiKAUllKM8SUwcAOk3cyzFZrFsBR25g](../../../media/5L3Qem39EBDe6ktGhgETJW4nopYUGaNaWBD5i6weXIPPNtceKFz_j2ho4XG0Fpff5-VwVAZNc026JEbDSIbnGXeFT7YU48LliC5XuMptiiKAUllKM8SUwcAOk3cyzFZrFsBR25g.png)
![hgyI88yTBGUyIFrxdeXc3IghnrLc2teqHmEvnL62rtgG3klf0Y--4GJCYaLUCLg1P-gKw2KJbfEdfne2yzytcEVkkBTZYqGxosfVNAszDzYoJYmRnWEOzS3GX0negxQqPIhbpTM](../../../media/hgyI88yTBGUyIFrxdeXc3IghnrLc2teqHmEvnL62rtgG3klf0Y--4GJCYaLUCLg1P-gKw2KJbfEdfne2yzytcEVkkBTZYqGxosfVNAszDzYoJYmRnWEOzS3GX0negxQqPIhbpTM.png)
![pstQ8K_GwWKL-uD5-OOkvhd56rE1yiPijKI_yTpn-2SyxUMkRmwDuMtvZGtNs1LV0gPkWaflWN7h7-dv2w1pHv_ibp-v3P6zeTHWSTOXsjPGvw3CvAMJJn78bvhP9EIuUVwjfbk](../../../media/pstQ8K_GwWKL-uD5-OOkvhd56rE1yiPijKI_yTpn-2SyxUMkRmwDuMtvZGtNs1LV0gPkWaflWN7h7-dv2w1pHv_ibp-v3P6zeTHWSTOXsjPGvw3CvAMJJn78bvhP9EIuUVwjfbk.png)

8. In the Targets section.
For Targets, select `SNS topic`.
9. For Topic, select the topic name that you created earlier.

![ct-lRafw_SGHkco6lqcn4m2g38KKpjz2Wc3OwAMhtJ1NXRztCET4DWuSbganxHAMMayzlAxiVJ8qr2giPXKU4d2YeuyAXdtSPDLAagPdqXkd-yi_xdqa7tB_Nz2PMl6azRWosbQ](../../../media/ct-lRafw_SGHkco6lqcn4m2g38KKpjz2Wc3OwAMhtJ1NXRztCET4DWuSbganxHAMMayzlAxiVJ8qr2giPXKU4d2YeuyAXdtSPDLAagPdqXkd-yi_xdqa7tB_Nz2PMl6azRWosbQ.png)
![dyjbgUdK5NTJkjMQYXnkS1R14IqNi2ciKDPJ0mkxu7qJxK1mUFlVPym5oFitn2guNOh-Xg3bcRd47YcP37R3t_EK--C44Z5gszMMV7elwr-zk4pGGJePJIoZ-JCEtBGcozGuE9Q](../../../media/dyjbgUdK5NTJkjMQYXnkS1R14IqNi2ciKDPJ0mkxu7qJxK1mUFlVPym5oFitn2guNOh-Xg3bcRd47YcP37R3t_EK--C44Z5gszMMV7elwr-zk4pGGJePJIoZ-JCEtBGcozGuE9Q.png)

10. For Configure input, select `Input Transformer`.
11. For Input Path, enter the following:


        {“instance-id”:”$.detail.instance-id”, “state”:”$.detail.state”, “time”:”$.time”, “region”:”$.region”, “account”:”$.account”}

12. For Input Template, enter the following:

        “At <time>, the status of your EC2 instance <instance-id> on account <account> in the AWS Region <region> has changed to <state>.”

![6cv4tz3IfL96iDRC142JiSLtvq46bzd80p-AY3_iZUBFKrmq3OTne6vLBUBC27jTfDtE-5OfoKukFanYn1e7B2A8ulDDpnmXhacJwIHFrmIwzEu-vSW58mCuuUCgQgYX4omvf7A](../../../media/6cv4tz3IfL96iDRC142JiSLtvq46bzd80p-AY3_iZUBFKrmq3OTne6vLBUBC27jTfDtE-5OfoKukFanYn1e7B2A8ulDDpnmXhacJwIHFrmIwzEu-vSW58mCuuUCgQgYX4omvf7A.png)

**Note**: The Input Template also allows custom inputs.

13. Click `Configure details`.
14. For Name, enter a rule name.
15. For Description, enter a rule description.

![s9aP0lIhsAyqFJt8lfhFacFu-DzNSbWwnow0zXo9ZAEbnfBQ3d3V1xbFRC6kHO9mU2IMhk2pDU34j12R8ZvyvvNoWSfXxqL4pVWSzeLZdB5tAmpd4kBmmXMKYEzOm7gpcuYMXbk](../../../media/s9aP0lIhsAyqFJt8lfhFacFu-DzNSbWwnow0zXo9ZAEbnfBQ3d3V1xbFRC6kHO9mU2IMhk2pDU34j12R8ZvyvvNoWSfXxqL4pVWSzeLZdB5tAmpd4kBmmXMKYEzOm7gpcuYMXbk.png)

16. Then click on `Create rule` to complete rule creation.
17. We can verify by changing the states of the instance in the EC2 console. Open the EC2 Console

![XV2JtqpZcWLLR0AbMxtmXFJvrZYMogxhAX_Kzf51eAtifvmomRZGKjoUNJjD_rVq744FnVufWLHDYuvD1EdNsW8RPKDa5PfLlDE35bBO0KfqL8fgQ6b_Fvxz6nsVE3zlu9nOCfA](../../../media/XV2JtqpZcWLLR0AbMxtmXFJvrZYMogxhAX_Kzf51eAtifvmomRZGKjoUNJjD_rVq744FnVufWLHDYuvD1EdNsW8RPKDa5PfLlDE35bBO0KfqL8fgQ6b_Fvxz6nsVE3zlu9nOCfA.png)

18. Select any instance and change the instance state manually. In this case we are Stopping an Instance.

![mRCv24h_dX4HVs7EnrNlCznxpNsNKc0dNOnUND_tQwMR5bB6ckcwFdnnkSdoCjnQkKq5qRkvX7H8Rc2RSsBS74H1bXb1XhGNhUdwdZN6OPyiYMTcOwrG7l0AOaAwbe1DzdO4fkI](../../../media/mRCv24h_dX4HVs7EnrNlCznxpNsNKc0dNOnUND_tQwMR5bB6ckcwFdnnkSdoCjnQkKq5qRkvX7H8Rc2RSsBS74H1bXb1XhGNhUdwdZN6OPyiYMTcOwrG7l0AOaAwbe1DzdO4fkI.png)
![NtJ8dhDJ4iC0c_E3pshwBeVpmn5adqJeapYihdI7dpZjSao4eUnNzb2XiS1UG6GULJmMYnZWwXRAll7SAHYwKvVZkrtJbE19tFgbz_wNY6ZrSThdf-1pgyjDn2r3vC5njf3e-do](../../../media/NtJ8dhDJ4iC0c_E3pshwBeVpmn5adqJeapYihdI7dpZjSao4eUnNzb2XiS1UG6GULJmMYnZWwXRAll7SAHYwKvVZkrtJbE19tFgbz_wNY6ZrSThdf-1pgyjDn2r3vC5njf3e-do.png)
![CJ45NF3t3EBlACIpQX6QJ-3xJh8giIpT1l97-KzW329np_yQ4GtOX_G5u3V1kXir55WWPYAjI94ditWqgDe205J-BtWPSHrLZPAqBq8y67U5j88tbVh9OOigoizO_dy2d2-OI2c](../../../media/CJ45NF3t3EBlACIpQX6QJ-3xJh8giIpT1l97-KzW329np_yQ4GtOX_G5u3V1kXir55WWPYAjI94ditWqgDe205J-BtWPSHrLZPAqBq8y67U5j88tbVh9OOigoizO_dy2d2-OI2c.png)

19. When the state of the instance is changed into “Stopping” from “running”. An Email alert is sent to our email address given in the SNS topic.

![Screen-Shot-2021-11-30-at-11.14.37-AM-1024x235](../../../media/Screen-Shot-2021-11-30-at-11.14.37-AM-1024x235.png)
![glqmaebsLkqwbJkKdSAhITDFyCS4D5YStqyrwrbt4ZJ7m7geR3LwBTAtlaXe-k_q83ilEPOH41A9CJZnzmk55aiPf0zPwyEHHYME2dFA2DAPngf06FEO90u6yfMYc7WvnSPYwoI](../../../media/glqmaebsLkqwbJkKdSAhITDFyCS4D5YStqyrwrbt4ZJ7m7geR3LwBTAtlaXe-k_q83ilEPOH41A9CJZnzmk55aiPf0zPwyEHHYME2dFA2DAPngf06FEO90u6yfMYc7WvnSPYwoI.png)

20. And When the instance state changes to “Stopped” from “Stopping”. 

![fLx9DmzgIy77_k8SMAsbWvpyEh_a_lA2BN1rSXr0X0993itTfosE_dFK7HwApv71ZBQE5QIhLEKkP50Yv8WgQTaudSxJFtFiZ_62Qdar6f7_o9VcWihtPcHd_jSxHIpBDYs-xmQ](../../../media/fLx9DmzgIy77_k8SMAsbWvpyEh_a_lA2BN1rSXr0X0993itTfosE_dFK7HwApv71ZBQE5QIhLEKkP50Yv8WgQTaudSxJFtFiZ_62Qdar6f7_o9VcWihtPcHd_jSxHIpBDYs-xmQ.png)

21. Then again we get an Email alert confirming the same. 

![GlyDOzDz8JAD-XOccjByS_9-GYRNN6AErKMI36oWFEibjUSRG59huHzZ-IQ1PFeaLzcc7VvSY5kVCeWk7zt-YGexQTEjwCZevlj01mLP4RyiCkO8W-BI4vfuAEEqSCqE_jQ5sAI](../../../media/GlyDOzDz8JAD-XOccjByS_9-GYRNN6AErKMI36oWFEibjUSRG59huHzZ-IQ1PFeaLzcc7VvSY5kVCeWk7zt-YGexQTEjwCZevlj01mLP4RyiCkO8W-BI4vfuAEEqSCqE_jQ5sAI.png)