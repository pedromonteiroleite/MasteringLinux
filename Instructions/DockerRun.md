## Run Container

- Publish WebAPI (to folder)
- Upload publish folder to VM
- DockerFile:

      FROM mcr.microsoft.com/dotnet/aspnet:6.0
      WORKDIR /app
      COPY . .
      EXPOSE 80
      ENTRYPOINT ["dotnet", "WebAPI.dll"]

- Add the inbound port 80 rule to VM if not yet added.

### The inbound port rule task was automated via azure-pipelines.yml

        - task: AzureCLI@2
          displayName: "Open Inbound Rule on Port 80"
          inputs:
            azureSubscription: "ServicePrincipalHotmail"
            scriptType: "bash"
            scriptLocation: "inlineScript"
            inlineScript: |
              az network nsg rule create \
                --resource-group $(resourceGroupName) \
                --nsg-name $(networkSecurityGroupName) \
                --name AllowPort80 \
                --access Allow \
                --protocol Tcp \
                --direction Inbound \
                --priority 100 \
                --source-address-prefix "*" \
                --source-port-range "*" \
                --destination-address-prefix "*" \
                --destination-port-range 80

- Upload Dockerfile to publish folder (WinSCP)
- Go to server and execute the commands (Putty)

         $ sudo docker ps
         $ cd publish
         $ sudo docker build -t webapi .
         $ sudo docker run -d \
           -e ASPNETCORE_ENVIRONMENT=Production \
           -p 80:80 \
           --name webapi \
           webapi:latest

- Test WebAPI

      http://[IP]]:[PORT]]/[ENDPOINT]]

### Remarks:

- If needed to clear the containers or/and the images from the VM:

      $ sudo docker stop <containerId>  # Stop the container
      $ sudo docker rm <containerId>    # Remove the container
      $ sudo docker rmi webapi:latest  # Remove the image

- Noticed the relation between the ASPNETCORE_ENVIRONMENT variable specified at the docker run command regarding tha configuration of the launchsetting.json profile of the WebAPI project and the openned inbound port rule on the VM.
