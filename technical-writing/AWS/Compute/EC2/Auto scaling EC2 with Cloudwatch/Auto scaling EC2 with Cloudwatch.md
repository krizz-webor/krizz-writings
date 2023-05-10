# Auto scaling EC2 with Cloudwatch
Launch your EC2 instance

When the instance has stated running, tick on the instance, click on the `Action` drop down

Select `Image and template` and click on `create template from instance`

![5_JwwQEtqCjsAz6-Yvbf-plYNF_SSKVL6mUL0Q5l5YKOrtdG3evyvhNVY__8qo2oEb_JHXA27uxawCi_6RfVvrAUbxNw1Dt_Zt7w_dg](../../../../../media/5_JwwQEtqCjsAz6-Yvbf-plYNF_SSKVL6mUL0Q5l5YKOrtdG3evyvhNVY__8qo2oEb_JHXA27uxawCi_6RfVvrAUbxNw1Dt_Zt7w_dg.png)

On the `Launch template name`, add a name to the template

![38pyMlaULOsogye8KE6ExMdL-g-hXGqejgQH99WVEZ2RFSvOEYGIw2llBg6UilW5PiFY6bGZ3k_KAJJbWV-pu6tvfv885a1upeBF1VUKZw](../../../../../media/38pyMlaULOsogye8KE6ExMdL-g-hXGqejgQH99WVEZ2RFSvOEYGIw2llBg6UilW5PiFY6bGZ3k_KAJJbWV-pu6tvfv885a1upeBF1VUKZw.png)

You may also give a description(Optional)

Click `Create launch template`

![TsPp2fn6KJPfAiani0Hep2zNchXRV4T_ni_G-kE0U2srwaGaiTEYNeEAy1LXxuqhKh9Vk_hp8VLstb6vw6jzgxqQzEsIX7_Yfg9iHQ6Ysg](../../../../../media/TsPp2fn6KJPfAiani0Hep2zNchXRV4T_ni_G-kE0U2srwaGaiTEYNeEAy1LXxuqhKh9Vk_hp8VLstb6vw6jzgxqQzEsIX7_Yfg9iHQ6Ysg.png)

Scroll down, Click on the `Create Auto Scaling group` button to start the creation process.

![9R-dd7aBIOKOOFIcnQAy6i-x5cTYK8e_LTmCfBMwoFqMSAjeBY1SYFocFuP5MOsjRFeuqDpkXhzfqUHKygkOcrVpLQNFzf7bDnE19Dss](../../../../../media/9R-dd7aBIOKOOFIcnQAy6i-x5cTYK8e_LTmCfBMwoFqMSAjeBY1SYFocFuP5MOsjRFeuqDpkXhzfqUHKygkOcrVpLQNFzf7bDnE19Dss.png)

Give the Auto scaling group a name

Select the launch template to use for the instances in the group.

![Lz7X_0ws4jBECEB6HmmAbDzPUH5rbGw98BaX_8EtsD1MvBTVyWI9Z8ANsj6vLfTE0LvdF9vRDEN5WyEW7CTDbYKiHYeNp1OiIWhMuBfS](../../../../../media/Lz7X_0ws4jBECEB6HmmAbDzPUH5rbGw98BaX_8EtsD1MvBTVyWI9Z8ANsj6vLfTE0LvdF9vRDEN5WyEW7CTDbYKiHYeNp1OiIWhMuBfS-2.png)

Choose the instance type and other configuration details such as VPC, subnet, security groups, and storage.

![EbZM4klbV5uetoX7UX5ubiZV3H63PN_QOtzxSLBvqzvGhYMasDQrCISV8age4wQprVc5j1xx9TutYlC3lE0UzyQv0YIjYDUOgdFIftbe](../../../../../media/EbZM4klbV5uetoX7UX5ubiZV3H63PN_QOtzxSLBvqzvGhYMasDQrCISV8age4wQprVc5j1xx9TutYlC3lE0UzyQv0YIjYDUOgdFIftbe.png)

