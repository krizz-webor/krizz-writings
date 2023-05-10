## Terraform create EC2 Instance

### AWS CLI installed
The AWS Command Line Interface (AWS CLI) is a unified tool to manage your AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.
1. Create an EC2 instance.
2. SSH into EC2 instance
3. Install AWS CLI

Run,

    sudo apt install awscli

![TjwKALXIIqVniuIPROPZIsDohBDAwbWKtNTMkWAEZnsU8biJm2jJQimhTAU9CDqctXkJZ1XAvYz6Iwq7bNmnnU5sMvS01b2aTW_K8lnS](../../media/TjwKALXIIqVniuIPROPZIsDohBDAwbWKtNTMkWAEZnsU8biJm2jJQimhTAU9CDqctXkJZ1XAvYz6Iwq7bNmnnU5sMvS01b2aTW_K8lnS.png)

Check aws cli version

![B7CJEJl1CiNFAWgpSPCrxR2rtwIFPT7x7MAWEbI5iLTQp9LWfPW6-SLA3H83i1jdKUzHIhpeuSXN1LfkUO1NdMXfqsAcJWIFEtpulUY](../../media/B7CJEJl1CiNFAWgpSPCrxR2rtwIFPT7x7MAWEbI5iLTQp9LWfPW6-SLA3H83i1jdKUzHIhpeuSXN1LfkUO1NdMXfqsAcJWIFEtpulUY.png)

### AWS IAM user
IAM (Identity Access Management) AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.

Create IAM user.

![EWLGDcP-rvDEyyRzmZ1EinxeECNAxxqdmNviQzf84IGSwTRt8LKK5xFJNWzOg0bk-XKds7TgDty7AcJdXXie-kPX-WoAgPmg3Mp45vjP](../../media/EWLGDcP-rvDEyyRzmZ1EinxeECNAxxqdmNviQzf84IGSwTRt8LKK5xFJNWzOg0bk-XKds7TgDty7AcJdXXie-kPX-WoAgPmg3Mp45vjP.png)

Create Access key for IAM user.

Click on 'Create access key'

![M3GanJwymprWdD-Zn2F0UqT4jHPkzD7Uja7TG3AL2smaNRfPYRDlQc2gjU6_0-V60qb-X5dBJQWaidm157JcR6oXAOZKTZmJUOTQLrXFTA](../../media/M3GanJwymprWdD-Zn2F0UqT4jHPkzD7Uja7TG3AL2smaNRfPYRDlQc2gjU6_0-V60qb-X5dBJQWaidm157JcR6oXAOZKTZmJUOTQLrXFTA.png)

Select 'command line interface'

![v0QamvUuY2FX5tCGZBb7zotLZcRujKz7T9zp7CFTAQIIzx0uE6_qtrC4cwrqKE_5XGciLworyCrDeEJjxTdVl9kW_n1a36wrlpd1uESo](../../media/v0QamvUuY2FX5tCGZBb7zotLZcRujKz7T9zp7CFTAQIIzx0uE6_qtrC4cwrqKE_5XGciLworyCrDeEJjxTdVl9kW_n1a36wrlpd1uESo.png)

![2Dr8XiFJPgNl1kTiyIRfjnou7vhLSrM5RxfGZ0ibxMUpOIc0Yl4QJBveki4-lHFLAOClFm3ZmT41nSQivj2npSGnNvK_M79mraptgCKu](../../media/2Dr8XiFJPgNl1kTiyIRfjnou7vhLSrM5RxfGZ0ibxMUpOIc0Yl4QJBveki4-lHFLAOClFm3ZmT41nSQivj2npSGnNvK_M79mraptgCKu.png)

![6MK3H9RHbm_cFKH2fsB3iHpCmEXcz_5WxaMsmbQ55VWj0sHJrkKCD9j4IYbeNB8VXQfwJPrCnifq3WJ5hWtVbMPOEu8OFFKtN8mFrDA](../../media/6MK3H9RHbm_cFKH2fsB3iHpCmEXcz_5WxaMsmbQ55VWj0sHJrkKCD9j4IYbeNB8VXQfwJPrCnifq3WJ5hWtVbMPOEu8OFFKtN8mFrDA.png)

In order to connect your AWS account and Terraform, you need the access keys and secret access keys exported to your machine.

    export AWS_ACCESS_KEY_ID=<access key>
    export AWS_SECRET_ACCESS_KEY=<secret access key>

![Kf__pvnQsdm25QBP35Hz5aOJODicwviz00_2OjpHMH1VTZTjazMSK7SGRa6e93gO1I996PNgtLM6Gn369BqxdTtJ6Z3ftUtyUDZnFmEx9g](../../media/Kf__pvnQsdm25QBP35Hz5aOJODicwviz00_2OjpHMH1VTZTjazMSK7SGRa6e93gO1I996PNgtLM6Gn369BqxdTtJ6Z3ftUtyUDZnFmEx9g.png)

### Install required providers

    terraform {
     required_providers {
            aws = {
            source  = "hashicorp/aws"
            version = "~> 4.16"
    }
    }
            required_version = ">= 1.2.0"
    }

The **terraform** block defines the version of Terraform that is required to execute this configuration. In this case, it specifies that the Terraform version must be >= **1.2.0**.

