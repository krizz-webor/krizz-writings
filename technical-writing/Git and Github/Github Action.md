    name: Deploy and Run Docker Image on Azure
    on:
      push:
        branches:
          - main
    jobs:
      deploy:
        runs-on: ubuntu-latest
        steps:
        - name: Checkout code
          uses: actions/checkout@v2
        - name: Login to Azure
          uses: azure/login@v1
          with:
            creds: ${{ secrets.AZURE_CREDENTIALS }}
        - name: Build and push Docker image
          uses: azure/docker-login@v1
          with:
            login-server: ${{ secrets. }}
            username: ${{ secrets.REGISTRY_USERNAME }}
            password: ${{ secrets.REGISTRY_PASSWORD }}
        - name: Deploy Docker image to Azure Virtual Machine
          uses: azure/docker-deploy@v1
          with:
            container-image-name: ${{ secrets.REGISTRY_URL }}/my-image:latest
            vm-user-name: ${{ secrets.VM_USERNAME }}
            ssh-private-key: ${{ secrets.VM_SSH_PRIVATE_KEY }}
            vm-password: ${{ secrets.VM_PASSWORD }}
            vm-public-ip: ${{ secrets.VM_PUBLIC_IP }}
        - name: Run Docker container on Azure Virtual Machine
          run: |
            ssh -i ${{ secrets.VM_SSH_PRIVATE_KEY }} ${{ secrets.VM_USERNAME }}@${{ secrets.VM_PUBLIC_IP }} 'docker run -d -p 80:80 --name my-container ${{ secrets.REGISTRY_URL }}/my-image:latest'
        - name: Deploy Docker image to Azure Container Registry
          uses: azure/docker-login@v1
          with:
            login-server: ${{ secrets.REGISTRY_URL }}
            username: ${{ secrets.REGISTRY_USERNAME }}
            password: ${{ secrets.REGISTRY_PASSWORD }}
        - name: Push Docker image to Azure Container Registry
          run: docker push ${{ secrets.REGISTRY_URL }}/my-image:latest