# Client side setup

## Below will list out all the steps needed to remotly manage windows hyper-v server 2019
  >
  > I will be managing my build server from a windows 10 enterprise edition VM running of an ESXI hypervisor.
  >
### Lets get started

- First navigate to progreams and features on the client machine. Locate the hyper v folder and expand and enable all of the check boxes. Apply the changes and windows will reboot and install the changes.
  - Next you will need to edit the hosts file and add your servers ipaddress and server name.
  - Next run some commands

  ```
  Start-Service -Name winrm
  Set-Item WSMan:\localhost\Client\TrustedHosts -Value "your-server-name.local"
  ```

- Next run this command to check if powershell remoting is working.

  ```
  Invoke-Command {WHOAMI} -Computername server-name.Local -Credential Server-name\Administrator
  ```