The **required_providers** block declares the AWS provider and its version that Terraform will use for the resources defined in this configuration. In this case, it declares the AWS provider with the source **hashicorp/aws** and specifies that the version of the provider should be **~> 4.16**, which means any version of the AWS provider greater than or equal to 4.16 and less than 5.0 will be acceptable.
Add the region where you want your instances to be

    provider "aws" {
    region = "ap-south-1"
    }

![BEtDJ8fnyc4YXOeukNyzkghz5FKzx7rELxOdw8cpxro4oJOSIPtNcVTXRYxrxiY3AE7Z_Qifk38uC7685XSPspnLtacaVOu6FKF2XAhA](../../media/BEtDJ8fnyc4YXOeukNyzkghz5FKzx7rELxOdw8cpxro4oJOSIPtNcVTXRYxrxiY3AE7Z_Qifk38uC7685XSPspnLtacaVOu6FKF2XAhA.png)

Provision an AWS EC2 instance using Terraform

    resource "aws_instance" "aws_ec2_demo" {
            count = 2
            ami = "ami-0f8ca728008ff5af4"
            instance_type = "t2.micro"
            tags = {
                Name = "TerraformTestInstance"
      }
    }

The resource block has a resource type of "aws_instance" and a resource name of "aws_ec2_demo". The count parameter is set to 2, which means that two instances will be created.

The ami parameter specifies the Amazon Machine Image (AMI) to use for the instances. In this case, the AMI ID is "ami-0f8ca728008ff5af4".

The instance_type parameter specifies the type of instance to create. In this case, the instance type is "t2.micro".

The tags parameter specifies metadata to attach to the instance, in this case, a tag named "Name" with the value "TerraformTestInstance".

![cZOEPf7ikB-bjUujjhyQiwGiB_hRzW_rFDRavXFWPhRBLynjT4mdyKHN6TMEo6UvRhz3WegZHi7mE-7DnyanmQZffiMr6FNqzBnYLhU](../../media/cZOEPf7ikB-bjUujjhyQiwGiB_hRzW_rFDRavXFWPhRBLynjT4mdyKHN6TMEo6UvRhz3WegZHi7mE-7DnyanmQZffiMr6FNqzBnYLhU.png)

first initialize the working directory with the necessary plugins and modules by executing **terraform init**

![aUBSA2Uw_6e82vdE_27-Xnw8H1tWGOaXAX-DobfLq6X4v3u5hFA0gHlNcIRUl5oN51rhSwwO52xZJW0oQ0-rcLAjS1TPwChn45XmH5A](../../media/aUBSA2Uw_6e82vdE_27-Xnw8H1tWGOaXAX-DobfLq6X4v3u5hFA0gHlNcIRUl5oN51rhSwwO52xZJW0oQ0-rcLAjS1TPwChn45XmH5A.png)

It will create an execution plan by analyzing the changes required to achieve the desired state of your infrastructure with **terraform plan**

![EuefqBcT9LiWvWdSy0N53kqhOdzgm28kc1sKa5V-KxqVFJSJGDhHMx6Pgj-kham_5XCUghkrE4rteSnADtpTmUK_LY7hsOGYF9fcq7oj](../../media/EuefqBcT9LiWvWdSy0N53kqhOdzgm28kc1sKa5V-KxqVFJSJGDhHMx6Pgj-kham_5XCUghkrE4rteSnADtpTmUK_LY7hsOGYF9fcq7oj.png)

![a__2be5uDYVp7jYEVQeLMJiPHGM-iG5edeyHZ0Ubi2uPr4Gv2atq7rD-YXJJ8NKkywdx8es1Fs622M84RPHxUAXkx3OYugH6U1bs-GbH](../../media/a__2be5uDYVp7jYEVQeLMJiPHGM-iG5edeyHZ0Ubi2uPr4Gv2atq7rD-YXJJ8NKkywdx8es1Fs622M84RPHxUAXkx3OYugH6U1bs-GbH.png)

Finally, it will apply the changes to create or update resources as needed with **terraform apply**.

![B4tXqNfGGBbHL_iMLcjMZeh9rIq8bKeyx0MJvXhZD6mk6Nn8lStbF8mjh85JCeoYotRpqsiMy32Vc_MTUvgj3X_An7Fo2T4VwRCkjLY](../../media/B4tXqNfGGBbHL_iMLcjMZeh9rIq8bKeyx0MJvXhZD6mk6Nn8lStbF8mjh85JCeoYotRpqsiMy32Vc_MTUvgj3X_An7Fo2T4VwRCkjLY.png)

![4A8aiHYvnln75z2Chj8SlkE2z4k6-WF2ZpwMb_J2pELMUNrv3pVj7A24Qu5YTC-ULZZozI9Mf_FHYEUFb8IeEzAsLUlxr7_8FM-nVTla](../../media/4A8aiHYvnln75z2Chj8SlkE2z4k6-WF2ZpwMb_J2pELMUNrv3pVj7A24Qu5YTC-ULZZozI9Mf_FHYEUFb8IeEzAsLUlxr7_8FM-nVTla.png)

You can check two instances created using terraform.

![iRaJ65q_0meH44FiZiqjYTJ7QBz5weQqWR4TnVbdfvufFp1Z9OAPzI6Tq4eESi1RTsZaXDJ0oAMI7w7hocVNrPoOzk1CmAeff5-MEmr-](../../media/iRaJ65q_0meH44FiZiqjYTJ7QBz5weQqWR4TnVbdfvufFp1Z9OAPzI6Tq4eESi1RTsZaXDJ0oAMI7w7hocVNrPoOzk1CmAeff5-MEmr-.png)
