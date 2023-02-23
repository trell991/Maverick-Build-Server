# Server side setup

## In order to remotely manage windows hyper v server 2019 you need to complete a few quick steps lets get started
>
> note in order to remotely manage hyper-v server 2019 you must be using windows 10 pro or enterprise edition. I will be using the enterprise edition.
>
### Lets get started

- First ensure the network profile on hyper v server 2019 is set to private
  > run

   ```
    Get-NetAdapter| Get-NetConnectionProfile
    ```

  > If the Network Category is private run

   ```
    Set-NetConnectionProfile -InterfaceAlias "vEthernet (LAN)" -NetworkCategory Private
    ```

  > Next run

  ```
  Enable-PSRemoting
  ```

  > Then

  ```
  Enable-WSManCredSSP -Role server
  ```

### This is all for the server side setup
