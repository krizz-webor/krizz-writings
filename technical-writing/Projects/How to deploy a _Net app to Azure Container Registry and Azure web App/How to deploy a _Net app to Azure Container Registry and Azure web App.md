## How to deploy a .Net app to Azure Container Registry and Azure web App Using Github Actions

**Create an Azure Container Registry**:

Log in to the Azure portal and navigate to the `Container registries` page.

Click the `Add` button to create a new container registry.

Fill in the required information, such as the `resource group, name, location, SKU, and admin user.`

Click the `Create` button to create the container registry.

**Create an Azure Web App**:

Log in to the Azure portal and navigate to the `Web Apps` page.

Click the `Add` button to create a new web app.

Fill in the required information, such as the `resource group, name, operating system, runtime stack, and region`.

Click the `Review + create` button to create the web app.

**Generate a Dockerfile for your .NET 7.0 app**:

Create a new file in the root directory of your .NET app and name it `Dockerfile`.

Paste the following content into the Dockerfile:

    FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
    WORKDIR /app
    EXPOSE 80
    EXPOSE 443
    
    FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
    WORKDIR /src
    COPY ["Api.BillService.Afripie/Api.BillService.Afripie.csproj", "Api.BillService.Afripie/"]
    RUN dotnet restore "Api.BillService.Afripie/Api.BillService.Afripie.csproj"
    COPY . .
    WORKDIR "/src/Api.BillService.Afripie"
    RUN dotnet build "Api.BillService.Afripie.csproj" -c Release -o /app/build
    
    FROM build AS publish
    RUN dotnet publish "Api.BillService.Afripie.csproj" -c Release -o /app/publish /p:UseAppHost=false
    
    FROM base AS final
    WORKDIR /app
    COPY --from=publish /app/publish .
    ENTRYPOINT ["dotnet", "Api.BillService.Afripie.dll"]

Replace "myapp.dll" with the name of your .NET app's entry point DLL.

**You can also add a docker-compose file**:

    version: '3.4'
    
    services:
      api.billservice.afripie:
        image: ${DOCKER_REGISTRY-}apibillservice
        build:
          context: .
          dockerfile: Api.BillService.Afripie/Dockerfile
        environment:
          - ASPNETCORE_ENVIRONMENT=Development
          - ASPNETCORE_URLS=http://+:80
        ports:
          - "5230:80"
        volumes:
          - ~/.aspnet/https:/root/.aspnet/https:ro
          - ~/.microsoft/usersecrets:/root/.microsoft/usersecrets:ro

**Configure the GitHub Actions workflow**:

Create a new file in the root directory of your GitHub repository and name it "deploy.yml".

Paste the following content into the file:

    name: Deploy to ACR
    on:
      push:
        branches:
          - staging
    
    jobs:
      build-and-deploy:
        runs-on: ubuntu-latest
    
        steps:
        - uses: actions/checkout@v2

        - name: Login to Azure
          uses: azure/login@v1
          with:
            creds: ${{ secrets.AZURE_CREDENTIALS }}
    
        - name: Configure .NET 7.0
          uses: actions/setup-dotnet@v1
          with:
            dotnet-version: '7.0.x'
    
        - name: Build and tag Docker image
          uses: docker/build-push-action@v2
          with:
            context: .
            push: false
            tags: afripiestag.azurecr.io/latest:${{ github.sha }}
    
        - name: Login to ACR
          uses: azure/docker-login@v1
          with:
            login-server: afripiestag.azurecr.io
            username: ${{ secrets.AZURE_CONTAINER_REGISTRY_USERNAME }}
            password: ${{ secrets.AZURE_CONTAINER_REGISTRY_PASSWORD }}
    
        - name: Push Docker image to ACR
          run: docker push afripiestag.azurecr.io/latest:${{ github.sha }}
    
        - name: Deploy to Azure Web App
          uses: azure/webapps-deploy@v2
          with:
            app-name: afripiestag
            images: afripiestag.azurecr.io/latest:${{ github.sha }}


