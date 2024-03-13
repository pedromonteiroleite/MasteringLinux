## Install Docker

- SSH Connect
- Follow docker instalation to CentOS using docker repository - https://docs.docker.com/engine/install/centos/
- Check instalation

       $ sudo docker version

- Run image from docker hub

       $ sudo docker run hello-world

- List images
  $ sudo docker images

- Access VM on Azure portal, in the network tab add a inbound rule for http on port 80.

## Install Nginx

       $ sudo docker run --name appnginx -p 80:80 -d nginx

- Open a web browser and paste in the url the public ip of the VM. It should show the welcome page of nginx.
