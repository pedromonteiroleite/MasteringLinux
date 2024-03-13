## Run Container

- Publish WebAPI (to folder)
- Upload publish folder to VM
- Create DockerFile

      FROM mcr.microsoft.com/dotnet/aspnet:6.0
      WORKDIR /app
      COPY . .
      EXPOSE 80
      ENTRYPOINT ["dotnet", "WebAPI.dll"]

- Add the inbound port 80 rule to VM if not yet added.
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

- Run container

- Test WebAPI

### Remarks:

- If needed to clear the containers or/and the images from the VM:

      $ sudo docker stop <containerId>  # Stop the container
      $ sudo docker rm <containerId>    # Remove the container
      $ sudo docker rmi webapi:latest  # Remove the image

- Noticed the relation between the ASPNETCORE_ENVIRONMENT variable specified at the docker run command regarding tha configuration of the launchsetting.json profile of the WebAPI project and the openned inbound port rule on the VM.
