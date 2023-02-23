# Tooling

- Packer
- Vscode
- terraform
- Powershell core
- Windows Terminal
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
  choco install packer --version 1.8.5 -y
  choco install terraform --version 1.3.9 -y
  choco install vscode --version 1.75.1 -y
  choco install powershell-core --version 7.3.2 -y
  choco install microsoft-windows-terminal -y
  choco install git --version 2.39.2 -y
  choco install oh-my-posh --version 14.8.0 -y
  choco install docker-desktop --version 4.16.3 -y
  ```