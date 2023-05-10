## What is CodeDeploy ?
AWS CodeDeploy is a deployment service that automates application deployments to Amazon EC2 instances, on-premises instances, serverless Lambda functions, or Amazon ECS services.
CodeDeploy can deploy application content that runs on a server and is stored in Amazon S3 buckets, GitHub repositories, or Bitbucket repositories. CodeDeploy can also deploy a serverless Lambda function. You do not need to make changes to your existing code before you can use CodeDeploy.

The application specification file (AppSpec file) is a YAML formatted or JSON-formatted file used by CodeDeploy to manage a deployment. The AppSpec file for an EC2/On-Premises deployment must be named appspec. yml or appspec.yaml , unless you are performing a local deployment.

The appspec.yaml file is a configuration file that defines how the deployment should proceed. It specifies the deployment process, including which files should be deployed, where they should be deployed, and any scripts or hooks that should be executed during the deployment.

The appspec.yaml file typically includes the following sections:

1. version: This section specifies the version of the AppSpec file format being used.
2. os: This section specifies the operating system of the target instances.
3. files: This section specifies the source and destination locations of the files to be deployed.
4. hooks: This section specifies any scripts or hooks that should be executed during the deployment, such as scripts to stop and start the application.