![MdjxOXs9uVbDvPSWUPzg8HECCQzicwJZ8gho586Ao5Wm6Y2Xf9FO4qT_GfSsVsDo-Wj4yuvdymKXoqmXDgFvXpVRXPM3dseaHDEQipWE](../../../../../media/MdjxOXs9uVbDvPSWUPzg8HECCQzicwJZ8gho586Ao5Wm6Y2Xf9FO4qT_GfSsVsDo-Wj4yuvdymKXoqmXDgFvXpVRXPM3dseaHDEQipWE.png)

If you have a load balancer you can add it and it's target group by ticking `Attach to an existing load balancer`

![GvQtfyUSyDYujVvhCJvPkxD4fQI0aZKhMlpuZZKfmQwrvCxaZJonFmkbEa8ALvRCyAb23lDGwLliA4z_HJvworsaAoSf9ZuEEeFxsWNl](../../../../../media/GvQtfyUSyDYujVvhCJvPkxD4fQI0aZKhMlpuZZKfmQwrvCxaZJonFmkbEa8ALvRCyAb23lDGwLliA4z_HJvworsaAoSf9ZuEEeFxsWNl.png)

![fX_BRkBLb6GNb7gNhYpSkbdH3d_DAw1RQoAkHAzsG5wH5zA1aOGKU5fzhDku7dDcWdBxIBWXrnaa4y4fODk3nhXBG84SM-QyeWGr5xM](../../../../../media/fX_BRkBLb6GNb7gNhYpSkbdH3d_DAw1RQoAkHAzsG5wH5zA1aOGKU5fzhDku7dDcWdBxIBWXrnaa4y4fODk3nhXBG84SM-QyeWGr5xM.png)

Scroll down and click `Next`

Set up the scaling policies to determine when to launch new instances. configure desired, minimum and maximum capacity of instance.

![GM1xYknQF5unjBO5ZC1ZH0ipx9n4OjZio4Md1HBURCxXeEWBzFdhXa8Twn6VEXVI7ES-lop8iuCvT9ifXdYDn7PYeNse2NKUpSi4QNQ](../../../../../media/GM1xYknQF5unjBO5ZC1ZH0ipx9n4OjZio4Md1HBURCxXeEWBzFdhXa8Twn6VEXVI7ES-lop8iuCvT9ifXdYDn7PYeNse2NKUpSi4QNQ.png)

Select `Target tracking scaling policy` and choose `metric type` to CPU utilization which will create an alarm.

![HFw6DULprglKKCJR773R-xvjT6xnMtCsNJ0T6GqMwkNQihRWYLoK9L2IIyljE-eI03WkR93IHlNIfkR5ONDvtc5U4QORNEDyobJjiX8](../../../../../media/HFw6DULprglKKCJR773R-xvjT6xnMtCsNJ0T6GqMwkNQihRWYLoK9L2IIyljE-eI03WkR93IHlNIfkR5ONDvtc5U4QORNEDyobJjiX8.png)

Set a Target value for the server

Click on `Create auto scaling group`

![ySNUUnT0L2DcJqcxE1JR1Fg706m8DpwitXn4AtGgD55JyM-VR-TAUolTni5hZaW5ioVErgqfpXMB4GKhFYosjpJ_EVbqK3pulpVcL5Bz](../../../../../media/ySNUUnT0L2DcJqcxE1JR1Fg706m8DpwitXn4AtGgD55JyM-VR-TAUolTni5hZaW5ioVErgqfpXMB4GKhFYosjpJ_EVbqK3pulpVcL5Bz.png)

Auto-scaling group is created.

![ZhdVlO-RRh9gQZK8fOXG4PzL0huzcbMIxhrWbKzKQmUnAALUAWqeHpLBqQRygV5AWS_7wL9CGnXlAE4J8tWwbAux4pp0kBnGyxTI1x-8Eg](../../../../../media/ZhdVlO-RRh9gQZK8fOXG4PzL0huzcbMIxhrWbKzKQmUnAALUAWqeHpLBqQRygV5AWS_7wL9CGnXlAE4J8tWwbAux4pp0kBnGyxTI1x-8Eg.png)

### Use Amazon CloudWatch to monitor the performance of the Auto Scaling group and the EC2 instances and troubleshoot any issues that arise.

