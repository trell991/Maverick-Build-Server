# Client side setup

## Below will list out all the steps needed to remotely manage windows hyper-v server 2019
  >
  > I will be managing my build server from a windows 10 enterprise edition VM running of an ESXI hypervisor.
  >
### Lets get started

- First on the client machine navigate to Control Panel>Programs>Programs and Features> then select Turn Windows Features on or off in the left pane of the screen. Locate the Hyper-V folder, expand it and enable all of the check boxes. Apply the changes and windows will reboot to install the changes.
  - Next you will need to edit the hosts file. In the hosts file you will add your servers ip address and server name.
  - First launch notepad 
    - In File explorer navigate to ```C:\Windows\System32\drivers\etc ```
    - Open the Hosts file in notepad or any editor and add the servers IP address, server name, fully qualified domain name and IP address **at the very bottom of the hosts file**
    - Heres an example
    - > Note that there are two spaces between the IP address and server-name
    - ```
      11.1.1.111  SERVER_NAME
      11.1.1.111  SERVER-NAME.local
      ```
  - Next run these powershell commands as Administrator

  ```
  Start-Service -Name winrm
  Set-Item WSMan:\localhost\Client\TrustedHosts -Value "your-server-name.local"
  ```
  > Be sure to put your server name in quotes "your-server-name.local"
- Next run this command to check if powershell remoting is working. 

  ```
  Invoke-Command {WHOAMI} -Computername server-name.Local -Credential Server-name\Administrator
  ```
- After this command a prompt will appear. Enter your server credentials and the whoami command will return the server name and user profile.
- Next navigate to local group policy editor or just run ``` gpedit.msc```
- Within local group policy editor expand Computer Configuration and navigate to Administrative templates>System>Credentials Delegation. Here you need to enable "Allow delegating fresh credentials"and add your server to the list. Add the folowing : 
  ```
    wsman/SERVER-NAME.local
    wsman/SERVER-NAME
   ```
- Next enable "Allow delegating fresh credentials with NTLM-only server authentication". Add your servers to the list just as we did above. 
- Lastly run ```gpupdate /force ``` in powershell or cmd to force the group policy change. 
- Lastly open Hyper-V Manager and select connect to server. Select Another computer adn enter SERVER-NAME.local. Check the box that says connect as another user and enter your server credentials as such:
-  For user name use```SERVER-NAME\administrator``` and enter your servers password.

### Now you can remotely manage your server 