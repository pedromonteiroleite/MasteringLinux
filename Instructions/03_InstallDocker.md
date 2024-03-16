## The docker instalation task was automated via azure-pipelines.yml

         - task: AzureCLI@2
           displayName: "Install Docker on CentOS VM"
           inputs:
             azureSubscription: "ServicePrincipalHotmail"
             scriptType: "bash"
             scriptLocation: "inlineScript"
             inlineScript: |
               az vm extension set \
                 --publisher Microsoft.Azure.Extensions \
                 --version 2.0 \
                 --name CustomScript \
                 --vm-name $(virtualMachineName) \
                 --resource-group $(resourceGroupName) \
                 --settings '{
                   "commandToExecute": "sudo yum install -y yum-utils && \
                                        sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo && \
                                        sudo yum install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin && \
                                        sudo systemctl start docker"
                 }'

## Reference

- SSH Connect
- [Follow Docker instalation to CentOS using docker repository](https://docs.docker.com/engine/install/centos/)

- Verify instalation

       $ sudo docker version

- Run image from docker hub

       $ sudo docker run hello-world

- List images
  $ sudo docker images

- Access VM on Azure portal, in the network tab add a inbound rule for http on port 80.

## Install Nginx (test)

       $ sudo docker run --name appnginx -p 80:80 -d nginx

- Open a web browser and paste in the url the public ip of the VM. It should show the welcome page of nginx.
