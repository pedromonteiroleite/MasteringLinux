## Connect to vm (PowerShell)

- ssh
  - Check if SSH is installed
- ssh < username > @ < vmPublicIp >
  - Connect via the vm´s public ip informing the username. The password will be requested to stablish the connection.
  - The ps become a bash script window.
  - obs: Common "root" user is not allowed to connect using password.
- ip a
  - kind like ipconfig
- hostnamectl
  - Shows OS info, version etc
- exit
  - Close connection to vm.
  - Bash turns off.
