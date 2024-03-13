## Connect to vm (PowerShell)

- Check if SSH is installed

       ssh

- Connect via the vm´s public ip informing the username. The password will be requested to stablish the connection.
- The ps become a bash script window.
- obs: Common "root" user is not allowed to connect using password.

       ssh < username > @ < vmPublicIp >

- kind like ipconfig

       ip a

- Shows OS info, version etc

       hostnamectl

- Close connection to vm.

       exit

- Bash turns off.

## Connect to vm (Putty)

- Open Putty, inform the VM public IP and select SSH.
