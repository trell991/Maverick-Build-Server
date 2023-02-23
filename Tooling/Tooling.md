# Tooling

- Packer
- Vscode
- terraform
- Powershell core
- Windows Terminal
- Git
- Oh-My-Posh
- Docker Desktop
- Chocolatey
  - To install Chocolatey first run  

  ```
  Get-ExecutionPolicy
  ```

  - If it returns `restricted` run

  ```
  Set-ExecutionPolicy AllSigned
  ```

  - Or run

  ```
  Set-ExecutionPolicy Bypass -Scope Process
  ```

  - Next run this to install chocolatey:

  ```
  Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
  ```

  - Here is a  Chocolatey script to install all of the tooling. You can paste this into powershell ISE:
  
  ```
  choco install packer -y
  choco install terraform -y
  choco install vscode --version -y
  choco install powershell-core --version -y
  choco install microsoft-windows-terminal -y
  choco install git -y
  choco install oh-my-posh -y
  choco install docker-desktop -y
  ```
