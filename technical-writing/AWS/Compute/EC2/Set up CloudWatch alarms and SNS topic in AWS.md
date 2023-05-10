## Set up CloudWatch alarms and SNS topic in AWS

#### What is Amazon CloudWatch?
Amazon CloudWatch monitors your Amazon Web Services (AWS) resources and the applications you run on AWS in real time. You can use CloudWatch to collect and track metrics, which are variables you can measure for your resources and applications.

#### What is Amazon SNS?
Amazon Simple Notification Service is a notification service provided as part of Amazon Web Services since 2010. It provides a low-cost infrastructure for mass delivery of messages, predominantly to mobile users.

#### Task :
Create a CloudWatch alarm that monitors your billing and send an email to you when a it reaches $2.

#### To enable the monitoring of estimated charges
Open the AWS Billing console at https://console.aws.amazon.com/billing/.

In the navigation pane, choose Billing Preferences.

Choose Receive Billing Alerts.

Choose Save preferences.

![acE9NL8pPW_QbU0t5-w84x9X8-wUkM7QKZ0cWqVnZw5pid7JUo2mNGMpXX7QtxPiOfnhBlrFBYpcwOglokyzlqAy_ID5iqkigG2bylBK](../../../../media/acE9NL8pPW_QbU0t5-w84x9X8-wUkM7QKZ0cWqVnZw5pid7JUo2mNGMpXX7QtxPiOfnhBlrFBYpcwOglokyzlqAy_ID5iqkigG2bylBK.png)

![1OPCyrwERErZfIK8rfVIYWBI4op2O2WX4pJt3po6BErf-OmB1PQYhJcjuMSNAQHTfvOFjQos-MDVxj3Evk0cXBfcVA0fzg1IdjJbmrag](../../../../media/1OPCyrwERErZfIK8rfVIYWBI4op2O2WX4pJt3po6BErf-OmB1PQYhJcjuMSNAQHTfvOFjQos-MDVxj3Evk0cXBfcVA0fzg1IdjJbmrag.png)

#### Creating a billing alarm

Open the CloudWatch console

In the navigation pane, choose Alarms, and then choose All alarms.

Choose Create alarm.

![rBgP1BdqKMibiGTFxK6jbyWpKP3SnGXkWVzDxdhjM-WgnDE3oJ_UO5MBNqJT_2FcybE-Jf7-lKViZA5fpHnWnOrTsLuGSOO70fddr0v9](../../../../media/rBgP1BdqKMibiGTFxK6jbyWpKP3SnGXkWVzDxdhjM-WgnDE3oJ_UO5MBNqJT_2FcybE-Jf7-lKViZA5fpHnWnOrTsLuGSOO70fddr0v9.png)

Choose Select metric.

![fUiGw-tqJMDeSz-URzWxVNMCt-rW7Vb9h3EeNp71Nx93SqrOWY9b5UBI3L0TCYLeLgCxNq-lltKItBQnvpy6BFGqJAgyRIdt0le_XXA](../../../../media/fUiGw-tqJMDeSz-URzWxVNMCt-rW7Vb9h3EeNp71Nx93SqrOWY9b5UBI3L0TCYLeLgCxNq-lltKItBQnvpy6BFGqJAgyRIdt0le_XXA.png)

In Browse, choose Billing, and then choose Total Estimated Charge.

![Gj16u5naCczlb5VxEdhqbGXD86W1c8OxZhJXfLn2SC5oq_d5ynrLb6NIxMDg7TeiEIyDnYq70t_rl0ZHq1t8CcaMxFIQNFSka5fMzN7P](../../../../media/Gj16u5naCczlb5VxEdhqbGXD86W1c8OxZhJXfLn2SC5oq_d5ynrLb6NIxMDg7TeiEIyDnYq70t_rl0ZHq1t8CcaMxFIQNFSka5fMzN7P.png)

![q-YCFMDi9ULe_A_TzjWqguAEE4BnhkOrPl2y5SXrVdTXg8Zmp6FXJ1z4wWeynJAjl-mbtjqI_csq7SNIhhjBd6SW5VaPdawopvGXEOgTMw](../../../../media/q-YCFMDi9ULe_A_TzjWqguAEE4BnhkOrPl2y5SXrVdTXg8Zmp6FXJ1z4wWeynJAjl-mbtjqI_csq7SNIhhjBd6SW5VaPdawopvGXEOgTMw.png)

Select the box for the EstimatedCharges metric, and then choose Select metric.

![FuhwxZ18_JLnNM_zVC6Z--FKGZKWmgADHOTWNe-rR4S2uZ5z2Is2SO3Wi6LArReObJwhQTx1lcX4gcHCCQN9_hfuzzw25xZU4njXm3FE](../../../../media/FuhwxZ18_JLnNM_zVC6Z--FKGZKWmgADHOTWNe-rR4S2uZ5z2Is2SO3Wi6LArReObJwhQTx1lcX4gcHCCQN9_hfuzzw25xZU4njXm3FE.png)

For Statistic, choose Maximum.

For Period, choose 6 hours.

![MuNaVO8KgrpeKK_QqSKDqXkDxkIJsNhNHbR3LH4yrpdzXbNfoJPG88v1zYQz7SM2xevoftPwFHhVWvce0P5QXdyViZ5IuF7u_seep9t1](../../../../media/MuNaVO8KgrpeKK_QqSKDqXkDxkIJsNhNHbR3LH4yrpdzXbNfoJPG88v1zYQz7SM2xevoftPwFHhVWvce0P5QXdyViZ5IuF7u_seep9t1.png)

