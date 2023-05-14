## How to deploy a .NET app in GitHub to an azure web app service using Azure DevOps

**Create an Azure Web App Service**:

In the Azure portal, navigate to the `App Services` tab and click on `Add`.

Fill in the required information for your web app, including `subscription, resource group, and name`.

Choose your preferred operating system and runtime stack (in this case, .NET).

Select `Configure container` and choose `Single Container`.

Configure the rest of the settings as needed and click `Review + Create` to create your web app.

**Create a Service Principal for the Web App**:

In the Azure portal, navigate to the `Azure Active Directory` tab and click on `App registrations`.

Click on `New registration` and fill in the required information.

Under `Redirect URI`, select `Web` and enter the URL of your web app.

Click on `Register` to create the app registration.

From the app registration's overview page, copy the `Application (client) ID` and `Directory (tenant) ID` for use in the next step.

**Create a Service Connection in Azure DevOps**:

To connect to the Azure subscription from Azure DevOps, we need to create a Service Connection in Azure DevOps.

**Here are the steps to create a Service Connection in Azure DevOps**:

Go to the project in Azure DevOps and select `Project settings` from the bottom left corner of the page.

Select `Service connections` under the `Pipelines` section.

Click on `New service connection` and select `Azure Resource Manager`.

Select the appropriate subscription and resource group for the web app.

Provide a connection name and click on `OK` to create the Service Connection.

**Add a Pipeline in Azure DevOps**:

Now, we need to create a pipeline in Azure DevOps to deploy the .NET app to the Azure Web App Service.

**Here are the steps to create a pipeline in Azure DevOps**:

Go to the project in Azure DevOps and select `Pipelines` from the left menu.

Click on `New pipeline` and select `GitHub` as the source.

Select the repository and branch that contains the .NET app code.

Choose the .NET template and configure the pipeline settings as per the app requirements.

In the `Deployment` section of the pipeline, select the Service Connection created.

In the `App Service name` field, provide the name of the Azure Web App Service where the .NET app needs to be deployed.

Here is a sample pipeline script for deploying a .NET app to an Azure Web App Service:

    trigger:
    - main
    pool:
      vmImage: 'ubuntu-latest'
    steps:
    - task: UseDotNet@2
      inputs:
        version: '7.x'
        packageType: 'sdk'
    - task: DotNetCoreCLI@2
      inputs:
        command: 'restore'
        projects: '**/*.csproj'
        feedsToUse: 'config'
        nugetConfigPath: '$(System.DefaultWorkingDirectory)/nuget.config'
    - task: DotNetCoreCLI@2
      inputs:
        command: 'build'
        projects: '**/*.csproj'
        arguments: '--configuration Release'
    - task: DotNetCoreCLI@2
      inputs:
        command: 'publish'
        projects: '**/*.csproj'
        arguments: '--configuration Release --output $(Build.ArtifactStagingDirectory)'
    - task: AzureRmWebAppDeployment@4
      inputs:
        ConnectionType: 'AzureRM'
        azureSubscription: '<name of service connection>'
        appType: 'webAppLinux'
        WebAppName: '<name of web app>'
        packageForLinux: '$(Build.ArtifactStagingDirectory)/**/*.zip'

**Run the Pipeline**

Once the pipeline is created, we can trigger the pipeline to run and deploy the .NET app to the Azure Web App Service.

**Here are the steps to run the pipeline in Azure DevOps**:

Go to the pipeline created.

Click on `Run pipeline` and select the appropriate branch to deploy the app.

Click on `Run` to trigger the pipeline.

**Verify the Deployment**

Once the pipeline run is successful, we can verify the deployment of the .NET app to the Azure Web App Service.

**Here are the steps to verify the deployment**:

Go to the Azure portal and navigate to the Azure Web App Service where the app is deployed.