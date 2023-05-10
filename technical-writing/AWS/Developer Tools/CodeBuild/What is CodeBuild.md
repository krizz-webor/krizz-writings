## AWS CodeBuild
AWS CodeBuild is a fully managed build service that provides the similar capability that Jenkins can offer you. If you have maintained a Jenkin server on your own, you know how much effort it takes to maintain a highly available solid build service.

With the AWS CodeBuild, you don’t have to worry about the availability of the build server. It is more secure, follows pay as you go model, and allows us to integrate with various AWS services.

AWS CodeBuild is a fully managed build service in the cloud. CodeBuild compiles your source code, runs unit tests, and produces artifacts that are ready to deploy. CodeBuild eliminates the need to provision, manage, and scale your own build servers.

A **Buildspec** file is a YAML file that defines the build process for your CodeBuild project. It contains a series of commands that CodeBuild will execute to build and package your application.