For Threshold type, choose Static.

For Whenever EstimatedCharges is, choose Greater.

define a threshold value that triggers your alarm. here threshold value is 2$.

![xhryzws5T3grelYDdhuc9qEth7QBpvtcJbLEAdvjzp2FJnQs7yXlnf3-QlcLs5nvnldC4y-zrBlq3HkDuT5kfwNqljbXrQr-cdIYPiY](../../../../media/xhryzws5T3grelYDdhuc9qEth7QBpvtcJbLEAdvjzp2FJnQs7yXlnf3-QlcLs5nvnldC4y-zrBlq3HkDuT5kfwNqljbXrQr-cdIYPiY.png)

Under Notification, specify an Amazon SNS topic to be notified when your alarm is in the ALARM state.

You can select an existing Amazon SNS topic or create a new Amazon SNS topic by selecting 'Create new topic'.

![U0ZpLAV8uASCOI6ggI85Luh6VWP-eST4xsT0Hd8wJNDbU5C0Y7-5ACRKnALy6_yrITZimFU2m3sNGmb1EEcUXCakHTVxM1rZlLttG7A](../../../../media/U0ZpLAV8uASCOI6ggI85Luh6VWP-eST4xsT0Hd8wJNDbU5C0Y7-5ACRKnALy6_yrITZimFU2m3sNGmb1EEcUXCakHTVxM1rZlLttG7A.png)

If you want your alarm to send multiple notifications for the same alarm state or for different alarm states, 

choose Add notification.

choose Next.

![5Mif23s-UN2-f1mwxp6cpvry49-C5CEOecZYheZ7Pt_bTco2MHZVxEmCp2kpl06PRLEJd2IMEZgBpbPeEwBOb2ovcert0exG1VZP0D8](../../../../media/5Mif23s-UN2-f1mwxp6cpvry49-C5CEOecZYheZ7Pt_bTco2MHZVxEmCp2kpl06PRLEJd2IMEZgBpbPeEwBOb2ovcert0exG1VZP0D8.png)

Under Name and description, enter a name for your alarm.

![kEHEShFgXzdZnDIqGqWjOI4uQ9-9Oysq_shA6a11y-FJ3BiRVECarYb5S1bkvhtXj5D7zQNRL5plbnMcyjqxEw1TpWEGT5zms_OhW1U](../../../../media/kEHEShFgXzdZnDIqGqWjOI4uQ9-9Oysq_shA6a11y-FJ3BiRVECarYb5S1bkvhtXj5D7zQNRL5plbnMcyjqxEw1TpWEGT5zms_OhW1U.png)

Under Preview and create, make sure that your configuration is correct, and then choose Create alarm.

![fhg-57-82Yg7lxi7-hcC4UwXiq6XaVgC0KZ6eHR9NJheNSno4bgusApaH4gfgQVnF3TA8-ALlmsEXur28ExIaDLGd1gglWMiG-5BxdCr](../../../../media/fhg-57-82Yg7lxi7-hcC4UwXiq6XaVgC0KZ6eHR9NJheNSno4bgusApaH4gfgQVnF3TA8-ALlmsEXur28ExIaDLGd1gglWMiG-5BxdCr.png)

![asMrFb41DTUmI4g8w7G1tBpWhiGtTBitA8vdEI9BuovZp_hJ62KqQ5VdlCprSrODCLVPuS4SUGYM1rJhbcqwGS5gCyu5NVHPFpMcep6N](../../../../media/asMrFb41DTUmI4g8w7G1tBpWhiGtTBitA8vdEI9BuovZp_hJ62KqQ5VdlCprSrODCLVPuS4SUGYM1rJhbcqwGS5gCyu5NVHPFpMcep6N.png)

![ZVq_8pNqdadwnInKmpXLMKEG1k4HWVIAVf9rHzxMLBZIe2oIpGaU8c_X_lrIo7qvW53w5iFUo_Tl-O1eMaAvL9jSO6nmk1AD9pm4mzo](../../../../media/ZVq_8pNqdadwnInKmpXLMKEG1k4HWVIAVf9rHzxMLBZIe2oIpGaU8c_X_lrIo7qvW53w5iFUo_Tl-O1eMaAvL9jSO6nmk1AD9pm4mzo.png)

billing alarm is created.

![4R-NGCQw73kEl_FmeFmLSr3BAmr31U4xhJJ-ptAUPV3sTeFm4ERRlTG_XIM1uzZc8MWveDig2gg1IonwG8r1evTVnm4vW1pZPvIy43s-Zg](../../../../media/4R-NGCQw73kEl_FmeFmLSr3BAmr31U4xhJJ-ptAUPV3sTeFm4ERRlTG_XIM1uzZc8MWveDig2gg1IonwG8r1evTVnm4vW1pZPvIy43s-Zg.png)

![8u6PGGvU3ToMcnaTUAW0g9-2YaKFo976Aajd5vfp4SHShPq-ALtp-wgGjk0k_JmpxySqFiujtlzEJhTNhBlSsZgnCpdJAUCmmzaLJ2k0](../../../../media/8u6PGGvU3ToMcnaTUAW0g9-2YaKFo976Aajd5vfp4SHShPq-ALtp-wgGjk0k_JmpxySqFiujtlzEJhTNhBlSsZgnCpdJAUCmmzaLJ2k0.png)