Once the alarm is set up, it will start monitoring the specified metric for the Auto Scaling group.

If the metric exceeds the threshold that you have set, the alarm will be triggered and take the action that you have specified.

Target tracking policy in autoscaling create 2 alarms with 2 different conditions.


![kWKx7mVk3b_cU6I-gSfx6hF0u1ZZLupb4dRlV6F8smX6vBLDq9qalkkteyDKRUgjBF1EZmVhKlReD55vZirZtF3LnifV2yoBh8hOskRbaA](../../../../../media/kWKx7mVk3b_cU6I-gSfx6hF0u1ZZLupb4dRlV6F8smX6vBLDq9qalkkteyDKRUgjBF1EZmVhKlReD55vZirZtF3LnifV2yoBh8hOskRbaA.png)

Go to auto-scaling group that we created, Click on the `Monitoring` tab and enable `Auto scaling group metric`

![j8-N-tlfqKy4_BI3btXU8rjlVQSYiwIsPWaFgraA5cTz4L7iyqH7d9Bd9jMO6qGkrvEXUmF1Tg2lRGL_nMW7CRhQTgcMMxPeWteLUN6e](../../../../../media/j8-N-tlfqKy4_BI3btXU8rjlVQSYiwIsPWaFgraA5cTz4L7iyqH7d9Bd9jMO6qGkrvEXUmF1Tg2lRGL_nMW7CRhQTgcMMxPeWteLUN6e.png)

You can create alarm by going to CloudWatch dashboard.

Click on the `Create Alarm` button to set up an alarm.

![_1x7H2OXG76Q9QPs5QefE3per4lfO3V42OT4OJd0kC2VPNmebLr149Mo_4fjP1TcukR4agtOkFWa8qQa_xJfGm0xepGMBj3WCn772VEa](../../../../../media/_1x7H2OXG76Q9QPs5QefE3per4lfO3V42OT4OJd0kC2VPNmebLr149Mo_4fjP1TcukR4agtOkFWa8qQa_xJfGm0xepGMBj3WCn772VEa.png)

Click on `Select metric`

Click on "EC2".

![ZFSf6vQ5HoXqh5C2ah2h-tD4o6AgEilXqE3FtgzF5AV0k7z_sUOwCjzkxYzCki__lbRBbqtY1WdOm0erx0uY7DINLnnFJ4c-ea4l42LG](../../../../../media/ZFSf6vQ5HoXqh5C2ah2h-tD4o6AgEilXqE3FtgzF5AV0k7z_sUOwCjzkxYzCki__lbRBbqtY1WdOm0erx0uY7DINLnnFJ4c-ea4l42LG.png)

Click on 'By Auto Scaling Group'.

![VPDQmxatUSBMNeuhLJUDWwoHlaBYWivb4WJDeOcxQeOITPcbBnLIyftJqMt6nbPNmYngLpeGhTj2zDG4D-XzTDQo3muD8wcolN01rVEPWw](../../../../../media/VPDQmxatUSBMNeuhLJUDWwoHlaBYWivb4WJDeOcxQeOITPcbBnLIyftJqMt6nbPNmYngLpeGhTj2zDG4D-XzTDQo3muD8wcolN01rVEPWw.png)

Choose the metric you want to monitor. You can search for the metric by name.
Choose `CPUUtilisation`

![KoN0KC1Apfenw9b2QbjLd8dW-bfbBx7TMcvIQ-iGQRX9wioTApuUQ5vAbgIbellPcoGmxD5GGvVGeF078yIB8kbC2CjRpiMtVEffuJekKw](../../../../../media/KoN0KC1Apfenw9b2QbjLd8dW-bfbBx7TMcvIQ-iGQRX9wioTApuUQ5vAbgIbellPcoGmxD5GGvVGeF078yIB8kbC2CjRpiMtVEffuJekKw.png)

Click `Select a single metric to continue`

Once the alarm is created, it will start monitoring the specified metric and trigger the configured action if the conditions are met. You can view the status of the alarm in the CloudWatch console, and manage and update the alarm settings as needed.
